

# API Platform introduction

API Platform is a framework built on top of Symfony.

Traditionally, building an API in Symfony (or any framework) involves a lot of boilerplate:

1. Define an entity.
2. Create a form type for validation (maybe).
3. Write a controller for each operation (GET, POST, PUT, DELETE).
4. Manually handle serialization/deserialization in each controller.
5. Configure routes for each endpoint.

**API Platform flips this model.** You start by designing your data model (using Doctrine entities or any PHP class), and by adding a few annotations, you **automatically get a fully functional, hypermedia-rich, standardized API.**

# Topics

- [[API Platform Windows Setup]]
- [[API Platform Entity]]
- [[Sending requests]]
- [[API Platform Profiler]]
- [[API Platform Response manipulation]]
- [[API Platform Pagination]]
- [[API Platform Data Fixtures]]
- [[API Platform Filters]]
- [[API Platform Formats]]
- [[API Platform Validation]]

# Class notes

Make a user with `docker compose exec php php bin/console make:user` (User, yes to all, email). Also edit the entity to add a username string field. After confirming go to the ORM/Column attribute on the property and add unique:true. Make and run the migration. Create data fixtures for the user class. Paste this to your factory.

```php
namespace App\Factory;

use App\Entity\User;
use App\Repository\UserRepository;
use Symfony\Component\PasswordHasher\Hasher\UserPasswordHasherInterface;
use Zenstruck\Foundry\ModelFactory;
use Zenstruck\Foundry\Proxy;
use Zenstruck\Foundry\RepositoryProxy;

/**
 * @extends ModelFactory<User>
 */
final class UserFactory extends ModelFactory
{
    const USERNAMES = [
        'FlamingInferno',
        'ScaleSorcerer',
        'TheDragonWithBadBreath',
        'BurnedOut',
        'ForgotMyOwnName',
        'ClumsyClaws',
        'HoarderOfUselessTrinkets',
    ];
    public function __construct(
        private UserPasswordHasherInterface $passwordHasher
    )
    {
        parent::__construct();
    }
    protected function getDefaults(): array
    {
        return [
            'email' => self::faker()->email(),
            'password' => 'password',
            'username' => self::faker()->randomElement(self::USERNAMES) . self::faker()->randomNumber(3),
        ];
    }
    protected function initialize(): self
    {
        return $this
            ->afterInstantiate(function(User $user): void {
                $user->setPassword($this->passwordHasher->hashPassword(
                    $user,
                    $user->getPassword()
                ));
            })
        ;
    }

    protected static function getClass(): string
    {
        return User::class;
    }
}
```

Expose the User as an `ApiResource` and set normalization and denormalization context groups. you dont need id, email should be readable and writable, password writable-only (even though you're not dealing with hashing for now) and username should be readable and writable. Put the `UniqueEntity` attributes above the class for the fields email and username. Assert/NotBlank on username and email and Assert/Email on email.

**relating resources**

Use `make:entity` to edit `DragonTreasure` and create a new field called owner of the type ManyToOne. The class should relate to User, DragonTreasure.owner should not be nullable and user should be able to access/update DragonTreasure instances from itself. Do not perform orphan removal, we'll talk about this.

Talk about this!

Run `symfony console doctrine:database:drop -- force` then `symfony console doctrine:database:create` to put your database back up again. Then fix your factory to include a `owner => UserFactory::new()` and your fixtures with a callback to the `UserFactory::random()` method as follows:

```php
class AppFixtures extends Fixture
{
    public function load(ObjectManager $manager): void
    {
        UserFactory::createMany(10);
        DragonTreasureFactory::createMany(40, function () {
            return [
                'owner' => UserFactory::random(),
            ];
        });
    }
}
```

Now you're going to be able to load your fixtures. Remember to expose your owner property as part of the normalization and denormalization group. Owner will be returned as an IRI. It means international resource identifier. It also expects either a JSON or an IRI when you send data to the API. Expose the `dragonTreasure` property on the Owner entity as well and it will appear.

If instead of IRI you want embedded relations, for example, you want actual `DragonTreasure` data to come with your User request, you can go to the `DragonTreasure` entity and apply the `normalizationContext` group of your User class, such as `user:read`. The same can be done the other way around.

Now you have a new challenge. It is cool to get the owner data embedded when you fetch a single treasure, but when fetching the entire collection it might seem like you're wasting bandwidth. Is it possible to get embedded data when fetching a single treasure and just the IRI when fetching a whole collection? Yes it is.

Inside your `DragonTreasure.php` file, edit the `ApiResource` attribute to include this:

```php
#[ApiResource(
    operations: [
        new Get(
            normalizationContext: [
                'groups' => ['treasure:read', 'treasure:item:get'],
            ],
        ),
    ],
)]
class DragonTreasure
{
}
```

When you set a `normalizationContext` inside of a HTTP verb method, you're overriding the outer scope which in this case is the entity-wide `normalizationContext` configuration. This one means that everything marked as either part of the group `treasure:read` or `treasure:item:get` will be returned for this verb. Now go to the `User.php` file and set this group above the username property like this:

```php
#[Groups(['user:read', 'user:write', 'treasure:item:get'])]
private ?string $username = null;
```

But is it possible to change data from an entity through another entity's endpoint? Yes it is! It gets rather complex depending on the nuances, but let's follow a clear step by step.

You're allowed to change the owner for a `DragonTreasure` entity, just send the **PATCH** setting the owner's IRI to a different one. But what if I want to update something in the owner instead of updating the owner itself? Let's try something like this:

```json
{
	"owner": {
		"username": "Etermentales20Testing"
	}
}
```

And... it does not work. Of course, at this point you need to add the denormalization group to the owner property that you want to be able to update. Set `treasure:write` to the groups of the owner username property and try again.

And now you got yourself a brand new error! When you don't provide an @id in this type of request, API Platform tries to create a new owner instead of updating the existing one. By providing the @id string in the JSON, you should end up with a JSON like this one:

```json
{
	"owner": {
		"@id": "/api/users/3"
		"username": "Etermentales20Testing"
	}
}
```

And then you finally got yourself a functional update. Kind of. If you experiment some more, you'll notice that validation rules that were set up for the User class are not being applied here. This happens because when sending a request to the DragonTreasure endpoint it validates all of its properties, but the owner property has no validation attribute. How do you setup a validation for a property that has its own validation rules in another entity file? You simply type this above your property:

```php
#[Assert/Valid]
```

Even though this might seem really fancy it can lead to some confusion as the application grows larger, so be careful with complex operations as this one.

But now we've only worked changing the "One" side of the "OneToMany" relationship. As you could've guessed things might be a little bit different from the "Many" side. How do you update it? Can you add items to it?

First things first, you probably cannot see a dragonTreasures property when trying to update a user because you didn't set it to be part of the user:write group. Do that and you'll be good to do so by providing the necessary IRIs. Send a **PATCH** request to update some owner's list of DragonTreasure like this:

```json
{
	"email": "skaua@ggmail.com",
	"password": "password123",
	"username": "skaua",
	"dragonTreasures": [
		"treasures/1",
		"treasures/2",
		"treasures/3"
	]
}
```

Now it works, but there might be a strange feeling... how did API Platform update this row if there is no getter or setter for dragonTreasures inside my User entity? Well, there is addDragonTreasure and removeDragonTreasure, 