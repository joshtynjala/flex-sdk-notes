# MXML Document Special Attributes

A number of special attributes may be specified on an MXML document, like `implements`, `pageTitle` or `preloader`. These attributes are defined in the `flex2.compiler.mxml.builder.DocumentBuilder` class. Even if the component does not define properties with these names, the compiler will accept these attributes as valid. The compiler can handle them without setting their values on the component instance.

Special attributes are stored in the `specialAttributes2006` and `specialAttributes2009` static variables. Which set of special attributes is accepted by the compiler depends on which MXML namespace is specified.

In `flex2.compiler.mxml.builder.ComponentBuilder`, the super class of `DocumentBuilder`, has an inner class named `ComponentAttributeHandler`. These special attributes are passed to its `special()` method. However, this method does nothing.

`DocumentBuilder` defines its own inner class named `DocumentAttributeHandler`. However, this class is never used. Perhaps it was meant to be used and forgotten, or it could be legacy code that was not completely removed. Regadless, the `special()` method from `ComponentAttributeHandler` may be overridden in `DocumentAttributeHandler`. To use `DocumentAttributeHandler`, set the `attributeHandler` property of `DocumentBuilder` to a new instance of `DocumentAttributeHandler` in the `DocumentBuilder` constructor after the call to `super()`.

`DocumentAttributeHandler` already overrides the `dynamicProperty()` method. However, since `DocumentAttributeHandler` was not used, it is probably best to remove this override to avoid unintended conflicts.
