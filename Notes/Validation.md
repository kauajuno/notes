In Symfony, validation can be done through validation attributes. A key note is to import the validation component like this to improve readability:

```php
use Symfony\Component\Validator\Constraints as Assert;
```

Then there are a lot of different possible validations you can set up on your API. A lot of them go like this:

```php
#[Assert/NotBlank]
#[Assert\Length(min: 2, max: 50, maxMessage: 'Describe your loot in 50 chars or less')]

#[Assert\GreaterThanOrEqual(0)]
#[Assert\LesserThanOrEqual(10)]
```

More on validation [here](https://symfony.com/doc/current/validation.html).