In JavaScript, variables are dynamically typed, which means it isn't needed to specify the type of a variable. Also, there are 3 keywords that allow the programmer to declare variables, but each of them work in their own different way.

# Declaring with `var`

This one creates a function-scoped variable, which means it can be accessed anywhere in the function in which it was declared.

# Declaring with `let`

Declaring a variable with let implies that it is block-scoped. In other words, that variable will only be visible within the block in which it was declared.

# Declaring with `const`

Lastly, this one also creates a block-scoped variable, but as the name suggests, it is a read-only variable, so it can't have its value changed after it is assigned.

>[!info]
>Note that arrays in JavaScript are objects, implying that modifications to the array can be made even though they are declared with const. The thing being changed is the object's content, is is not the object itself that is being replaced.

# Good practices

As there are many ways to declare variables, there's also recommendations on how to use them:

- Prefer using `let`and `const` over `var`.
- Use `const` by default unless it is known that a variable has to be changed.

# Declaring with... nothing?

If you just assign a variable without using any of the 3 keywords mentioned previously, it becomes a global variable, that can be seen from anywhere in the code. This is discouraged as it can pollute the global namespace and create scope issues such as overwriting previously declared variables.

