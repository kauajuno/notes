The MVC pattern segregates the application into three components: Model, View and Controller, with each of them having different concerns.

# Controller

The Controller component is responsible for handling requests and sending responses to the user. It is called a Controller for a reason: this is the components that interacts with both of the other two in order to process the requests received, it manages everything so the other two components don't have to interact with each other.

# Model

The Model component is responsible for handling the application data logic, so it is the component responsible for querying for some requested data in a database, for example. Note that it is activated by the Controller and the Controller only.

# View

The View component is responsible for whatever is going to be rendered to the user in its screen. For example, if the Controller got some data from the model, how it will be rendered to the user is a responsibility of the View component. If the request resulted in some kind of error, the Controller will handle it, but the View needs to be ready to show an error screen, for example.