Now let's send some requests and test your API.

**GET** requests are used to retrieve data.
**POST** requests are used to create data.
**DELETE** requests are used to delete data.
**PATCH** requests are used to update data.

Start by creating some data for your API. Go to the **POST** request, click on it and click on "Try it out".

```json
{
	"name": "Cryo Brazilian Dragon",
	"description": "Scream if you love brazilian cold afternoons! This one is so cool especially because it mixes things that should not be mixed at all, such as Brazil and cold",
	"createdAt": "2025-10-16T15:46:57.953Z",
	"coolFactor": 94,
	"value": 128400,
	"isPublished": true
}
```

Create as many as you want. Then go to the **GET** /dragon_treasures endpoint and try it out. You'll end up with a list just like this one:

```json
{
	"@context": "/contexts/DragonTreasure",
	"@id": "/dragon_treasures",
	"@type": "Collection",
	"totalItems": 2,
	"member": [
		{
			"@id": "/dragon_treasures/1",
			"@type": "DragonTreasure",
			"id": 1,
			"name": "Electric Argentinian Dragon",
			"description": "American southern culture classic",
			"createdAt": "2025-10-16T15:46:57+00:00",
			"coolFactor": "12",
			"value": "12000",
			"published": true
		},
		{
			"@id": "/dragon_treasures/2",
			"@type": "DragonTreasure",
			"id": 2,
			"name": "Cryo Brazilian Dragon",
			"description": "Scream if you love brazilian cold afternoons! This one is so cool especially because it mixes things that should not be mixed at all, such as Brazil and cold",
			"createdAt": "2025-10-16T15:46:57+00:00",
			"coolFactor": "94",
			"value": "128400",
			"published": true
		}
	]
}
```

In order to visualize all the routes available on your application, use the following command:

```bash
docker compose exec php php bin/console debug:router
```

