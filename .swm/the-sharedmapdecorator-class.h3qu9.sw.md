---
title: The SharedMapDecorator class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="42:3:3" line-data="	public SharedMapDecorator(Map&lt;K, V&gt; map) {">`SharedMapDecorator`</SwmToken> in the Spring Web Flow project. We will discuss:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="42:3:3" line-data="	public SharedMapDecorator(Map&lt;K, V&gt; map) {">`SharedMapDecorator`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="42:3:3" line-data="	public SharedMapDecorator(Map&lt;K, V&gt; map) {">`SharedMapDecorator`</SwmToken>.

## What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="42:3:3" line-data="	public SharedMapDecorator(Map&lt;K, V&gt; map) {">`SharedMapDecorator`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="42:3:3" line-data="	public SharedMapDecorator(Map&lt;K, V&gt; map) {">`SharedMapDecorator`</SwmToken> class is a map decorator that implements the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="26:16:16" line-data=" * A map decorator that implements &lt;code&gt;SharedMap&lt;/code&gt;. By default, simply returns the map itself as the mutex.">`SharedMap`</SwmToken> interface. It is designed to wrap a target map and provide synchronization for multiple threads. By default, it returns the map itself as the mutex, but subclasses can override this behavior to return a different mutex object.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="38">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="42:3:3" line-data="	public SharedMapDecorator(Map&lt;K, V&gt; map) {">`SharedMapDecorator`</SwmToken> constructor initializes the decorator with the provided map, which is shared by multiple threads.

```java
	/**
	 * Creates a new shared map decorator.
	 * @param map the map that is shared by multiple threads, to be synced
	 */
	public SharedMapDecorator(Map<K, V> map) {
		this.map = map;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="48">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="48:5:5" line-data="	public void clear() {">`clear`</SwmToken> function clears all entries in the wrapped map.

```java
	public void clear() {
		map.clear();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="52">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="52:5:5" line-data="	public boolean containsKey(Object key) {">`containsKey`</SwmToken> function checks if the wrapped map contains a specific key.

```java
	public boolean containsKey(Object key) {
		return map.containsKey(key);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="56">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="56:5:5" line-data="	public boolean containsValue(Object value) {">`containsValue`</SwmToken> function checks if the wrapped map contains a specific value.

```java
	public boolean containsValue(Object value) {
		return map.containsValue(value);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="60">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="60:13:13" line-data="	public Set&lt;Entry&lt;K, V&gt;&gt; entrySet() {">`entrySet`</SwmToken> function returns a set view of the entries contained in the wrapped map.

```java
	public Set<Entry<K, V>> entrySet() {
		return map.entrySet();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="64">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="64:5:5" line-data="	public V get(Object key) {">`get`</SwmToken> function retrieves the value associated with a specific key from the wrapped map.

```java
	public V get(Object key) {
		return map.get(key);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="68">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="68:5:5" line-data="	public boolean isEmpty() {">`isEmpty`</SwmToken> function checks if the wrapped map is empty.

```java
	public boolean isEmpty() {
		return map.isEmpty();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="72">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="72:8:8" line-data="	public Set&lt;K&gt; keySet() {">`keySet`</SwmToken> function returns a set view of the keys contained in the wrapped map.

```java
	public Set<K> keySet() {
		return map.keySet();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="76">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="76:5:5" line-data="	public V put(K key, V value) {">`put`</SwmToken> function associates a specific value with a specific key in the wrapped map.

```java
	public V put(K key, V value) {
		return map.put(key, value);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="80">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="80:5:5" line-data="	public void putAll(Map&lt;? extends K, ? extends V&gt; map) {">`putAll`</SwmToken> function copies all mappings from the specified map to the wrapped map.

```java
	public void putAll(Map<? extends K, ? extends V> map) {
		this.map.putAll(map);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="84">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="84:5:5" line-data="	public V remove(Object key) {">`remove`</SwmToken> function removes the mapping for a specific key from the wrapped map.

```java
	public V remove(Object key) {
		return map.remove(key);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="88">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="88:5:5" line-data="	public int size() {">`size`</SwmToken> function returns the number of key-value mappings in the wrapped map.

```java
	public int size() {
		return map.size();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="92">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="92:8:8" line-data="	public Collection&lt;V&gt; values() {">`values`</SwmToken> function returns a collection view of the values contained in the wrapped map.

```java
	public Collection<V> values() {
		return map.values();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="98">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="98:5:5" line-data="	public Object getMutex() {">`getMutex`</SwmToken> function returns the mutex object for the wrapped map, which is the map itself by default.

```java
	public Object getMutex() {
		return map;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="102">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="102:5:5" line-data="	public String toString() {">`toString`</SwmToken> function returns a string representation of the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="42:3:3" line-data="	public SharedMapDecorator(Map&lt;K, V&gt; map) {">`SharedMapDecorator`</SwmToken> object, including the map and mutex.

```java
	public String toString() {
		return new ToStringCreator(this).append("map", map).append("mutex", getMutex()).toString();
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
