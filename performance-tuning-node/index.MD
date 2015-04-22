# Performance Tuning Node
### Writing Performant Code
* Write JavaScript like you would write C
* Keep function signatures consistent
* Use constructors and factory methods to ensure properties are added in the same order.
* Keep object maps the same, declare ALL property values (even if null/undefined)
* Avoid mixing types in arrays.
* Use named functions, avoid anonymous closures
* Apparently... keep function size < 600 characters (bytes) ...Seriously! (v8 optimization! Ignore unless super serious about performant Node.) Comments count against it!

###
