---
title: The AttributeMap interface
---
This document will cover the interface <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" pos="142:22:22" line-data="	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`AttributeMap`</SwmToken> in the Spring Web Flow project. We will cover:

1. What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" pos="142:22:22" line-data="	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`AttributeMap`</SwmToken>
2. Variables and functions in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" pos="142:22:22" line-data="	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`AttributeMap`</SwmToken>

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" pos="142:22:22" line-data="	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`AttributeMap`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" pos="142:22:22" line-data="	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`AttributeMap`</SwmToken> interface in <SwmPath>[spring-webflow/…/collection/AttributeMap.java](spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java)</SwmPath> is an immutable interface for accessing attributes in a backing map with string keys. It is used to manage and retrieve attributes in a type-safe manner within the Spring Web Flow framework.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="32">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="37:3:3" line-data="	V get(String attributeName);">`get`</SwmToken> retrieves an attribute value from the map, returning <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="33:25:25" line-data="	 * Get an attribute value out of this map, returning &lt;code&gt;null&lt;/code&gt; if not found.">`null`</SwmToken> if the attribute is not found.

```java
	/**
	 * Get an attribute value out of this map, returning <code>null</code> if not found.
	 * @param attributeName the attribute name
	 * @return the attribute value
	 */
	V get(String attributeName);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="39">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="40:7:7" line-data="	 * Returns the size of this map.">`size`</SwmToken> returns the number of entries in the map.

```java
	/**
	 * Returns the size of this map.
	 * @return the number of entries in the map
	 */
	int size();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="45">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="49:3:3" line-data="	boolean isEmpty();">`isEmpty`</SwmToken> checks if the attribute map is empty, returning `true` if it has a size of 0.

```java
	/**
	 * Is this attribute map empty with a size of 0?
	 * @return true if empty, false if not
	 */
	boolean isEmpty();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="51">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="56:3:3" line-data="	boolean contains(String attributeName);">`contains`</SwmToken> checks if an attribute with the provided name exists in the map.

```java
	/**
	 * Does the attribute with the provided name exist in this map?
	 * @param attributeName the attribute name
	 * @return true if so, false otherwise
	 */
	boolean contains(String attributeName);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="58">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="65:3:3" line-data="	boolean contains(String attributeName, Class&lt;? extends V&gt; requiredType) throws IllegalArgumentException;">`contains`</SwmToken> checks if an attribute with the provided name exists in the map and if its value is of the specified required type.

```java
	/**
	 * Does the attribute with the provided name exist in this map and is its value of the specified required type?
	 * @param attributeName the attribute name
	 * @param requiredType the required class of the attribute value
	 * @return true if so, false otherwise
	 * @throws IllegalArgumentException when the value is not of the required type
	 */
	boolean contains(String attributeName, Class<? extends V> requiredType) throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="67">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="73:3:3" line-data="	V get(String attributeName, V defaultValue);">`get`</SwmToken> retrieves an attribute value, returning the default value if no value is found.

```java
	/**
	 * Get an attribute value, returning the default value if no value is found.
	 * @param attributeName the name of the attribute
	 * @param defaultValue the default value
	 * @return the attribute value, falling back to the default if no such attribute exists
	 */
	V get(String attributeName, V defaultValue);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="75">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="82:11:11" line-data="	&lt;T extends V&gt; T get(String attributeName, Class&lt;T&gt; requiredType) throws IllegalArgumentException;">`get`</SwmToken> retrieves an attribute value, asserting the value is of the required type.

```java
	/**
	 * Get an attribute value, asserting the value is of the required type.
	 * @param attributeName the name of the attribute
	 * @param requiredType the required type of the attribute value
	 * @return the attribute value, or null if not found
	 * @throws IllegalArgumentException when the value is not of the required type
	 */
	<T extends V> T get(String attributeName, Class<T> requiredType) throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="84">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="92:11:11" line-data="	&lt;T extends V&gt; T get(String attributeName, Class&lt;T&gt; requiredType, T defaultValue)">`get`</SwmToken> retrieves an attribute value, asserting the value is of the required type and returning the default value if not found.

```java
	/**
	 * Get an attribute value, asserting the value is of the required type and returning the default value if not found.
	 * @param attributeName the name of the attribute
	 * @param requiredType the value required type
	 * @param defaultValue the default value
	 * @return the attribute value, or the default if not found
	 * @throws IllegalArgumentException when the value (if found) is not of the required type
	 */
	<T extends V> T get(String attributeName, Class<T> requiredType, T defaultValue)
			throws IllegalStateException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="95">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="101:3:3" line-data="	V getRequired(String attributeName) throws IllegalArgumentException;">`getRequired`</SwmToken> retrieves the value of a required attribute, throwing an exception if no attribute is found.

```java
	/**
	 * Get the value of a required attribute, throwing an exception of no attribute is found.
	 * @param attributeName the name of the attribute
	 * @return the attribute value
	 * @throws IllegalArgumentException when the attribute is not found
	 */
	V getRequired(String attributeName) throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="103">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="110:11:11" line-data="	&lt;T extends V&gt; T getRequired(String attributeName, Class&lt;T&gt; requiredType) throws IllegalArgumentException;">`getRequired`</SwmToken> retrieves the value of a required attribute and ensures it is of the required type.

```java
	/**
	 * Get the value of a required attribute and make sure it is of the required type.
	 * @param attributeName name of the attribute to get
	 * @param requiredType the required type of the attribute value
	 * @return the attribute value
	 * @throws IllegalArgumentException when the attribute is not found or not of the required type
	 */
	<T extends V> T getRequired(String attributeName, Class<T> requiredType) throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="112">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="118:3:3" line-data="	String getString(String attributeName) throws IllegalArgumentException;">`getString`</SwmToken> returns a string attribute value in the map, returning <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="113:25:25" line-data="	 * Returns a string attribute value in the map, returning &lt;code&gt;null&lt;/code&gt; if no value was found.">`null`</SwmToken> if no value was found.

```java
	/**
	 * Returns a string attribute value in the map, returning <code>null</code> if no value was found.
	 * @param attributeName the attribute name
	 * @return the string attribute value
	 * @throws IllegalArgumentException if the attribute is present but not a string
	 */
	String getString(String attributeName) throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="120">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="127:3:3" line-data="	String getString(String attributeName, String defaultValue) throws IllegalArgumentException;">`getString`</SwmToken> returns a string attribute value in the map, returning the default value if no value was found.

```java
	/**
	 * Returns a string attribute value in the map, returning the default value if no value was found.
	 * @param attributeName the attribute name
	 * @param defaultValue the default
	 * @return the string attribute value
	 * @throws IllegalArgumentException if the attribute is present but not a string
	 */
	String getString(String attributeName, String defaultValue) throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="129">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="136:3:3" line-data="	String getRequiredString(String attributeName) throws IllegalArgumentException;">`getRequiredString`</SwmToken> returns a string attribute value in the map, throwing an exception if the attribute is not present and of the correct type.

```java
	/**
	 * Returns a string attribute value in the map, throwing an exception if the attribute is not present and of the
	 * correct type.
	 * @param attributeName the attribute name
	 * @return the string attribute value
	 * @throws IllegalArgumentException if the attribute is not present or present but not a string
	 */
	String getRequiredString(String attributeName) throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="138">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="144:6:6" line-data="	Collection&lt;V&gt; getCollection(String attributeName) throws IllegalArgumentException;">`getCollection`</SwmToken> returns a collection attribute value in the map.

```java
	/**
	 * Returns a collection attribute value in the map.
	 * @param attributeName the attribute name
	 * @return the collection attribute value
	 * @throws IllegalArgumentException if the attribute is present but not a collection
	 */
	Collection<V> getCollection(String attributeName) throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="146">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="153:13:13" line-data="	&lt;T extends Collection&lt;V&gt;&gt; T getCollection(String attributeName, Class&lt;T&gt; requiredType)">`getCollection`</SwmToken> returns a collection attribute value in the map and ensures it is of the required type.

```java
	/**
	 * Returns a collection attribute value in the map and make sure it is of the required type.
	 * @param attributeName the attribute name
	 * @param requiredType the required type of the attribute value
	 * @return the collection attribute value
	 * @throws IllegalArgumentException if the attribute is present but not a collection of the required type
	 */
	<T extends Collection<V>> T getCollection(String attributeName, Class<T> requiredType)
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="156">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="163:6:6" line-data="	Collection&lt;V&gt; getRequiredCollection(String attributeName) throws IllegalArgumentException;">`getRequiredCollection`</SwmToken> returns a collection attribute value in the map, throwing an exception if the attribute is not present or not a collection.

```java
	/**
	 * Returns a collection attribute value in the map, throwing an exception if the attribute is not present or not a
	 * collection.
	 * @param attributeName the attribute name
	 * @return the collection attribute value
	 * @throws IllegalArgumentException if the attribute is not present or is present but not a collection
	 */
	Collection<V> getRequiredCollection(String attributeName) throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="165">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="174:13:13" line-data="	&lt;T extends Collection&lt;V&gt;&gt; T getRequiredCollection(String attributeName, Class&lt;T&gt; requiredType)">`getRequiredCollection`</SwmToken> returns a collection attribute value in the map, throwing an exception if the attribute is not present or not a collection of the required type.

```java
	/**
	 * Returns a collection attribute value in the map, throwing an exception if the attribute is not present or not a
	 * collection of the required type.
	 * @param attributeName the attribute name
	 * @param requiredType the required collection type
	 * @return the collection attribute value
	 * @throws IllegalArgumentException if the attribute is not present or is present but not a collection of the
	 * required type
	 */
	<T extends Collection<V>> T getRequiredCollection(String attributeName, Class<T> requiredType)
			throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="177">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="184:13:13" line-data="	&lt;T extends V&gt; T[] getArray(String attributeName, Class&lt;? extends T[]&gt; requiredType)">`getArray`</SwmToken> returns an array attribute value in the map and ensures it is of the required type.

```java
	/**
	 * Returns an array attribute value in the map and makes sure it is of the required type.
	 * @param attributeName the attribute name
	 * @param requiredType the required type of the attribute value
	 * @return the array attribute value
	 * @throws IllegalArgumentException if the attribute is present but not an array of the required type
	 */
	<T extends V> T[] getArray(String attributeName, Class<? extends T[]> requiredType)
			throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="187">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="196:13:13" line-data="	&lt;T extends V&gt; T[] getRequiredArray(String attributeName, Class&lt;? extends T[]&gt; requiredType)">`getRequiredArray`</SwmToken> returns an array attribute value in the map, throwing an exception if the attribute is not present or not an array of the required type.

```java
	/**
	 * Returns an array attribute value in the map, throwing an exception if the attribute is not present or not an
	 * array of the required type.
	 * @param attributeName the attribute name
	 * @param requiredType the required array type
	 * @return the collection attribute value
	 * @throws IllegalArgumentException if the attribute is not present or is present but not a array of the required
	 * type
	 */
	<T extends V> T[] getRequiredArray(String attributeName, Class<? extends T[]> requiredType)
			throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="199">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="207:11:11" line-data="	&lt;T extends Number&gt; T getNumber(String attributeName, Class&lt;T&gt; requiredType) throws IllegalArgumentException;">`getNumber`</SwmToken> returns a number attribute value in the map that is of the specified type, returning <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="200:37:37" line-data="	 * Returns a number attribute value in the map that is of the specified type, returning &lt;code&gt;null&lt;/code&gt; if no">`null`</SwmToken> if no value was found.

```java
	/**
	 * Returns a number attribute value in the map that is of the specified type, returning <code>null</code> if no
	 * value was found.
	 * @param attributeName the attribute name
	 * @param requiredType the required number type
	 * @return the number attribute value
	 * @throws IllegalArgumentException if the attribute is present but not a number of the required type
	 */
	<T extends Number> T getNumber(String attributeName, Class<T> requiredType) throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="209">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="217:11:11" line-data="	&lt;T extends Number&gt; T getNumber(String attributeName, Class&lt;T&gt; requiredType, T defaultValue)">`getNumber`</SwmToken> returns a number attribute value in the map of the specified type, returning the default value if no value was found.

```java
	/**
	 * Returns a number attribute value in the map of the specified type, returning the default value if no value was
	 * found.
	 * @param attributeName the attribute name
	 * @param defaultValue the default
	 * @return the number attribute value
	 * @throws IllegalArgumentException if the attribute is present but not a number of the required type
	 */
	<T extends Number> T getNumber(String attributeName, Class<T> requiredType, T defaultValue)
			throws IllegalArgumentException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" line="220">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/AttributeMap.java" pos="227:11:11" line-data="	&lt;T extends Number&gt; T getRequiredNumber(String attributeName, Class&lt;T&gt; requiredType)">`getRequiredNumber`</SwmToken> returns a number attribute value in the map, throwing an exception if the attribute is not present and of the correct type.

```java
	/**
	 * Returns a number attribute value in the map, throwing an exception if the attribute is not present and of the
	 * correct type.
	 * @param attributeName the attribute name
	 * @return the number attribute value
	 * @throws IllegalArgumentException if the attribute is not present or present but not a number of the required type
	 */
	<T extends Number> T getRequiredNumber(String attributeName, Class<T> requiredType)
			throws IllegalArgumentException;
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" line="142">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" pos="75:4:4" line-data="public class JpaFlowExecutionListener implements FlowExecutionListener {">`JpaFlowExecutionListener`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" pos="142:22:22" line-data="	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`AttributeMap`</SwmToken> is used in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" pos="142:5:5" line-data="	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`sessionEnded`</SwmToken> method to handle the output attributes when a session ends.

```java
	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap<?> output) {
		if (isParentPersistenceContext(session)) {
			if (!isPersistenceContext(session.getDefinition())) {
				bind(getEntityManager(session.getParent()));
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/persistence/HibernateFlowExecutionListener.java" line="156">

---

Similarly, in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/HibernateFlowExecutionListener.java" pos="75:4:4" line-data="public class HibernateFlowExecutionListener implements FlowExecutionListener {">`HibernateFlowExecutionListener`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/HibernateFlowExecutionListener.java" pos="156:22:22" line-data="	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`AttributeMap`</SwmToken> is used in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/HibernateFlowExecutionListener.java" pos="156:5:5" line-data="	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`sessionEnded`</SwmToken> method to manage the output attributes when a session concludes.

```java
	public void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap<?> output) {
		if (isParentPersistenceContext(session)) {
			if (!isPersistenceContext(session.getDefinition())) {
				bind(getHibernateSession(session.getParent()));
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionResource.java" line="36">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionResource.java" pos="44:3:3" line-data="	public FlowDefinitionResource(String flowId, Resource path, AttributeMap&lt;Object&gt; attributes) {">`FlowDefinitionResource`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionResource.java" pos="36:3:3" line-data="	private AttributeMap&lt;Object&gt; attributes;">`AttributeMap`</SwmToken> is used to store <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionResource.java" pos="42:8:10" line-data="	 * @param attributes meta-attributes describing the flow resource">`meta-attributes`</SwmToken> describing the flow resource. It is initialized in the constructor and accessed via the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="209:14:14" line-data="		AttributeMap&lt;Object&gt; flowAttributes = getFlowAttributes(location.getAttributes());">`getAttributes`</SwmToken> method.

```java
	private AttributeMap<Object> attributes;

	/**
	 * Creates a new flow definition resource
	 * @param flowId the flow id
	 * @param path the location of the resource
	 * @param attributes meta-attributes describing the flow resource
	 */
	public FlowDefinitionResource(String flowId, Resource path, AttributeMap<Object> attributes) {
		this.id = flowId;
		this.path = path;
		this.attributes = attributes;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" line="208">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="57:2:2" line-data="class FlowRegistryFactoryBean implements FactoryBean&lt;FlowDefinitionRegistry&gt;, BeanClassLoaderAware, InitializingBean,">`FlowRegistryFactoryBean`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="209:1:1" line-data="		AttributeMap&lt;Object&gt; flowAttributes = getFlowAttributes(location.getAttributes());">`AttributeMap`</SwmToken> is used to manage flow attributes. It is utilized in methods like <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="208:5:5" line-data="	private FlowDefinitionResource createResource(FlowLocation location) {">`createResource`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="209:10:10" line-data="		AttributeMap&lt;Object&gt; flowAttributes = getFlowAttributes(location.getAttributes());">`getFlowAttributes`</SwmToken> to handle attributes related to flow definitions.

```java
	private FlowDefinitionResource createResource(FlowLocation location) {
		AttributeMap<Object> flowAttributes = getFlowAttributes(location.getAttributes());
		return flowResourceFactory.createResource(location.getPath(), flowAttributes, location.getId());
	}

	private AttributeMap<Object> getFlowAttributes(Set<FlowElementAttribute> attributes) {
		MutableAttributeMap<Object> flowAttributes = null;
		if (flowBuilderServices.getDevelopment()) {
			flowAttributes = new LocalAttributeMap<>(1 + attributes.size(), 1);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/ActionExecutionException.java" line="39">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/ActionExecutionException.java" pos="39:3:3" line-data="	public ActionExecutionException(String flowId, String stateId, Action action,">`ActionExecutionException`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/ActionExecutionException.java" pos="40:1:1" line-data="			AttributeMap&lt;Object&gt; executionAttributes, Throwable cause) {">`AttributeMap`</SwmToken> is used to store execution attributes related to an action. It is passed as a parameter in the constructor.

```java
	public ActionExecutionException(String flowId, String stateId, Action action,
			AttributeMap<Object> executionAttributes, Throwable cause) {
		super(flowId, stateId, "Exception thrown executing " + action + " in state '" + stateId + "' of flow '"
				+ flowId + "' -- action execution attributes were '" + executionAttributes + "'", cause);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/action/AbstractAction.java" line="170">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/AbstractAction.java" pos="40:6:6" line-data="public abstract class AbstractAction implements Action, InitializingBean {">`AbstractAction`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/AbstractAction.java" pos="170:12:12" line-data="	protected Event result(String eventId, AttributeMap&lt;Object&gt; resultAttributes) {">`AttributeMap`</SwmToken> is used in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/AbstractAction.java" pos="170:5:5" line-data="	protected Event result(String eventId, AttributeMap&lt;Object&gt; resultAttributes) {">`result`</SwmToken> method to handle event attributes when creating an action result event.

```java
	protected Event result(String eventId, AttributeMap<Object> resultAttributes) {
		return getEventFactorySupport().event(this, eventId, resultAttributes);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/SubflowAttributeMapper.java" line="40">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/SubflowAttributeMapper.java" pos="26:4:4" line-data="public interface SubflowAttributeMapper {">`SubflowAttributeMapper`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/SubflowAttributeMapper.java" pos="40:5:5" line-data="	void mapSubflowOutput(AttributeMap&lt;?&gt; output, RequestContext context);">`AttributeMap`</SwmToken> is used in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/SubflowAttributeMapper.java" pos="40:3:3" line-data="	void mapSubflowOutput(AttributeMap&lt;?&gt; output, RequestContext context);">`mapSubflowOutput`</SwmToken> method to map output attributes returned by an ended subflow.

```java
	void mapSubflowOutput(AttributeMap<?> output, RequestContext context);
}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/action/EventFactorySupport.java" line="242">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/AbstractAction.java" pos="51:3:3" line-data="	public EventFactorySupport getEventFactorySupport() {">`EventFactorySupport`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/EventFactorySupport.java" pos="242:17:17" line-data="	public Event event(Object source, String eventId, AttributeMap&lt;Object&gt; attributes) {">`AttributeMap`</SwmToken> is used in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/EventFactorySupport.java" pos="242:5:5" line-data="	public Event event(Object source, String eventId, AttributeMap&lt;Object&gt; attributes) {">`event`</SwmToken> method to create an event with the specified attributes.

```java
	public Event event(Object source, String eventId, AttributeMap<Object> attributes) {
		return new Event(source, eventId, attributes);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/FlowExecutionListener.java" line="185">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" pos="31:10:10" line-data="import org.springframework.webflow.execution.FlowExecutionListener;">`FlowExecutionListener`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/FlowExecutionListener.java" pos="185:22:22" line-data="	default void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`AttributeMap`</SwmToken> is used in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/FlowExecutionListener.java" pos="185:5:5" line-data="	default void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap&lt;?&gt; output) {">`sessionEnded`</SwmToken> method to handle the output attributes when a session ends.

```java
	default void sessionEnded(RequestContext context, FlowSession session, String outcome, AttributeMap<?> output) {
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/FlowExecutionContext.java" line="119">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/FlowExecutionContext.java" pos="42:4:4" line-data="public interface FlowExecutionContext {">`FlowExecutionContext`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/FlowExecutionContext.java" pos="119:1:1" line-data="	AttributeMap&lt;Object&gt; getAttributes();">`AttributeMap`</SwmToken> is used to retrieve execution attributes.

```java
	AttributeMap<Object> getAttributes();
}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorFactoryBean.java" line="212">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorFactoryBean.java" pos="56:2:2" line-data="class FlowExecutorFactoryBean implements FactoryBean&lt;FlowExecutor&gt;, BeanClassLoaderAware, InitializingBean {">`FlowExecutorFactoryBean`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorFactoryBean.java" pos="212:7:7" line-data="	private FlowExecutionImplFactory createFlowExecutionFactory(AttributeMap&lt;Object&gt; executionAttributes) {">`AttributeMap`</SwmToken> is used in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorFactoryBean.java" pos="212:5:5" line-data="	private FlowExecutionImplFactory createFlowExecutionFactory(AttributeMap&lt;Object&gt; executionAttributes) {">`createFlowExecutionFactory`</SwmToken> method to set execution attributes for the flow execution factory.

```java
	private FlowExecutionImplFactory createFlowExecutionFactory(AttributeMap<Object> executionAttributes) {
		FlowExecutionImplFactory executionFactory = new FlowExecutionImplFactory();
		executionFactory.setExecutionAttributes(executionAttributes);
		if (flowExecutionListenerLoader != null) {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/Event.java" line="72">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/Event.java" pos="72:3:3" line-data="	public Event(Object source, String id, AttributeMap&lt;Object&gt; attributes) {">`Event`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/Event.java" pos="72:15:15" line-data="	public Event(Object source, String id, AttributeMap&lt;Object&gt; attributes) {">`AttributeMap`</SwmToken> is used to store additional event attributes that form the event's payload. It is initialized in the constructor and accessed via the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/Event.java" pos="100:8:8" line-data="	public AttributeMap&lt;Object&gt; getAttributes() {">`getAttributes`</SwmToken> method.

```java
	public Event(Object source, String id, AttributeMap<Object> attributes) {
		super(source);
		Assert.hasText(id, "The event id is required: please set this event's id to a non-blank string identifier");
		this.id = id;
		this.attributes = attributes != null ? attributes : CollectionUtils.EMPTY_ATTRIBUTE_MAP;
	}

	/**
	 * Returns the event identifier.
	 * @return the event id
	 */
	public String getId() {
		return id;
	}

	/**
	 * Returns the time at which the event occurred, represented as the number of milliseconds since January 1, 1970,
	 * 00:00:00 GMT.
	 * @return the timestamp
	 */
	public long getTimestamp() {
		return timestamp;
	}

	/**
	 * Returns an unmodifiable map storing the attributes of this event. Never returns <code>null</code>.
	 * @return the event attributes (payload)
	 */
	public AttributeMap<Object> getAttributes() {
		return attributes;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/FlowExecutionOutcome.java" line="38">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/FlowExecutionOutcome.java" pos="38:3:3" line-data="	public FlowExecutionOutcome(String id, AttributeMap&lt;Object&gt; output) {">`FlowExecutionOutcome`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/FlowExecutionOutcome.java" pos="38:10:10" line-data="	public FlowExecutionOutcome(String id, AttributeMap&lt;Object&gt; output) {">`AttributeMap`</SwmToken> is used to store the output returned by the execution. It is initialized in the constructor.

```java
	public FlowExecutionOutcome(String id, AttributeMap<Object> output) {
		super();
		this.id = id;
		this.output = (output != null ? output : CollectionUtils.EMPTY_ATTRIBUTE_MAP);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
