---
title: The BinderConfiguration class
---
This document will cover the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" pos="160:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken> class. We will explain:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" pos="160:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken> is.
2. The variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" pos="160:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" pos="160:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken>

<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" pos="160:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken> is a class in the Spring Web Flow framework, located in <SwmPath>[spring-webflow/…/builder/BinderConfiguration.java](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java)</SwmPath>. It contains the information needed to bind a model to a view. This information consists of one or more bindings that connect properties of the model to UI elements of the view.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="25">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="25:5:5" line-data="	public void addBinding(Binding binding) {">`addBinding`</SwmToken> is used to add a new binding to the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" pos="160:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken>.

```java
	public void addBinding(Binding binding) {
		bindings.add(binding);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="32">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="32:8:8" line-data="	public Set&lt;Binding&gt; getBindings() {">`getBindings`</SwmToken> returns the set of bindings associated with the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" pos="160:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken>.

```java
	public Set<Binding> getBindings() {
		return bindings;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="41">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="41:5:5" line-data="	public Binding getBinding(String name) {">`getBinding`</SwmToken> gets the binding with the specified name, or returns null if no such binding is found.

```java
	public Binding getBinding(String name) {
		for (Binding binding : bindings) {
			if (name.equals(binding.getProperty())) {
				return binding;
			}
		}
		return null;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="57">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="57:5:5" line-data="	public String getConverterId(String name) {">`getConverterId`</SwmToken> gets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="51:7:7" line-data="	 * Gets the converterId for the binding with the specified name. Returns null if either a binding or a converterId">`converterId`</SwmToken> for the binding with the specified name. Returns null if either a binding or a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="51:7:7" line-data="	 * Gets the converterId for the binding with the specified name. Returns null if either a binding or a converterId">`converterId`</SwmToken> for the given name is not found.

```java
	public String getConverterId(String name) {
		Binding binding = getBinding(name);
		if (binding != null) {
			return binding.getConverter();
		} else {
			return null;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="71">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="71:9:9" line-data="	public static final class Binding {">`Binding`</SwmToken> is a static inner class that provides the information needed to connect an element of the view to a property of the model.

```java
	public static final class Binding {

		private String property;

		private String converter;

		private boolean required;

		/**
		 * Creates a new view binding
		 * @param property the model property to bind to
		 * @param converter the id of a custom converter to apply type conversion during binding
		 * @param required whether this binding is required
		 */
		public Binding(String property, String converter, boolean required) {
			Assert.hasText(property, "The property is required");
			this.property = property;
			this.converter = converter;
			this.required = required;
		}

		public boolean equals(Object object) {
			if (!(object instanceof Binding)) {
				return false;
			}
			Binding binding = (Binding) object;
			return property.equals(binding.property);
		}

		public int hashCode() {
			return property.hashCode();
		}

		/**
		 * The name of the bound property.
		 * @return the property
		 */
		public String getProperty() {
			return property;
		}

		/**
		 * The id of the custom converter to use to convert bound property values.
		 * @return the converter id, or null
		 */
		public String getConverter() {
			return converter;
		}

		/**
		 * Whether a non-empty value is required for each binding attempt.
		 * @return the required status
		 */
		public boolean getRequired() {
			return required;
		}

		public String toString() {
			return new ToStringCreator(this).append("property", property).append("converter", converter)
					.append("required", required).toString();
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="92">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="92:5:5" line-data="		public boolean equals(Object object) {">`equals`</SwmToken> checks if the given object is equal to the current binding.

```java
		public boolean equals(Object object) {
			if (!(object instanceof Binding)) {
				return false;
			}
			Binding binding = (Binding) object;
			return property.equals(binding.property);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="100">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="100:5:5" line-data="		public int hashCode() {">`hashCode`</SwmToken> returns the hash code of the binding's property.

```java
		public int hashCode() {
			return property.hashCode();
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="108">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="108:5:5" line-data="		public String getProperty() {">`getProperty`</SwmToken> returns the name of the bound property.

```java
		public String getProperty() {
			return property;
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="116">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="116:5:5" line-data="		public String getConverter() {">`getConverter`</SwmToken> returns the id of the custom converter to use to convert bound property values.

```java
		public String getConverter() {
			return converter;
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="124">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="124:5:5" line-data="		public boolean getRequired() {">`getRequired`</SwmToken> returns whether a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="121:7:9" line-data="		 * Whether a non-empty value is required for each binding attempt.">`non-empty`</SwmToken> value is required for each binding attempt.

```java
		public boolean getRequired() {
			return required;
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" line="128">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/BinderConfiguration.java" pos="128:5:5" line-data="		public String toString() {">`toString`</SwmToken> returns a string representation of the binding.

```java
		public String toString() {
			return new ToStringCreator(this).append("property", property).append("converter", converter)
					.append("required", required).toString();
		}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" line="159">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" pos="55:4:4" line-data="public class MvcViewFactoryCreator implements ViewFactoryCreator {">`MvcViewFactoryCreator`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" pos="160:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken> is used as a parameter in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/builder/MvcViewFactoryCreator.java" pos="159:5:5" line-data="	public ViewFactory createViewFactory(Expression viewId, ExpressionParser expressionParser,">`createViewFactory`</SwmToken> method. This method is responsible for creating a view factory with the specified configuration, including the binder configuration.

```java
	public ViewFactory createViewFactory(Expression viewId, ExpressionParser expressionParser,
			ConversionService conversionService, BinderConfiguration binderConfiguration,
			Validator validator, ValidationHintResolver validationHintResolver) {
		if (useSpringBeanBinding) {
			expressionParser = new BeanWrapperExpressionParser(conversionService);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="74">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="676:3:3" line-data="			List&lt;BindingModel&gt; bindings = binderModel.getBindings();">`BindingModel`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="74:3:3" line-data="	private BinderConfiguration binderConfiguration;">`BinderConfiguration`</SwmToken> is used to set and get the binder configuration for the binding model. This configuration describes how the model should bind to the view.

```java
	private BinderConfiguration binderConfiguration;

	/**
	 * Creates a new Spring Binding model.
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcViewFactory.java" line="65">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcViewFactory.java" pos="65:3:3" line-data="	public AbstractMvcViewFactory(Expression viewId, FlowViewResolver viewResolver, ExpressionParser expressionParser,">`AbstractMvcViewFactory`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcViewFactory.java" pos="66:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken> is used as a parameter in the constructor to initialize the view factory with the specified binder configuration.

```java
	public AbstractMvcViewFactory(Expression viewId, FlowViewResolver viewResolver, ExpressionParser expressionParser,
			ConversionService conversionService, BinderConfiguration binderConfiguration,
			MessageCodesResolver messageCodesResolver) {
		this.viewId = viewId;
		this.viewResolver = viewResolver;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="149">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="54:6:6" line-data=" * @see AbstractMvcView">`AbstractMvcView`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="149:7:7" line-data="	public void setBinderConfiguration(BinderConfiguration binderConfiguration) {">`BinderConfiguration`</SwmToken> is used to set and get the binder configuration for the view. This configuration defines how to connect properties of the model to UI elements.

```java
	public void setBinderConfiguration(BinderConfiguration binderConfiguration) {
		this.binderConfiguration = binderConfiguration;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcViewFactory.java" line="44">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcViewFactory.java" pos="44:3:3" line-data="	public ServletMvcViewFactory(Expression viewId, FlowViewResolver viewResolver, ExpressionParser expressionParser,">`ServletMvcViewFactory`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcViewFactory.java" pos="45:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken> is used as a parameter in the constructor to create a new instance of the view factory with the specified binder configuration.

```java
	public ServletMvcViewFactory(Expression viewId, FlowViewResolver viewResolver, ExpressionParser expressionParser,
			ConversionService conversionService, BinderConfiguration binderConfiguration,
			MessageCodesResolver messageCodesResolver) {
		super(viewId, viewResolver, expressionParser, conversionService, binderConfiguration, messageCodesResolver);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" line="667">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="120:4:4" line-data="public class FlowModelFlowBuilder extends AbstractFlowBuilder {">`FlowModelFlowBuilder`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="667:1:1" line-data="		BinderConfiguration binderConfiguration = createBinderConfiguration(binderModel);">`BinderConfiguration`</SwmToken> is created and used to configure the view factory. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="667:7:7" line-data="		BinderConfiguration binderConfiguration = createBinderConfiguration(binderModel);">`createBinderConfiguration`</SwmToken> method constructs a new <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="667:1:1" line-data="		BinderConfiguration binderConfiguration = createBinderConfiguration(binderModel);">`BinderConfiguration`</SwmToken> instance based on the provided <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="673:7:7" line-data="	private BinderConfiguration createBinderConfiguration(BinderModel binderModel) {">`BinderModel`</SwmToken>.

```java
		BinderConfiguration binderConfiguration = createBinderConfiguration(binderModel);
		return getLocalContext().getViewFactoryCreator().createViewFactory(viewId,
				getLocalContext().getExpressionParser(), getLocalContext().getConversionService(), binderConfiguration,
				getLocalContext().getValidator(), getLocalContext().getValidationHintResolver());
	}

	private BinderConfiguration createBinderConfiguration(BinderModel binderModel) {
		if (binderModel != null && binderModel.getBindings() != null) {
			BinderConfiguration binderConfiguration = new BinderConfiguration();
			List<BindingModel> bindings = binderModel.getBindings();
			for (BindingModel bindingModel : bindings) {
				boolean required = false;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-faces/src/main/java/org/springframework/faces/webflow/JsfViewFactoryCreator.java" line="40">

---

In the <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/JsfViewFactoryCreator.java" pos="34:4:4" line-data="public class JsfViewFactoryCreator implements ViewFactoryCreator {">`JsfViewFactoryCreator`</SwmToken> class, <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/JsfViewFactoryCreator.java" pos="41:6:6" line-data="			ConversionService conversionService, BinderConfiguration binderConfiguration,">`BinderConfiguration`</SwmToken> is used as a parameter in the <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/JsfViewFactoryCreator.java" pos="40:5:5" line-data="	public ViewFactory createViewFactory(Expression viewIdExpression, ExpressionParser expressionParser,">`createViewFactory`</SwmToken> method to create a new JSF view factory with the specified binder configuration.

```java
	public ViewFactory createViewFactory(Expression viewIdExpression, ExpressionParser expressionParser,
			ConversionService conversionService, BinderConfiguration binderConfiguration,
			Validator validator, ValidationHintResolver resolver) {
		return new JsfViewFactory(viewIdExpression, getLifecycle());
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
