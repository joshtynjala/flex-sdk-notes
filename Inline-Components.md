# Inline Components with `<fx:Component>`

The `flex2.compiler.mxml.InterfaceCompiler` class defines a function named `createInlineComponentUnit()` that extracts the MXML code for an inline component and copies it to a virtual file. The inline component will now be treated like a separate MXML file by the compiler.

The `flex2.compiler.mxml.builder.InlineComponentBuilder` class takes the ActionScript class generated for the inline component and passes it to the `factoryFromClass()` function defined in `flex2.compiler.mxml.builder.AbstractBuilder`. The `factoryFromClass` function takes a reference to a fully-qualified ActionScript class name and uses it to create an `mx.core.ClassFactory`. The generated class for the inline component is passed here from 

The `flex2.compiler.mxml.rep.init.ValueInitializer` class defines a function named `getDefinitionBody()` where objects defined in MXML are instantiated. This includes the `mx.core.ClassFactory` for the inline component.
