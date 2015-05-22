# Startup and Preloader

The `flex2.tools.PreLink` class generates the startup code that can display a preloader and bootstrap the application. This is where the `SystemManager` is made the root of a Flex application.

The `swfmetadata()` function parses the attributes of `[SWF]` metadata like `frameRate` and `backgroundColor`.

The `codegenModuleFactory()` function generates a subclass of the class specified in the `factoryClass` attribute of `[Frame]` metadata. This subclass overrides the `info()` function to pass in a number of configuration properties. These configuration properties are written to the subclass in `codegenInfo()`.

## Related Links

* [Feathers MXML internals: abstracting away Starling initialization](http://joshblog.net/2015/feathers-mxml-internals-abstracting-away-starling-initialization/)
* [Flex Non-Docs: metadata.Frame](http://nondocs.blogspot.com/2007/04/metadataframe_22.html)
