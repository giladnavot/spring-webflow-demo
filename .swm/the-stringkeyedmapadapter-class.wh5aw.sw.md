---
title: The StringKeyedMapAdapter class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletContextMap.java" pos="31:8:8" line-data="public class HttpServletContextMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`StringKeyedMapAdapter`</SwmToken> in the Spring Web Flow project. We will discuss:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletContextMap.java" pos="31:8:8" line-data="public class HttpServletContextMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`StringKeyedMapAdapter`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletContextMap.java" pos="31:8:8" line-data="public class HttpServletContextMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`StringKeyedMapAdapter`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletContextMap.java" pos="31:8:8" line-data="public class HttpServletContextMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`StringKeyedMapAdapter`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletContextMap.java" pos="31:8:8" line-data="public class HttpServletContextMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`StringKeyedMapAdapter`</SwmToken> is an abstract base class for map adapters whose keys are String values. It is used to provide a common implementation for maps that use String keys, requiring concrete subclasses to implement specific hook methods for getting, setting, and removing attributes, as well as retrieving attribute names.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="40">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="40:5:5" line-data="	public void clear() {">`clear`</SwmToken> removes all <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="122:28:30" line-data="	 * Hook method that needs to be implemented by concrete subclasses. Puts a key-value pair in the map, overwriting">`key-value`</SwmToken> pairs from the map by iterating over the attribute names and removing each attribute.

```java
	public void clear() {
		for (Iterator<String> it = getAttributeNames(); it.hasNext();) {
			removeAttribute(it.next());
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="46">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="46:5:5" line-data="	public boolean containsKey(Object key) {">`containsKey`</SwmToken> checks if a given key is present in the map by verifying if the attribute associated with the key is not null.

```java
	public boolean containsKey(Object key) {
		return getAttribute(key.toString()) != null;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="50">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="50:5:5" line-data="	public boolean containsValue(Object value) {">`containsValue`</SwmToken> checks if a given value is present in the map by iterating over the attribute names and comparing each attribute's value to the given value.

```java
	public boolean containsValue(Object value) {
		if (value == null) {
			return false;
		}
		for (Iterator<String> it = getAttributeNames(); it.hasNext();) {
			Object aValue = getAttribute(it.next());
			if (value.equals(aValue)) {
				return true;
			}
		}
		return false;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="63">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="63:13:13" line-data="	public Set&lt;Entry&lt;String, V&gt;&gt; entrySet() {">`entrySet`</SwmToken> returns a set view of the mappings contained in the map. It initializes the entry set if it is null.

```java
	public Set<Entry<String, V>> entrySet() {
		return (entrySet != null) ? entrySet : (entrySet = new EntrySet());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="67">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="67:5:5" line-data="	public V get(Object key) {">`get`</SwmToken> retrieves the value associated with a given key by calling the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="68:3:3" line-data="		return getAttribute(key.toString());">`getAttribute`</SwmToken> method.

```java
	public V get(Object key) {
		return getAttribute(key.toString());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="71">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="71:5:5" line-data="	public boolean isEmpty() {">`isEmpty`</SwmToken> checks if the map is empty by verifying if there are no attribute names.

```java
	public boolean isEmpty() {
		return !getAttributeNames().hasNext();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="75">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="75:8:8" line-data="	public Set&lt;String&gt; keySet() {">`keySet`</SwmToken> returns a set view of the keys contained in the map. It initializes the key set if it is null.

```java
	public Set<String> keySet() {
		return (keySet != null) ? keySet : (keySet = new KeySet());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="79">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="79:5:5" line-data="	public V put(String key, V value) {">`put`</SwmToken> associates a given value with a given key in the map, returning the previous value associated with the key, if any.

```java
	public V put(String key, V value) {
		String stringKey = String.valueOf(key);
		V previousValue = getAttribute(stringKey);
		setAttribute(stringKey, value);
		return previousValue;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="86">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="86:5:5" line-data="	public void putAll(Map&lt;? extends String, ? extends V&gt; map) {">`putAll`</SwmToken> copies all of the mappings from the specified map to this map.

```java
	public void putAll(Map<? extends String, ? extends V> map) {
		for (Entry<? extends String, ? extends V> entry : map.entrySet()) {
			setAttribute(entry.getKey(), entry.getValue());
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="92">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="92:5:5" line-data="	public V remove(Object key) {">`remove`</SwmToken> removes the mapping for a key from this map if it is present, returning the value associated with the key.

```java
	public V remove(Object key) {
		String stringKey = key.toString();
		V retval = getAttribute(stringKey);
		removeAttribute(stringKey);
		return retval;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="99">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="99:5:5" line-data="	public int size() {">`size`</SwmToken> returns the number of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="122:28:30" line-data="	 * Hook method that needs to be implemented by concrete subclasses. Puts a key-value pair in the map, overwriting">`key-value`</SwmToken> mappings in the map by iterating over the attribute names.

```java
	public int size() {
		int size = 0;
		for (Iterator<String> it = getAttributeNames(); it.hasNext();) {
			size++;
			it.next();
		}
		return size;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="108">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="108:8:8" line-data="	public Collection&lt;V&gt; values() {">`values`</SwmToken> returns a collection view of the values contained in the map. It initializes the values collection if it is null.

```java
	public Collection<V> values() {
		return (values != null) ? values : (values = new Values());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="119">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="119:7:7" line-data="	protected abstract V getAttribute(String key);">`getAttribute`</SwmToken> is an abstract method that needs to be implemented by concrete subclasses to get a value associated with a key.

```java
	protected abstract V getAttribute(String key);

	/**
	 * Hook method that needs to be implemented by concrete subclasses. Puts a key-value pair in the map, overwriting
	 * any possible earlier value associated with the same key.
	 * @param key the key to associate the value with
	 * @param value the value to associate with the key
	 */
	protected abstract void setAttribute(String key, V value);

	/**
	 * Hook method that needs to be implemented by concrete subclasses. Removes a key and its associated value from the
	 * map.
	 * @param key the key to remove
	 */
	protected abstract void removeAttribute(String key);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="121">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="82:1:1" line-data="		setAttribute(stringKey, value);">`setAttribute`</SwmToken> is an abstract method that needs to be implemented by concrete subclasses to put a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="122:28:30" line-data="	 * Hook method that needs to be implemented by concrete subclasses. Puts a key-value pair in the map, overwriting">`key-value`</SwmToken> pair in the map.

```java
	/**
	 * Hook method that needs to be implemented by concrete subclasses. Puts a key-value pair in the map, overwriting
	 * any possible earlier value associated with the same key.
	 * @param key the key to associate the value with
	 * @param value the value to associate with the key
	 */
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="129">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="42:1:1" line-data="			removeAttribute(it.next());">`removeAttribute`</SwmToken> is an abstract method that needs to be implemented by concrete subclasses to remove a key and its associated value from the map.

```java
	/**
	 * Hook method that needs to be implemented by concrete subclasses. Removes a key and its associated value from the
	 * map.
	 * @param key the key to remove
	 */
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" line="136">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/StringKeyedMapAdapter.java" pos="41:13:13" line-data="		for (Iterator&lt;String&gt; it = getAttributeNames(); it.hasNext();) {">`getAttributeNames`</SwmToken> is an abstract method that needs to be implemented by concrete subclasses to return an enumeration listing all keys known to the map.

```java
	/**
	 * Hook method that needs to be implemented by concrete subclasses. Returns an enumeration listing all keys known to
	 * the map.
	 * @return the key enumeration
	 */
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletContextMap.java" line="31">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletContextMap.java" pos="31:4:4" line-data="public class HttpServletContextMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`HttpServletContextMap`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletContextMap.java" pos="31:8:11" line-data="public class HttpServletContextMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`StringKeyedMapAdapter<Object>`</SwmToken> and implements <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletContextMap.java" pos="31:15:21" line-data="public class HttpServletContextMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`SharedMap<String, Object>`</SwmToken>. It is used to wrap the servlet context, providing a map-like interface to interact with servlet context attributes.

```java
public class HttpServletContextMap extends StringKeyedMapAdapter<Object> implements SharedMap<String, Object> {

	/**
	 * The wrapped servlet context.
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletRequestMap.java" line="30">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletRequestMap.java" pos="30:4:4" line-data="public class HttpServletRequestMap extends StringKeyedMapAdapter&lt;Object&gt; {">`HttpServletRequestMap`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletRequestMap.java" pos="30:8:11" line-data="public class HttpServletRequestMap extends StringKeyedMapAdapter&lt;Object&gt; {">`StringKeyedMapAdapter<Object>`</SwmToken>. It is used to wrap the HTTP request, allowing access to request attributes through a map-like interface.

```java
public class HttpServletRequestMap extends StringKeyedMapAdapter<Object> {

	/**
	 * The wrapped HTTP request.
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpSessionMap.java" line="35">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpSessionMap.java" pos="35:4:4" line-data="public class HttpSessionMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`HttpSessionMap`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpSessionMap.java" pos="35:8:11" line-data="public class HttpSessionMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`StringKeyedMapAdapter<Object>`</SwmToken> and implements <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpSessionMap.java" pos="35:15:21" line-data="public class HttpSessionMap extends StringKeyedMapAdapter&lt;Object&gt; implements SharedMap&lt;String, Object&gt; {">`SharedMap<String, Object>`</SwmToken>. It wraps the HTTP session, providing a map-like interface to interact with session attributes.

```java
public class HttpSessionMap extends StringKeyedMapAdapter<Object> implements SharedMap<String, Object> {

	/**
	 * The wrapped HTTP request, providing access to the session.
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletRequestParameterMap.java" line="36">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletRequestParameterMap.java" pos="36:4:4" line-data="public class HttpServletRequestParameterMap extends StringKeyedMapAdapter&lt;Object&gt; {">`HttpServletRequestParameterMap`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/HttpServletRequestParameterMap.java" pos="36:8:11" line-data="public class HttpServletRequestParameterMap extends StringKeyedMapAdapter&lt;Object&gt; {">`StringKeyedMapAdapter<Object>`</SwmToken>. It is used to wrap the HTTP request parameters, allowing access to request parameters through a map-like interface.

```java
public class HttpServletRequestParameterMap extends StringKeyedMapAdapter<Object> {

	/**
	 * The wrapped HTTP request.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
