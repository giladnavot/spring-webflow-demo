---
title: The FlowBuilderServices class
---
This document will cover the class <SwmToken path="spring-faces/src/main/java/org/springframework/faces/config/FlowBuilderServicesBuilder.java" pos="133:3:3" line-data="	public FlowBuilderServices build() {">`FlowBuilderServices`</SwmToken> in detail. We will cover:

1. What is <SwmToken path="spring-faces/src/main/java/org/springframework/faces/config/FlowBuilderServicesBuilder.java" pos="133:3:3" line-data="	public FlowBuilderServices build() {">`FlowBuilderServices`</SwmToken>
2. Variables and functions in <SwmToken path="spring-faces/src/main/java/org/springframework/faces/config/FlowBuilderServicesBuilder.java" pos="133:3:3" line-data="	public FlowBuilderServices build() {">`FlowBuilderServices`</SwmToken>

# What is <SwmToken path="spring-faces/src/main/java/org/springframework/faces/config/FlowBuilderServicesBuilder.java" pos="133:3:3" line-data="	public FlowBuilderServices build() {">`FlowBuilderServices`</SwmToken>

The <SwmToken path="spring-faces/src/main/java/org/springframework/faces/config/FlowBuilderServicesBuilder.java" pos="133:3:3" line-data="	public FlowBuilderServices build() {">`FlowBuilderServices`</SwmToken> class is a simple holder for configuring the services used by flow builders. These services are exposed to a builder in a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="29:12:12" line-data="import org.springframework.webflow.engine.builder.FlowBuilderContext;">`FlowBuilderContext`</SwmToken>. It does not attempt to default any service implementations other than the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="91:3:3" line-data="	public FlowArtifactFactory getFlowArtifactFactory() {">`FlowArtifactFactory`</SwmToken>, which is more like builder helper objects than a service. It is expected that clients inject <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="38:34:36" line-data=" * which is more like builder helper objects than a service. It is expected clients inject non-null references to">`non-null`</SwmToken> references to concrete service implementations appropriate for their environment.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="91">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="91:5:5" line-data="	public FlowArtifactFactory getFlowArtifactFactory() {">`getFlowArtifactFactory`</SwmToken> returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="91:3:3" line-data="	public FlowArtifactFactory getFlowArtifactFactory() {">`FlowArtifactFactory`</SwmToken> instance used for creating central Flow artifacts such as flows and states.

```java
	public FlowArtifactFactory getFlowArtifactFactory() {
		return flowArtifactFactory;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="94">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="95:5:5" line-data="	public void setFlowArtifactFactory(FlowArtifactFactory flowArtifactFactory) {">`setFlowArtifactFactory`</SwmToken> sets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="95:7:7" line-data="	public void setFlowArtifactFactory(FlowArtifactFactory flowArtifactFactory) {">`FlowArtifactFactory`</SwmToken> instance used for creating central Flow artifacts.

```java

	public void setFlowArtifactFactory(FlowArtifactFactory flowArtifactFactory) {
		this.flowArtifactFactory = flowArtifactFactory;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="99">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="99:5:5" line-data="	public ViewFactoryCreator getViewFactoryCreator() {">`getViewFactoryCreator`</SwmToken> returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="99:3:3" line-data="	public ViewFactoryCreator getViewFactoryCreator() {">`ViewFactoryCreator`</SwmToken> instance used for creating views to render during flow execution.

```java
	public ViewFactoryCreator getViewFactoryCreator() {
		return viewFactoryCreator;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="102">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="103:5:5" line-data="	public void setViewFactoryCreator(ViewFactoryCreator viewFactoryCreator) {">`setViewFactoryCreator`</SwmToken> sets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="103:7:7" line-data="	public void setViewFactoryCreator(ViewFactoryCreator viewFactoryCreator) {">`ViewFactoryCreator`</SwmToken> instance used for creating views to render during flow execution.

```java

	public void setViewFactoryCreator(ViewFactoryCreator viewFactoryCreator) {
		this.viewFactoryCreator = viewFactoryCreator;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="107">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="107:5:5" line-data="	public ConversionService getConversionService() {">`getConversionService`</SwmToken> returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="107:3:3" line-data="	public ConversionService getConversionService() {">`ConversionService`</SwmToken> instance used for converting from one object type to another.

```java
	public ConversionService getConversionService() {
		return conversionService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="110">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="111:5:5" line-data="	public void setConversionService(ConversionService conversionService) {">`setConversionService`</SwmToken> sets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="111:7:7" line-data="	public void setConversionService(ConversionService conversionService) {">`ConversionService`</SwmToken> instance used for converting from one object type to another.

```java

	public void setConversionService(ConversionService conversionService) {
		this.conversionService = conversionService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="115">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="115:5:5" line-data="	public ExpressionParser getExpressionParser() {">`getExpressionParser`</SwmToken> returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="115:3:3" line-data="	public ExpressionParser getExpressionParser() {">`ExpressionParser`</SwmToken> instance used for parsing expression strings into expression objects.

```java
	public ExpressionParser getExpressionParser() {
		return expressionParser;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="118">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="119:5:5" line-data="	public void setExpressionParser(ExpressionParser expressionParser) {">`setExpressionParser`</SwmToken> sets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="119:7:7" line-data="	public void setExpressionParser(ExpressionParser expressionParser) {">`ExpressionParser`</SwmToken> instance used for parsing expression strings into expression objects.

```java

	public void setExpressionParser(ExpressionParser expressionParser) {
		this.expressionParser = expressionParser;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="123">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="123:5:5" line-data="	public Validator getValidator() {">`getValidator`</SwmToken> returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="123:3:3" line-data="	public Validator getValidator() {">`Validator`</SwmToken> instance used for validating a model declared on a view state.

```java
	public Validator getValidator() {
		return validator;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="126">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="127:5:5" line-data="	public void setValidator(Validator validator) {">`setValidator`</SwmToken> sets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="127:7:7" line-data="	public void setValidator(Validator validator) {">`Validator`</SwmToken> instance used for validating a model declared on a view state.

```java

	public void setValidator(Validator validator) {
		this.validator = validator;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="131">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="131:5:5" line-data="	public ValidationHintResolver getValidationHintResolver() {">`getValidationHintResolver`</SwmToken> returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="131:3:3" line-data="	public ValidationHintResolver getValidationHintResolver() {">`ValidationHintResolver`</SwmToken> instance used for resolving string-based validation hints.

```java
	public ValidationHintResolver getValidationHintResolver() {
		return validationHintResolver;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="134">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="135:5:5" line-data="	public void setValidationHintResolver(ValidationHintResolver validationHintResolver) {">`setValidationHintResolver`</SwmToken> sets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="135:7:7" line-data="	public void setValidationHintResolver(ValidationHintResolver validationHintResolver) {">`ValidationHintResolver`</SwmToken> instance used for resolving string-based validation hints.

```java

	public void setValidationHintResolver(ValidationHintResolver validationHintResolver) {
		this.validationHintResolver = validationHintResolver;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="139">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="139:5:5" line-data="	public boolean getDevelopment() {">`getDevelopment`</SwmToken> returns whether or not the flow system is in development mode. In development mode, flows <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="87:33:35" line-data="	 * Whether or not the flow system is in development mode. In development mode, flows auto-refresh on change.">`auto-refresh`</SwmToken> on change.

```java
	public boolean getDevelopment() {
		return development;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="143">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="143:5:5" line-data="	public void setDevelopment(boolean development) {">`setDevelopment`</SwmToken> sets whether or not the flow system is in development mode.

```java
	public void setDevelopment(boolean development) {
		this.development = development;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="147">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="147:5:5" line-data="	public ApplicationContext getApplicationContext() {">`getApplicationContext`</SwmToken> returns the Spring application context that provides access to the services of the application.

```java
	public ApplicationContext getApplicationContext() {
		return applicationContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="153">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="153:5:5" line-data="	public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {">`setApplicationContext`</SwmToken> sets the Spring application context that provides access to the services of the application.

```java
	public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {
		this.applicationContext = applicationContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" line="159">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="159:5:5" line-data="	public void afterPropertiesSet() throws Exception {">`afterPropertiesSet`</SwmToken> ensures that all required properties are set after the bean properties have been set.

```java
	public void afterPropertiesSet() throws Exception {
		Assert.notNull(flowArtifactFactory, "The FlowArtifactFactory is required");
		Assert.notNull(viewFactoryCreator, "The ViewFactoryCreator is required");
		Assert.notNull(conversionService, "The type ConversionService is required");
		Assert.notNull(expressionParser, "The expressionParser is required");
		Assert.notNull(applicationContext, "The ApplicationContext is required");
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-faces/src/main/java/org/springframework/faces/config/FlowBuilderServicesBuilder.java" line="133">

---

The <SwmToken path="spring-faces/src/main/java/org/springframework/faces/config/FlowBuilderServicesBuilder.java" pos="133:3:3" line-data="	public FlowBuilderServices build() {">`FlowBuilderServices`</SwmToken> class is instantiated and configured in the <SwmToken path="spring-faces/src/main/java/org/springframework/faces/config/FlowBuilderServicesBuilder.java" pos="42:4:4" line-data="public class FlowBuilderServicesBuilder {">`FlowBuilderServicesBuilder`</SwmToken> class. This builder class creates an instance of <SwmToken path="spring-faces/src/main/java/org/springframework/faces/config/FlowBuilderServicesBuilder.java" pos="133:3:3" line-data="	public FlowBuilderServices build() {">`FlowBuilderServices`</SwmToken> and sets various services such as the conversion service, expression parser, and view factory creator.

```java
	public FlowBuilderServices build() {
		FlowBuilderServices flowBuilderServices = new FlowBuilderServices();
		flowBuilderServices.setConversionService(this.conversionService);
		flowBuilderServices.setExpressionParser(getExpressionParser());
		flowBuilderServices.setViewFactoryCreator(this.viewFactoryCreator);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" line="110">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="57:2:2" line-data="class FlowRegistryFactoryBean implements FactoryBean&lt;FlowDefinitionRegistry&gt;, BeanClassLoaderAware, InitializingBean,">`FlowRegistryFactoryBean`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="110:7:7" line-data="	public void setFlowBuilderServices(FlowBuilderServices flowBuilderServices) {">`FlowBuilderServices`</SwmToken> is used to hold the services needed to build flow definitions. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="110:5:5" line-data="	public void setFlowBuilderServices(FlowBuilderServices flowBuilderServices) {">`setFlowBuilderServices`</SwmToken> method is used to set the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="110:7:7" line-data="	public void setFlowBuilderServices(FlowBuilderServices flowBuilderServices) {">`FlowBuilderServices`</SwmToken> instance.

```java
	public void setFlowBuilderServices(FlowBuilderServices flowBuilderServices) {
		this.flowBuilderServices = flowBuilderServices;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderContextImpl.java" line="60">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="41:6:6" line-data=" * @see FlowBuilderContextImpl">`FlowBuilderContextImpl`</SwmToken> class uses <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderContextImpl.java" pos="60:6:6" line-data="			FlowDefinitionLocator flowDefinitionLocator, FlowBuilderServices flowBuilderServices) {">`FlowBuilderServices`</SwmToken> to provide access to additional services needed by the flow builder. The constructor of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderServices.java" pos="41:6:6" line-data=" * @see FlowBuilderContextImpl">`FlowBuilderContextImpl`</SwmToken> takes <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderContextImpl.java" pos="60:6:6" line-data="			FlowDefinitionLocator flowDefinitionLocator, FlowBuilderServices flowBuilderServices) {">`FlowBuilderServices`</SwmToken> as a parameter and initializes it.

```java
			FlowDefinitionLocator flowDefinitionLocator, FlowBuilderServices flowBuilderServices) {
		Assert.hasText(flowId, "The flow id is required");
		Assert.notNull(flowDefinitionLocator, "The flow definition locator is required");
		Assert.notNull(flowBuilderServices, "The flow builder services holder is required");
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderContextImpl.java" line="71">

---

Additionally, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderContextImpl.java" pos="71:5:5" line-data="	public FlowBuilderServices getFlowBuilderServices() {">`getFlowBuilderServices`</SwmToken> method is used to retrieve the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/FlowBuilderContextImpl.java" pos="71:3:3" line-data="	public FlowBuilderServices getFlowBuilderServices() {">`FlowBuilderServices`</SwmToken> instance.

```java
	public FlowBuilderServices getFlowBuilderServices() {
		return flowBuilderServices;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" line="59">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" pos="51:4:4" line-data="public class FlowDefinitionRegistryBuilder {">`FlowDefinitionRegistryBuilder`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" pos="59:3:3" line-data="	private FlowBuilderServices flowBuilderServices;">`FlowBuilderServices`</SwmToken> is used to manage the services required for building flow definitions. It is stored as a private member and is essential for the flow definition registry.

```java
	private FlowBuilderServices flowBuilderServices;

```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
