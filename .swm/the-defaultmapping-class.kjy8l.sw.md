---
title: The DefaultMapping class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="59:3:3" line-data="	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {">`DefaultMapping`</SwmToken> in the Spring Web Flow project. We will discuss:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="59:3:3" line-data="	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {">`DefaultMapping`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="59:3:3" line-data="	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {">`DefaultMapping`</SwmToken>.

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="59:3:3" line-data="	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {">`DefaultMapping`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="59:3:3" line-data="	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {">`DefaultMapping`</SwmToken> class in <SwmPath>[spring-binding/…/impl/DefaultMapping.java](spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java)</SwmPath> is a single mapping definition. It encapsulates the information necessary to map the result of evaluating an expression on a source object to a property on a target object, optionally applying a type conversion during the mapping process.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="59">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="59:3:3" line-data="	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {">`DefaultMapping`</SwmToken> is the constructor of the class. It initializes the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="59:7:7" line-data="	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {">`sourceExpression`</SwmToken> and <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="59:12:12" line-data="	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {">`targetExpression`</SwmToken> variables, ensuring they are not null.

```java
	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {
		Assert.notNull(sourceExpression, "The source expression is required");
		Assert.notNull(targetExpression, "The target expression is required");
		this.sourceExpression = sourceExpression;
		this.targetExpression = targetExpression;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="68">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="68:5:5" line-data="	public Expression getSourceExpression() {">`getSourceExpression`</SwmToken> returns the source expression to evaluate against a source object to map from.

```java
	public Expression getSourceExpression() {
		return sourceExpression;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="72">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="72:5:5" line-data="	public Expression getTargetExpression() {">`getTargetExpression`</SwmToken> returns the target expression to set on a target object to map to.

```java
	public Expression getTargetExpression() {
		return targetExpression;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="76">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="76:5:5" line-data="	public boolean isRequired() {">`isRequired`</SwmToken> returns whether or not this is a required mapping; if true, the source expression must return a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="45:37:39" line-data="	 * Whether or not this is a required mapping; if true, the source expression must return a non-null value.">`non-null`</SwmToken> value.

```java
	public boolean isRequired() {
		return required;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="85">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="85:5:5" line-data="	public ConversionExecutor getTypeConverter() {">`getTypeConverter`</SwmToken> returns the type conversion executor to use during mapping execution. It may be null.

```java
	public ConversionExecutor getTypeConverter() {
		return typeConverter;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="89">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="93:5:5" line-data="	public void setTypeConverter(ConversionExecutor typeConverter) {">`setTypeConverter`</SwmToken> sets a specific type conversion executor to use during mapping execution.

```java
	/**
	 * Sets a specific type conversion executor to use during mapping execution.
	 * @param typeConverter the type converter
	 */
	public void setTypeConverter(ConversionExecutor typeConverter) {
		this.typeConverter = typeConverter;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="97">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="101:5:5" line-data="	public void setRequired(boolean required) {">`setRequired`</SwmToken> indicates if this mapping is a required mapping. The default is false.

```java
	/**
	 * Indicates if this mapping is a required mapping. Default is false.
	 * @param required required status
	 */
	public void setRequired(boolean required) {
		this.required = required;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="105">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="109:5:5" line-data="	public void map(DefaultMappingContext context) {">`map`</SwmToken> executes this mapping. It evaluates the source expression, applies type conversion if necessary, and sets the target expression.

```java
	/**
	 * Execute this mapping.
	 * @param context the mapping context
	 */
	public void map(DefaultMappingContext context) {
		context.setCurrentMapping(this);
		Object sourceValue;
		try {
			sourceValue = sourceExpression.getValue(context.getSource());
		} catch (EvaluationException e) {
			context.setSourceAccessError(e);
			return;
		}
		if (required && (sourceValue == null || isEmptyString(sourceValue))) {
			context.setRequiredErrorResult(sourceValue);
			return;
		}
		Object targetValue = sourceValue;
		if (sourceValue != null) {
			if (typeConverter != null) {
				try {
					targetValue = typeConverter.execute(sourceValue);
				} catch (ConversionExecutionException e) {
					context.setTypeConversionErrorResult(sourceValue, e);
					return;
				}
			}
		}
		try {
			targetExpression.setValue(context.getTarget(), targetValue);
			context.setSuccessResult(sourceValue, targetValue);
		} catch (EvaluationException e) {
			context.setTargetAccessError(sourceValue, e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="141">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="141:5:5" line-data="	private boolean isEmptyString(Object sourceValue) {">`isEmptyString`</SwmToken> checks if the given source value is an empty string.

```java
	private boolean isEmptyString(Object sourceValue) {
		if (sourceValue instanceof CharSequence) {
			return ((CharSequence) sourceValue).length() == 0;
		} else {
			return false;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="149">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="149:5:5" line-data="	public boolean equals(Object o) {">`equals`</SwmToken> checks if the given object is equal to this <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="150:10:10" line-data="		if (!(o instanceof DefaultMapping)) {">`DefaultMapping`</SwmToken> instance by comparing the source and target expressions.

```java
	public boolean equals(Object o) {
		if (!(o instanceof DefaultMapping)) {
			return false;
		}
		DefaultMapping other = (DefaultMapping) o;
		return sourceExpression.equals(other.sourceExpression) && targetExpression.equals(other.targetExpression);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="157">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="157:5:5" line-data="	public int hashCode() {">`hashCode`</SwmToken> returns the hash code of this <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="59:3:3" line-data="	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {">`DefaultMapping`</SwmToken> instance, calculated from the source and target expressions.

```java
	public int hashCode() {
		return sourceExpression.hashCode() + targetExpression.hashCode();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="161">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="161:5:5" line-data="	public String toString() {">`toString`</SwmToken> returns a string representation of this <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="59:3:3" line-data="	public DefaultMapping(Expression sourceExpression, Expression targetExpression) {">`DefaultMapping`</SwmToken> instance, showing the source and target expressions.

```java
	public String toString() {
		return sourceExpression + " -> " + targetExpression;
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="444">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="73:6:6" line-data="public abstract class AbstractMvcView implements View {">`AbstractMvcView`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="447:1:1" line-data="		DefaultMapping mapping = new DefaultMapping(source, target);">`DefaultMapping`</SwmToken> is used to create a mapping between a source expression and a target expression. This is done by first creating an expression for the source and target, and then initializing a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="447:1:1" line-data="		DefaultMapping mapping = new DefaultMapping(source, target);">`DefaultMapping`</SwmToken> object with these expressions. The mapping is then configured to be required if specified, and a conversion service is asserted if a converter is provided.

```java
		Expression source = new RequestParameterExpression(binding.getProperty());
		ParserContext parserContext = new SimpleParserContext(model.getClass());
		Expression target = expressionParser.parseExpression(binding.getProperty(), parserContext);
		DefaultMapping mapping = new DefaultMapping(source, target);
		mapping.setRequired(binding.getRequired());
		if (binding.getConverter() != null) {
			Assert.notNull(conversionService,
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" line="449">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="120:4:4" line-data="public class FlowModelFlowBuilder extends AbstractFlowBuilder {">`FlowModelFlowBuilder`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="452:1:1" line-data="		DefaultMapping mapping = new DefaultMapping(source, target);">`DefaultMapping`</SwmToken> is used in methods like <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="433:5:5" line-data="				inputMapper.addMapping(parseFlowInputMapping(inputModel));">`parseFlowInputMapping`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="462:5:5" line-data="				inputMapper.addMapping(parseSubflowInputMapping(inputModel));">`parseSubflowInputMapping`</SwmToken>. These methods parse expressions for the source and target, create a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="452:1:1" line-data="		DefaultMapping mapping = new DefaultMapping(source, target);">`DefaultMapping`</SwmToken> object, and then configure the mapping with conversion executors and required settings based on the input model.

```java
		}
		Expression source = parser.parseExpression(name, new FluentParserContext().evaluate(MutableAttributeMap.class));
		Expression target = parser.parseExpression(value, new FluentParserContext().evaluate(RequestContext.class));
		DefaultMapping mapping = new DefaultMapping(source, target);
		parseAndSetMappingConversionExecutor(input, mapping);
		parseAndSetMappingRequired(input, mapping);
		return mapping;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" line="45">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" pos="45:3:3" line-data="	public DefaultMapper addMapping(DefaultMapping mapping) {">`DefaultMapper`</SwmToken> class, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" pos="45:7:7" line-data="	public DefaultMapper addMapping(DefaultMapping mapping) {">`DefaultMapping`</SwmToken> objects are added to a list of mappings. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" pos="45:5:5" line-data="	public DefaultMapper addMapping(DefaultMapping mapping) {">`addMapping`</SwmToken> method allows for programmatically configuring mappings by adding <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" pos="45:7:7" line-data="	public DefaultMapper addMapping(DefaultMapping mapping) {">`DefaultMapping`</SwmToken> instances to the mapper. These mappings are then applied in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" pos="58:5:5" line-data="	public MappingResults map(Object source, Object target) {">`map`</SwmToken> method, which iterates over the list of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" pos="45:7:7" line-data="	public DefaultMapper addMapping(DefaultMapping mapping) {">`DefaultMapping`</SwmToken> objects and applies each mapping to the provided context.

```java
	public DefaultMapper addMapping(DefaultMapping mapping) {
		mappings.add(mapping);
		return this;
	}

	/**
	 * Returns this mapper's list of mappings.
	 * @return the list of mappings
	 */
	public Mapping[] getMappings() {
		return mappings.toArray(new Mapping[mappings.size()]);
	}

	public MappingResults map(Object source, Object target) {
		if (logger.isDebugEnabled()) {
			logger.debug("Beginning mapping between source [" + source.getClass().getName() + "] and target ["
					+ target.getClass().getName() + "]");
		}
		DefaultMappingContext context = new DefaultMappingContext(source, target);
		for (DefaultMapping mapping : mappings) {
			mapping.map(context);
		}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
