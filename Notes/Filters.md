API Platform enables you to set filters that the end-user can specify in order to get a customized set of data. For example, in a class that has the `isPublished` property, you can set up a filter for it using the `ApiFilter` attribute above the class:

```php
#[ApiFilter(BooleanFilter::class, properties: ['isPublished'])]
```

Then a **GET** request can be sent like this:

```
https://localhost/treasures?page=1&isPublished=true
```

Filters can also be applied to properties that are not boolean, such as strings and integers. For example, in order to filter based on a range (greater than, lesser than), you can use a `RangeFilter` like this:

```php
#[Groups(['treasure:read', 'treasure:write'])]  
#[ORM\Column]  
#[ApiFilter(RangeFilter::class)]  
private ?int $value = null;
```

Then you'll be able to send requests like this one:

```bash
https://localhost/treasures?page=1&description=est&value%5Bgte%5D=40000
```

It is also possible to set a `PropertyFilter`, even though it isn't really the recommended approach of solving the problem it is supposed to solve (more on that on [Vulcain](https://github.com/dunglas/vulcain)).

