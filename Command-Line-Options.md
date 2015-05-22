# Command Line Options

How the Flex compiler defines command line options is not particularly easy to discover. In the `flex2.compiler.config.ConfigurationBuffer` class, the compiler seems to use reflection to look for method names in the `flex2.compiler.common.CompilerConfiguration` class that follow specific naming conventions. Using these discovered methods, `ConfigurationBuffer` extracts the names of the available command line options at runtime.

For example, the `--compiler.theme` option is defined by adding the following two functions to the `CompilerConfiguration` class:

	public void cfgTheme( ConfigurationValue cv, List paths ) throws ConfigurationException
	public static ConfigurationInfo getThemeInfo()
