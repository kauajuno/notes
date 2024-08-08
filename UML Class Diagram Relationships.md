Relationships are elements of a class diagram that defines the interaction between specific elements in the model. This definition by itself is pretty generic as there are different types of relationships.

# Generalization relationships

In this relationship, the child-class relates to the parent-class by acquiring all of its attributes, operations and relationships by default. The child and parent elements are often called subclass and superclass, respectively.

![[generalization-arrow-example.png]]

# Association relationships

Association is one of the most basic relationships, in which it indicates that two classes are somehow related. It can also indicate the multiplicity of the relationship (one-to-one, one-to-many, many-to-many).

![[association-arrow-example.png]]

# Aggregation relationships

Aggregation represents a "has-a" relationship. When a class "have" some other class, it is a aggregation relationship. Aggregations are a type of [[#Association relationships|association]].

![[aggregation-arrow-example.png]]

# Composition relationships

This relationship represents a "whole-part" relationship, in which the part-class lifetime is dependent on the whole-class lifetime. If the whole is gone, the part is also gone. Compositions are a type of [[#Aggregation relationships|aggregation]].

![[composition-arrow-example.png]]

# Realization

This is frequently seen as the arrow that connects classes to the interfaces they implement, because that's basically it: a relationship in which a blueprint class has its details implemented by another class.

![[realization-arrow-example.png]]

# Dependency

Dependency is a relationship in which some change in some class may affect the one that is dependent on it.

![[dependency-arrow-example.png]]
