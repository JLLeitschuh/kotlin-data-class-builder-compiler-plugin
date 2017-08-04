# Kotlin Data Class Builder Compiler Plugin

## Proposal

The current implementation of data classes is really nice, however, creating large data classes can end up creating large constructors. I really like them because they create nicely immutable bundles of data.

In java, the builder pattern is usually utilized when constructors start to get large. However, the builder pattern can become quite clunky quickly, even when written by hand in Kotlin.

A developer could use the google auto-value annotation processor but I don't think this works with data classes. Plus its clunky and you have to deal with IDE configuration.

In Kotlin named parameters gets around this issue quite nicely because you can selectively specify the fields you want to assign. However, when creating a new instance of a data class in Java you end up with a very large constructor call without any way of knowing what fields you are assigning in the object when looking at the constructor.

My proposal is that data classes get expanded to have a static `builder()` method on them that allows data classes created from java to use this builder. Default values that the data classes already have wouldn't be required to be specified in the builder.
