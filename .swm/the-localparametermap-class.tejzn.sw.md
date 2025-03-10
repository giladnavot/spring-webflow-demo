---
title: The LocalParameterMap class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="69:3:3" line-data="	public LocalParameterMap(Map&lt;String, Object&gt; parameters) {">`LocalParameterMap`</SwmToken> in detail. We will discuss:

1. What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="69:3:3" line-data="	public LocalParameterMap(Map&lt;String, Object&gt; parameters) {">`LocalParameterMap`</SwmToken>
2. Variables and functions in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="69:3:3" line-data="	public LocalParameterMap(Map&lt;String, Object&gt; parameters) {">`LocalParameterMap`</SwmToken>

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="69:3:3" line-data="	public LocalParameterMap(Map&lt;String, Object&gt; parameters) {">`LocalParameterMap`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="69:3:3" line-data="	public LocalParameterMap(Map&lt;String, Object&gt; parameters) {">`LocalParameterMap`</SwmToken> class is an immutable parameter map that stores <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="38:13:15" line-data=" * An immutable parameter map storing String-keyed, String-valued parameters in a backing {@link Map} implementation.">`String-keyed`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="38:18:20" line-data=" * An immutable parameter map storing String-keyed, String-valued parameters in a backing {@link Map} implementation.">`String-valued`</SwmToken> parameters in a backing <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="69:5:5" line-data="	public LocalParameterMap(Map&lt;String, Object&gt; parameters) {">`Map`</SwmToken> implementation. It provides convenient operations for accessing parameters in a typed manner. This class is used to manage parameters in a web flow context, ensuring that parameters are accessed and converted correctly.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="62">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="69:3:3" line-data="	public LocalParameterMap(Map&lt;String, Object&gt; parameters) {">`LocalParameterMap`</SwmToken> initializes a new parameter map from the provided map. It expects that the contents of the backing map adhere to the parameter map contract, meaning map entries have string keys, string values, and remain unmodifiable.

```java
	/**
	 * Creates a new parameter map from the provided map.
	 * <p>
	 * It is expected that the contents of the backing map adhere to the parameter map contract; that is, map entries
	 * have string keys, string values, and remain unmodifiable.
	 * @param parameters the contents of this parameter map
	 */
	public LocalParameterMap(Map<String, Object> parameters) {
		this(parameters, DEFAULT_CONVERSION_SERVICE);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="73">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="81:3:3" line-data="	public LocalParameterMap(Map&lt;String, Object&gt; parameters, ConversionService conversionService) {">`LocalParameterMap`</SwmToken> initializes a new parameter map from the provided map and a helper for performing type conversion of map entry values.

```java
	/**
	 * Creates a new parameter map from the provided map.
	 * <p>
	 * It is expected that the contents of the backing map adhere to the parameter map contract; that is, map entries
	 * have string keys, string values, and remain unmodifiable.
	 * @param parameters the contents of this parameter map
	 * @param conversionService a helper for performing type conversion of map entry values
	 */
	public LocalParameterMap(Map<String, Object> parameters, ConversionService conversionService) {
		initParameters(parameters);
		this.conversionService = conversionService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="86">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="86:5:5" line-data="	public boolean equals(Object o) {">`equals`</SwmToken> checks if the given object is equal to the current <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="87:10:10" line-data="		if (!(o instanceof LocalParameterMap)) {">`LocalParameterMap`</SwmToken> instance by comparing the parameters.

```java
	public boolean equals(Object o) {
		if (!(o instanceof LocalParameterMap)) {
			return false;
		}
		LocalParameterMap other = (LocalParameterMap) o;
		return parameters.equals(other.parameters);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="94">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="94:5:5" line-data="	public int hashCode() {">`hashCode`</SwmToken> returns the hash code of the parameters map.

```java
	public int hashCode() {
		return parameters.hashCode();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="98">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="98:11:11" line-data="	public Map&lt;String, Object&gt; asMap() {">`asMap`</SwmToken> returns an unmodifiable view of the parameters map.

```java
	public Map<String, Object> asMap() {
		return Collections.unmodifiableMap(parameterAccessor.asMap());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="102">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="102:5:5" line-data="	public boolean isEmpty() {">`isEmpty`</SwmToken> checks if the parameters map is empty.

```java
	public boolean isEmpty() {
		return parameters.isEmpty();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="106">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="106:5:5" line-data="	public int size() {">`size`</SwmToken> returns the size of the parameters map.

```java
	public int size() {
		return parameters.size();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="110">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="110:5:5" line-data="	public boolean contains(String parameterName) {">`contains`</SwmToken> checks if the parameters map contains a specific parameter name.

```java
	public boolean contains(String parameterName) {
		return parameters.containsKey(parameterName);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="114">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="114:5:5" line-data="	public String get(String parameterName) {">`get`</SwmToken> retrieves the value of a parameter by its name.

```java
	public String get(String parameterName) {
		return get(parameterName, (String) null);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="118">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="118:5:5" line-data="	public String get(String parameterName, String defaultValue) {">`get`</SwmToken> retrieves the value of a parameter by its name, with a default value if the parameter is not found.

```java
	public String get(String parameterName, String defaultValue) {
		if (!parameters.containsKey(parameterName)) {
			return defaultValue;
		}
		Object value = parameters.get(parameterName);
		if (value.getClass().isArray()) {
			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);
			String[] array = (String[]) value;
			if (array.length == 0) {
				return null;
			} else {
				Object first = ((String[]) value)[0];
				parameterAccessor.assertKeyValueInstanceOf(parameterName, first, String.class);
				return (String) first;
			}

		} else {
			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String.class);
			return (String) value;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="140">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="140:7:7" line-data="	public String[] getArray(String parameterName) {">`getArray`</SwmToken> retrieves the array of values of a parameter by its name.

```java
	public String[] getArray(String parameterName) {
		if (!parameters.containsKey(parameterName)) {
			return null;
		}
		Object value = parameters.get(parameterName);
		if (value.getClass().isArray()) {
			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);
			return (String[]) value;
		} else {
			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String.class);
			return new String[] { (String) value };
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="154">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="154:11:11" line-data="	public &lt;T&gt; T[] getArray(String parameterName, Class&lt;T&gt; targetElementType) throws ConversionExecutionException {">`getArray`</SwmToken> retrieves the array of values of a parameter by its name, converting them to the specified target element type.

```java
	public <T> T[] getArray(String parameterName, Class<T> targetElementType) throws ConversionExecutionException {
		String[] parameters = getArray(parameterName);
		return parameters != null ? convert(parameters, targetElementType) : null;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="159">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="159:9:9" line-data="	public &lt;T&gt; T get(String parameterName, Class&lt;T&gt; targetType) throws ConversionExecutionException {">`get`</SwmToken> retrieves the value of a parameter by its name, converting it to the specified target type.

```java
	public <T> T get(String parameterName, Class<T> targetType) throws ConversionExecutionException {
		return get(parameterName, targetType, null);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="163">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="163:9:9" line-data="	public &lt;T&gt; T get(String parameterName, Class&lt;T&gt; targetType, T defaultValue) throws ConversionExecutionException {">`get`</SwmToken> retrieves the value of a parameter by its name, converting it to the specified target type, with a default value if the parameter is not found.

```java
	public <T> T get(String parameterName, Class<T> targetType, T defaultValue) throws ConversionExecutionException {
		if (defaultValue != null) {
			assertAssignableTo(targetType, defaultValue.getClass());
		}
		String parameter = get(parameterName);
		return parameter != null ? convert(parameter, targetType) : defaultValue;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="171">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="171:5:5" line-data="	public String getRequired(String parameterName) throws IllegalArgumentException {">`getRequired`</SwmToken> retrieves the value of a required parameter by its name.

```java
	public String getRequired(String parameterName) throws IllegalArgumentException {
		parameterAccessor.assertContainsKey(parameterName);
		return get(parameterName);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="176">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="176:7:7" line-data="	public String[] getRequiredArray(String parameterName) throws IllegalArgumentException {">`getRequiredArray`</SwmToken> retrieves the array of values of a required parameter by its name.

```java
	public String[] getRequiredArray(String parameterName) throws IllegalArgumentException {
		parameterAccessor.assertContainsKey(parameterName);
		return getArray(parameterName);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="181">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="181:11:11" line-data="	public &lt;T&gt; T[] getRequiredArray(String parameterName, Class&lt;T&gt; targetElementType) throws IllegalArgumentException,">`getRequiredArray`</SwmToken> retrieves the array of values of a required parameter by its name, converting them to the specified target element type.

```java
	public <T> T[] getRequiredArray(String parameterName, Class<T> targetElementType) throws IllegalArgumentException,
			ConversionExecutionException {
		String[] parameters = getRequiredArray(parameterName);
		return convert(parameters, targetElementType);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="187">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="187:9:9" line-data="	public &lt;T&gt; T getRequired(String parameterName, Class&lt;T&gt; targetType) throws IllegalArgumentException,">`getRequired`</SwmToken> retrieves the value of a required parameter by its name, converting it to the specified target type.

```java
	public <T> T getRequired(String parameterName, Class<T> targetType) throws IllegalArgumentException,
			ConversionExecutionException {
		return convert(getRequired(parameterName), targetType);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="192">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="192:13:13" line-data="	public &lt;T extends Number&gt; T getNumber(String parameterName, Class&lt;T&gt; targetType)">`getNumber`</SwmToken> retrieves the value of a parameter by its name, converting it to the specified number type.

```java
	public <T extends Number> T getNumber(String parameterName, Class<T> targetType)
			throws ConversionExecutionException {
		assertAssignableTo(Number.class, targetType);
		return get(parameterName, targetType);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="198">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="198:13:13" line-data="	public &lt;T extends Number&gt; T getNumber(String parameterName, Class&lt;T&gt; targetType, T defaultValue)">`getNumber`</SwmToken> retrieves the value of a parameter by its name, converting it to the specified number type, with a default value if the parameter is not found.

```java
	public <T extends Number> T getNumber(String parameterName, Class<T> targetType, T defaultValue)
			throws ConversionExecutionException {
		assertAssignableTo(Number.class, targetType);
		return get(parameterName, targetType, defaultValue);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="204">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="204:13:13" line-data="	public &lt;T extends Number&gt; T getRequiredNumber(String parameterName, Class&lt;T&gt; targetType)">`getRequiredNumber`</SwmToken> retrieves the value of a required parameter by its name, converting it to the specified number type.

```java
	public <T extends Number> T getRequiredNumber(String parameterName, Class<T> targetType)
			throws IllegalArgumentException, ConversionExecutionException {
		assertAssignableTo(Number.class, targetType);
		return getRequired(parameterName, targetType);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="210">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="210:5:5" line-data="	public Integer getInteger(String parameterName) throws ConversionExecutionException {">`getInteger`</SwmToken> retrieves the value of a parameter by its name, converting it to an Integer.

```java
	public Integer getInteger(String parameterName) throws ConversionExecutionException {
		return get(parameterName, Integer.class);
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="353">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="42:4:4" line-data="public class ServletExternalContext implements ExternalContext {">`ServletExternalContext`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="356:9:9" line-data="		this.requestParameterMap = new LocalParameterMap(new HttpServletRequestParameterMap(request));">`LocalParameterMap`</SwmToken> is instantiated with an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="356:13:13" line-data="		this.requestParameterMap = new LocalParameterMap(new HttpServletRequestParameterMap(request));">`HttpServletRequestParameterMap`</SwmToken> object. This usage indicates that <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="356:9:9" line-data="		this.requestParameterMap = new LocalParameterMap(new HttpServletRequestParameterMap(request));">`LocalParameterMap`</SwmToken> is being used to wrap and manage request parameters from an HTTP servlet request.

```java
		this.context = context;
		this.request = request;
		this.response = response;
		this.requestParameterMap = new LocalParameterMap(new HttpServletRequestParameterMap(request));
		this.requestMap = new LocalAttributeMap<>(new HttpServletRequestMap(request));
		this.sessionMap = new LocalSharedAttributeMap<>(new HttpSessionMap(request));
		this.applicationMap = new LocalSharedAttributeMap<>(new HttpServletContextMap(context));
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
