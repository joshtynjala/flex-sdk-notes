## Code generation for `[Bindable]` metadata

A file named `BindableProperty.vm` exists in the `flex2.compiler.as3.binding` package. This template is used to generate a getter and setter for a property marked with `[Bindable]` metadata that doesn't specify an event. If the `[Bindable]` metadata specifies an event, then no code is generated, and the event should be dispatched manually from ActionScript.

A bindable variable may be defined like this:

	[Bindable]
	public var someProperty:String;

Using `BindableProperty.vm`, the compiler generates code to turn it into this:

	[Bindable(event="propertyChange")]
	public function get someProperty():String
	{
		return this._1377687758someProperty;
	}

	public function set someProperty(value:String):void
	{
		var oldValue:Object = this._1377687758someProperty;
		if (oldValue !== value)
		{
			this._1377687758someProperty = value;
			if (this.hasEventListener("propertyChange"))
				this.dispatchEvent(mx.events.PropertyChangeEvent.createUpdateEvent(this, "someProperty", oldValue, value));
		}
	}

This template can also handle static properties marked with `[Bindable]` metadata by creating a static event dispatcher.

In the case where the class doesn't implement `flash.events.IEventDispatcher`, this template can generate an implementation of the required functions like `addEventListener()` and `dispatchEvent()` automatically. These calls are passed to a separate, internal `flash.events.EventDispatcher` where `this` is passed into the constructor as a custom target.
