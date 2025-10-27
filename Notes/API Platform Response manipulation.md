# Allowing request types

Even though by default API Platform provides the 5 main HTTP verbs to the entity, you might not want all of them to be exposed. For example, you might not want your end-user to be able to directly dele resources. In order to control that, you can specify which types of request can be sent to your API through the `ApiResource` attribute. _Let's also add a description on it to improve readability._

```php
#[ApiResource(
	description: 'Dragon Treasure entity, represents... a Dragon Treasure, what did you expect',
		operations: [
		new Get(),
		new Put(),
		new Patch(),
		new Post(),
		new GetCollection(),
	]
)]
```

# Readable and writable properties  

To define if a property is readable and/or writable, first API Platform will look to see whether if the property itself is public or private. If it is private, it will then seek for getters and setters inside of your code. This can define in which requests a property may appear or not. For example, you wouldn't want to be able to set a `createdAt` property (except in its creation, of course). If you delete your `setCreatedAt` method and include a construct method that sets your data on creation, you'll achieve exactly that.

```php
public function __construct()
{
	$this->plunderedAt = new \DateTimeImmutable();
}
```

You can also define getters and setters that do not correspond to a specific property in your entity and they will be exposed on your API. Those can be called virtual properties. For example, let's try to make the DateTime property more readable for humans. First install this bundle:

```bash
docker exec php composer require nesbot/carbon  
```

Then create a getter with some other name, like `getPlunderedAtAgo` and use Carbon to return a human-friendly and readable string instead of the pure DateTime value:

```php
public function getPlunderedAtAgo(): string
{
	return Carbon::instance($this->plunderedAt)->diffForHumans();
}
```

Now your responses should look like this:


```json
	{
	"@context": "/contexts/DragonTreasure",
	"@id": "/dragon_treasures",
	"@type": "Collection",
	"totalItems": 4,
	"member": [
		{
			"@id": "/dragon_treasures/1",
			"@type": "DragonTreasure",
			"id": 1,
			"name": "Electric Argentinian Dragon",
			"description": "Not so cool and not so valuable, he is from argentina after all",
			"plunderedAt": "2025-10-16T15:46:57+00:00",
			"coolFactor": "12",
			"value": "300",
			"plunderedAtAgo": "1 day ago",
			"published": true
		},
		{
			"@id": "/dragon_treasures/2",
			"@type": "DragonTreasure",
			"id": 2,
			"name": "Cryo Brazilian Dragon",
			"description": "Scream if you love brazilian cold afternoons! This one is so cool especially because it mixes things that should not be mixed at all, such as Brazil and cold",
			"plunderedAt": "2025-10-16T15:46:57+00:00",
			"coolFactor": "94",
			"value": "128400",
			"plunderedAtAgo": "1 day ago",
			"published": true
		},
		{
			"@id": "/dragon_treasures/3",
			"@type": "DragonTreasure",
			"id": 3,
			"name": "Estonian Mountain Dragon",
			"description": "This one eats a lot, it is going to be a pain in your pocket.",
			"plunderedAt": "2025-10-17T16:22:59+00:00",
			"coolFactor": "6",
			"value": "70000",
			"plunderedAtAgo": "31 minutes ago",
			"published": true
		},
		{
			"@id": "/dragon_treasures/4",
			"@type": "DragonTreasure",
			"id": 4,
			"name": "Bosnian Urban Dragon",
			"description": "Common to the streets of Bosnia, can almost be considered a stray dog",
			"plunderedAt": "2025-10-17T16:34:02+00:00",
			"coolFactor": "1",
			"value": "200",
			"plunderedAtAgo": "20 minutes ago",
			"published": true
		}
	]
}
```

# Serialization Groups: some more on readable/writable property control

It often happens that you'll want to have a setter or getter to be available inside of your code but you don't want to expose it to the API. There are two good solutions for this: DTOs and serialization groups. Let's stick with the serialization groups for now. Serialization groups can be set through the `ApiResource` attribute with `normalizationContext` and `denormalizationContext`, which are about getting data from the API and setting data on the API, respectively.
  
```php
#[ApiResource(
	shortName: 'treasure',
	description: 'Dragon Treasure entity, represents... a Dragon Treasure, what did you expect',
	operations: [
		new Get(),
		new Put(),
		new Delete(),
		new Patch(),
		new Post(),
		new GetCollection(),
	],
	normalizationContext: ['groups' => ['treasure:read']],
	denormalizationContext: ['groups' => ['treasure:write']],
)]
```

Now if you try to send a **GET** request to the API you'll get a response with basically nothing. That's because now the API is set to send only whatever is in the normalization group. To mark some property as part of a group, you can set the group attribute right above it to the normalizationContext group. It also works for virtual properties if you put the group attribute above the method that defines it.

>[!info]
>You can change the name of a key in JSON by setting the attribute `SerializedName` right above it, it is particularly great for cases where you want to rename a virtual property.

# Some more control on deserialization: the constructor

If you want some data to be set only when the entity is being created and then never again, you can achieve so by removing the setter method, annotating it as part of the denormalizing group and attributing its value inside of the constructor.

If the name of the parameter on the constructor matches some property on the class, it will receive a corresponding key-value pair in the request JSON.
