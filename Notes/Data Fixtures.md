Data fixtures are a pre-defined set of data that is used to populate a database in order to run tests. In API Platform, you can run the following command in order to install the Doctrine Fixtures Bundle:

```bash
docker compose exec php composer require foundry orm-fixtures --dev
```

Foundry will help you generate randomized and realistic data to populate your database and orm-fixtures will help you load the dataset onto your database.

Run the following command to create a factory for your class:

```bash
docker compose exec php php bin/console make:factory
```

This will prompt you to choose which entity you want to create a factory for. A factory will be responsible for creating the objects that will then be loaded into your database. The defaults method will create a list of attributes correspondent to those of your entity.

```php
#[\Override]
    protected function defaults(): array
    {
        return [
            'coolFactor' => self::faker()->numberBetween(1, 10),
            'description' => self::faker()->paragraph(1),
            'isPublished' => self::faker()->boolean(),
            'name' => self::faker()->randomElement(self::TREASURE_NAMES),
            'plunderedAt' => \DateTimeImmutable::createFromMutable(self::faker()->dateTimeBetween('-1 year')),
            'value' => self::faker()->numberBetween(1000, 1000000),
        ];
    }
```

Now hop on your AppFixtures.php and create your objects:

```php
<?php  
  
namespace App\DataFixtures;  
  
use App\Factory\DragonTreasureFactory;  
use Doctrine\Bundle\FixturesBundle\Fixture;  
use Doctrine\Persistence\ObjectManager;  
  
class AppFixtures extends Fixture  
{  
    public function load(ObjectManager $manager): void  
    {  
        DragonTreasureFactory::createMany(40);  
    }  
}
```

Then run the following command to load them into your database:

```bash
docker compose exec php php bin/console doctrine:fixtures:load
```