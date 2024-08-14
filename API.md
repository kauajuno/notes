API is an acronym that stands for Application Programming Interface, and it's simple to understand how it works through the use of an analogy.

Let's suppose you go to a restaurant. You don't go straight to the kitchen and order the chef what you want him to cook. There's someone who does the bridge, that being the waitstaff. You place the order to the waitstaff and they return you the food. The same goes in web applications, the client can't talk directly to the server, there shall be an API that does the communication bridge between them. You make a [[HTTP Requests|HTTP request]] to the API and it retrieves the information for you.

APIs are meant to be used to get information that the client can't access directly, that means, information that isn't already on the client's cache/storage.

It's looking like the information only flows one way, from the server to the client, but that isn't true, and now it is time to diverge a little bit from the analogy. Aside from getting information, it's also possible to create, update or delete it from the server via the API. In more technical words: aside from the GET request, it's possible to make POST, PUT and DELETE requests.