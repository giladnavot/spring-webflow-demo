---
title: The DefaultMappingContext class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="50:3:3" line-data="	public DefaultMappingContext(Object source, Object target) {">`DefaultMappingContext`</SwmToken> in the Spring Web Flow project. We will discuss:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="50:3:3" line-data="	public DefaultMappingContext(Object source, Object target) {">`DefaultMappingContext`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="50:3:3" line-data="	public DefaultMappingContext(Object source, Object target) {">`DefaultMappingContext`</SwmToken>.

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="50:3:3" line-data="	public DefaultMappingContext(Object source, Object target) {">`DefaultMappingContext`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="50:3:3" line-data="	public DefaultMappingContext(Object source, Object target) {">`DefaultMappingContext`</SwmToken> class is a default implementation of a mapping context in the Spring Web Flow project. It is used to manage the context of a mapping operation, including the source and target objects, the current mapping being processed, and the results of the mapping operations.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="50">

---

The constructor <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="50:3:3" line-data="	public DefaultMappingContext(Object source, Object target) {">`DefaultMappingContext`</SwmToken> initializes the context with the source and target objects and prepares an empty list to store mapping results.

```java
	public DefaultMappingContext(Object source, Object target) {
		this.source = source;
		this.target = target;
		this.mappingResults = new ArrayList<>();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="59">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="59:5:5" line-data="	public Object getSource() {">`getSource`</SwmToken> returns the source object being mapped from.

```java
	public Object getSource() {
		return source;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="66">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="66:5:5" line-data="	public Object getTarget() {">`getTarget`</SwmToken> returns the target object being mapped to.

```java
	public Object getTarget() {
		return target;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="74">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="74:5:5" line-data="	public Mapping getCurrentMapping() {">`getCurrentMapping`</SwmToken> returns the current mapping being processed.

```java
	public Mapping getCurrentMapping() {
		return currentMapping;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="83">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="83:5:5" line-data="	public void setCurrentMapping(Mapping mapping) {">`setCurrentMapping`</SwmToken> sets the current mapping. It is called when a single mapping operation is about to begin and updates the progress of the overall mapping transaction.

```java
	public void setCurrentMapping(Mapping mapping) {
		if (currentMapping != null) {
			throw new IllegalStateException("The current mapping has not finished yet");
		}
		currentMapping = mapping;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="96">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="96:5:5" line-data="	public void setSuccessResult(Object originalValue, Object mappedValue) {">`setSuccessResult`</SwmToken> indicates that the current mapping completed successfully. It records the original value from the source and the successfully mapped value.

```java
	public void setSuccessResult(Object originalValue, Object mappedValue) {
		add(new Success(currentMapping, mappedValue, originalValue));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="105">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="105:5:5" line-data="	public void setRequiredErrorResult(Object originalValue) {">`setRequiredErrorResult`</SwmToken> indicates that the current mapping ended with a 'required' error, meaning the value obtained from the source was empty and the mapping could not be completed.

```java
	public void setRequiredErrorResult(Object originalValue) {
		add(new RequiredError(currentMapping, originalValue));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="115">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="115:5:5" line-data="	public void setTypeConversionErrorResult(Object originalValue, Exception cause) {">`setTypeConversionErrorResult`</SwmToken> indicates that the current mapping ended with a 'type conversion' error, meaning the value obtained from the source could not be converted to a type that could be assigned to the target expression.

```java
	public void setTypeConversionErrorResult(Object originalValue, Exception cause) {
		add(new TypeConversionError(currentMapping, originalValue, cause));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="123">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="123:5:5" line-data="	public void setSourceAccessError(EvaluationException error) {">`setSourceAccessError`</SwmToken> indicates that an error occurred while accessing the source mapping expression.

```java
	public void setSourceAccessError(EvaluationException error) {
		add(new SourceAccessError(currentMapping, error));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="132">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="131:5:5" line-data="	public void setTargetAccessError(Object originalValue, EvaluationException error) {">`setTargetAccessError`</SwmToken> indicates that an error occurred while accessing the target mapping expression.

```java
		add(new TargetAccessError(currentMapping, originalValue, error));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="140">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="139:5:5" line-data="	public MappingResults getMappingResults() {">`getMappingResults`</SwmToken> returns the mapping results recorded in this context.

```java
		return new DefaultMappingResults(source, target, mappingResults);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" line="145">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingContext.java" pos="145:5:5" line-data="	private void add(MappingResult result) {">`add`</SwmToken> is an internal helper that adds a mapping result to the list of mapping results and resets the current mapping.

```java
	private void add(MappingResult result) {
		if (logger.isDebugEnabled()) {
			logger.debug("Adding mapping result " + result);
		}
		mappingResults.add(result);
		currentMapping = null;
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" line="60">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" pos="34:4:4" line-data="public class DefaultMapper implements Mapper {">`DefaultMapper`</SwmToken> class, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" pos="63:1:1" line-data="		DefaultMappingContext context = new DefaultMappingContext(source, target);">`DefaultMappingContext`</SwmToken> is instantiated to facilitate the mapping process between a source and a target. The context is created with the source and target objects, and then it is used in a loop to apply each <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" pos="64:4:4" line-data="		for (DefaultMapping mapping : mappings) {">`DefaultMapping`</SwmToken> to the context.

```java
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

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" line="106">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapper.java" pos="64:4:4" line-data="		for (DefaultMapping mapping : mappings) {">`DefaultMapping`</SwmToken> class, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="109:7:7" line-data="	public void map(DefaultMappingContext context) {">`DefaultMappingContext`</SwmToken> is used to execute a mapping. The context is passed as a parameter to the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMapping.java" pos="109:5:5" line-data="	public void map(DefaultMappingContext context) {">`map`</SwmToken> method, where it sets the current mapping and handles the mapping logic.

```java
	 * Execute this mapping.
	 * @param context the mapping context
	 */
	public void map(DefaultMappingContext context) {
		context.setCurrentMapping(this);
		Object sourceValue;
		try {
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
