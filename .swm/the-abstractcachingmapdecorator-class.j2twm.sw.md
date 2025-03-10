---
title: The AbstractCachingMapDecorator class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="63:3:3" line-data="	public AbstractCachingMapDecorator() {">`AbstractCachingMapDecorator`</SwmToken> in detail. We will discuss:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="63:3:3" line-data="	public AbstractCachingMapDecorator() {">`AbstractCachingMapDecorator`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="63:3:3" line-data="	public AbstractCachingMapDecorator() {">`AbstractCachingMapDecorator`</SwmToken>.

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="63:3:3" line-data="	public AbstractCachingMapDecorator() {">`AbstractCachingMapDecorator`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="63:3:3" line-data="	public AbstractCachingMapDecorator() {">`AbstractCachingMapDecorator`</SwmToken> is an abstract class that serves as a decorator for a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="52:5:5" line-data="	private final Map&lt;K, Object&gt; targetMap;">`Map`</SwmToken>, encapsulating the workflow for caching expensive values in a target <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="52:5:5" line-data="	private final Map&lt;K, Object&gt; targetMap;">`Map`</SwmToken>. It supports caching with either weak or strong keys. This class is designed as an abstract template, and caching <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="52:5:5" line-data="	private final Map&lt;K, Object&gt; targetMap;">`Map`</SwmToken> implementations should subclass and override the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="39:14:17" line-data=" * subclass and override the &lt;code&gt;create(key)&lt;/code&gt; method which encapsulates">`create(key)`</SwmToken> method, which encapsulates the expensive creation of a new object.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="49">

---

The variable <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="49:7:7" line-data="	private static Object NULL_VALUE = new Object();">`NULL_VALUE`</SwmToken> is a static object used to represent <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="112:19:19" line-data="		Assert.notNull(targetMap, &quot;&#39;targetMap&#39; must not be null&quot;);">`null`</SwmToken> values within the map.

```java
	private static Object NULL_VALUE = new Object();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="52">

---

The variable <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="52:13:13" line-data="	private final Map&lt;K, Object&gt; targetMap;">`targetMap`</SwmToken> is a final <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="52:5:5" line-data="	private final Map&lt;K, Object&gt; targetMap;">`Map`</SwmToken> that holds the actual data of the decorated map.

```java
	private final Map<K, Object> targetMap;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="54">

---

The variable <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="54:7:7" line-data="	private final boolean synchronize;">`synchronize`</SwmToken> is a final boolean that indicates whether the map operations should be synchronized.

```java
	private final boolean synchronize;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="56">

---

The variable <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="56:7:7" line-data="	private final boolean weak;">`weak`</SwmToken> is a final boolean that indicates whether weak references should be used for keys and values.

```java
	private final boolean weak;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="63">

---

The constructor <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="63:3:5" line-data="	public AbstractCachingMapDecorator() {">`AbstractCachingMapDecorator()`</SwmToken> creates a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="60:7:7" line-data="	 * Create a CachingMapDecorator with strong keys,">`CachingMapDecorator`</SwmToken> with strong keys, using an underlying synchronized <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="52:5:5" line-data="	private final Map&lt;K, Object&gt; targetMap;">`Map`</SwmToken>.

```java
	public AbstractCachingMapDecorator() {
		this(false);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="72">

---

The constructor <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="72:3:8" line-data="	public AbstractCachingMapDecorator(boolean weak) {">`AbstractCachingMapDecorator(boolean weak)`</SwmToken> creates a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="60:7:7" line-data="	 * Create a CachingMapDecorator with strong keys,">`CachingMapDecorator`</SwmToken>, using an underlying synchronized <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="73:1:1" line-data="		Map&lt;K, Object&gt; internalMap = (weak ? new WeakHashMap&lt;&gt;() : new HashMap&lt;&gt;());">`Map`</SwmToken>. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="72:7:7" line-data="	public AbstractCachingMapDecorator(boolean weak) {">`weak`</SwmToken> parameter determines whether to use weak references for keys and values.

```java
	public AbstractCachingMapDecorator(boolean weak) {
		Map<K, Object> internalMap = (weak ? new WeakHashMap<>() : new HashMap<>());
		this.targetMap = Collections.synchronizedMap(internalMap);
		this.synchronize = true;
		this.weak = weak;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="85">

---

The constructor <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="85:3:13" line-data="	public AbstractCachingMapDecorator(boolean weak, int size) {">`AbstractCachingMapDecorator(boolean weak, int size)`</SwmToken> creates a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="60:7:7" line-data="	 * Create a CachingMapDecorator with strong keys,">`CachingMapDecorator`</SwmToken> with an initial size, using an underlying synchronized <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="86:1:1" line-data="		Map&lt;K, Object&gt; internalMap = weak ? new WeakHashMap&lt;&gt;(size) : new HashMap&lt;&gt;(size);">`Map`</SwmToken>. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="85:7:7" line-data="	public AbstractCachingMapDecorator(boolean weak, int size) {">`weak`</SwmToken> parameter determines whether to use weak references for keys and values, and the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="85:12:12" line-data="	public AbstractCachingMapDecorator(boolean weak, int size) {">`size`</SwmToken> parameter sets the initial cache size.

```java
	public AbstractCachingMapDecorator(boolean weak, int size) {
		Map<K, Object> internalMap = weak ? new WeakHashMap<>(size) : new HashMap<>(size);
		this.targetMap = Collections.synchronizedMap(internalMap);
		this.synchronize = true;
		this.weak = weak;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="98">

---

The constructor <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="98:3:14" line-data="	public AbstractCachingMapDecorator(Map&lt;K, V&gt; targetMap) {">`AbstractCachingMapDecorator(Map<K, V> targetMap)`</SwmToken> creates a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="60:7:7" line-data="	 * Create a CachingMapDecorator with strong keys,">`CachingMapDecorator`</SwmToken> for the given <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="98:5:5" line-data="	public AbstractCachingMapDecorator(Map&lt;K, V&gt; targetMap) {">`Map`</SwmToken>. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="94:8:10" line-data="	 * &lt;p&gt;The passed-in Map won&#39;t get synchronized explicitly,">`passed-in`</SwmToken> <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="98:5:5" line-data="	public AbstractCachingMapDecorator(Map&lt;K, V&gt; targetMap) {">`Map`</SwmToken> won't get synchronized explicitly, so make sure to pass in a properly synchronized <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="98:5:5" line-data="	public AbstractCachingMapDecorator(Map&lt;K, V&gt; targetMap) {">`Map`</SwmToken>, if desired.

```java
	public AbstractCachingMapDecorator(Map<K, V> targetMap) {
		this(targetMap, false, false);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="111">

---

The constructor <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="111:3:24" line-data="	public AbstractCachingMapDecorator(Map&lt;K, V&gt; targetMap, boolean synchronize, boolean weak) {">`AbstractCachingMapDecorator(Map<K, V> targetMap, boolean synchronize, boolean weak)`</SwmToken> creates a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="60:7:7" line-data="	 * Create a CachingMapDecorator with strong keys,">`CachingMapDecorator`</SwmToken> for the given <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="111:5:5" line-data="	public AbstractCachingMapDecorator(Map&lt;K, V&gt; targetMap, boolean synchronize, boolean weak) {">`Map`</SwmToken>. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="111:18:18" line-data="	public AbstractCachingMapDecorator(Map&lt;K, V&gt; targetMap, boolean synchronize, boolean weak) {">`synchronize`</SwmToken> parameter determines whether to synchronize on the given <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="111:5:5" line-data="	public AbstractCachingMapDecorator(Map&lt;K, V&gt; targetMap, boolean synchronize, boolean weak) {">`Map`</SwmToken>, and the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="111:23:23" line-data="	public AbstractCachingMapDecorator(Map&lt;K, V&gt; targetMap, boolean synchronize, boolean weak) {">`weak`</SwmToken> parameter determines whether to use weak references for values.

```java
	public AbstractCachingMapDecorator(Map<K, V> targetMap, boolean synchronize, boolean weak) {
		Assert.notNull(targetMap, "'targetMap' must not be null");
		this.targetMap = (Map<K, Object>) (synchronize ? Collections.synchronizedMap(targetMap) : targetMap);
		this.synchronize = synchronize;
		this.weak = weak;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="119">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="119:5:5" line-data="	public int size() {">`size`</SwmToken> returns the size of the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="120:5:5" line-data="		return this.targetMap.size();">`targetMap`</SwmToken>.

```java
	public int size() {
		return this.targetMap.size();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="123">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="123:5:5" line-data="	public boolean isEmpty() {">`isEmpty`</SwmToken> checks if the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="124:5:5" line-data="		return this.targetMap.isEmpty();">`targetMap`</SwmToken> is empty.

```java
	public boolean isEmpty() {
		return this.targetMap.isEmpty();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="127">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="127:5:5" line-data="	public boolean containsKey(Object key) {">`containsKey`</SwmToken> checks if the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="128:5:5" line-data="		return this.targetMap.containsKey(key);">`targetMap`</SwmToken> contains the specified key.

```java
	public boolean containsKey(Object key) {
		return this.targetMap.containsKey(key);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="131">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="131:5:5" line-data="	public boolean containsValue(Object value) {">`containsValue`</SwmToken> checks if the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="134:6:6" line-data="			synchronized (this.targetMap) {">`targetMap`</SwmToken> contains the specified value.

```java
	public boolean containsValue(Object value) {
		Object valueToCheck = (value != null ? value : NULL_VALUE);
		if (this.synchronize) {
			synchronized (this.targetMap) {
				return containsValueOrReference(valueToCheck);
			}
		}
		else {
			return containsValueOrReference(valueToCheck);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="143">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="143:5:5" line-data="	private boolean containsValueOrReference(Object value) {">`containsValueOrReference`</SwmToken> is a private method that checks if the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="144:6:6" line-data="		if (this.targetMap.containsValue(value)) {">`targetMap`</SwmToken> contains the specified value or reference.

```java
	private boolean containsValueOrReference(Object value) {
		if (this.targetMap.containsValue(value)) {
			return true;
		}
		for (Object mapVal : this.targetMap.values()) {
			if (mapVal instanceof Reference && value.equals(((Reference) mapVal).get())) {
				return true;
			}
		}
		return false;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="155">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="155:5:5" line-data="	public V remove(Object key) {">`remove`</SwmToken> removes the mapping for the specified key from the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="156:7:7" line-data="		return unwrapReturnValue(this.targetMap.remove(key));">`targetMap`</SwmToken>.

```java
	public V remove(Object key) {
		return unwrapReturnValue(this.targetMap.remove(key));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="159">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="160:5:5" line-data="	private V unwrapReturnValue(Object value) {">`unwrapReturnValue`</SwmToken> is a private method that unwraps the return value from the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="52:13:13" line-data="	private final Map&lt;K, Object&gt; targetMap;">`targetMap`</SwmToken>, handling <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="162:8:8" line-data="		if (returnValue instanceof Reference) {">`Reference`</SwmToken> and <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="165:8:8" line-data="		return (returnValue == NULL_VALUE ? null : (V) returnValue);">`NULL_VALUE`</SwmToken> appropriately.

```java
	@SuppressWarnings("unchecked")
	private V unwrapReturnValue(Object value) {
		Object returnValue = value;
		if (returnValue instanceof Reference) {
			returnValue = ((Reference) returnValue).get();
		}
		return (returnValue == NULL_VALUE ? null : (V) returnValue);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="168">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="168:5:5" line-data="	public void putAll(Map&lt;? extends K, ? extends V&gt; map) {">`putAll`</SwmToken> copies all of the mappings from the specified map to the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="169:3:3" line-data="		this.targetMap.putAll(map);">`targetMap`</SwmToken>.

```java
	public void putAll(Map<? extends K, ? extends V> map) {
		this.targetMap.putAll(map);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="172">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="172:5:5" line-data="	public void clear() {">`clear`</SwmToken> removes all of the mappings from the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="173:3:3" line-data="		this.targetMap.clear();">`targetMap`</SwmToken>.

```java
	public void clear() {
		this.targetMap.clear();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="176">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="176:8:8" line-data="	public Set&lt;K&gt; keySet() {">`keySet`</SwmToken> returns a set view of the keys contained in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="178:6:6" line-data="			synchronized (this.targetMap) {">`targetMap`</SwmToken>.

```java
	public Set<K> keySet() {
		if (this.synchronize) {
			synchronized (this.targetMap) {
				return new LinkedHashSet<>(this.targetMap.keySet());
			}
		}
		else {
			return new LinkedHashSet<>(this.targetMap.keySet());
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="187">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="187:8:8" line-data="	public Collection&lt;V&gt; values() {">`values`</SwmToken> returns a collection view of the values contained in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="189:6:6" line-data="			synchronized (this.targetMap) {">`targetMap`</SwmToken>.

```java
	public Collection<V> values() {
		if (this.synchronize) {
			synchronized (this.targetMap) {
				return valuesCopy();
			}
		}
		else {
			return valuesCopy();
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" line="198">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="199:8:8" line-data="	private Collection&lt;V&gt; valuesCopy() {">`valuesCopy`</SwmToken> is a private method that returns a copy of the values contained in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="201:15:15" line-data="		for (Iterator&lt;Object&gt; it = this.targetMap.values().iterator(); it.hasNext();) {">`targetMap`</SwmToken>, handling <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="203:8:8" line-data="			if (value instanceof Reference) {">`Reference`</SwmToken> and <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/AbstractCachingMapDecorator.java" pos="210:9:9" line-data="			values.add(value == NULL_VALUE ? null : (V) value);">`NULL_VALUE`</SwmToken> appropriately.

```java
	@SuppressWarnings("unchecked")
	private Collection<V> valuesCopy() {
		LinkedList<V> values = new LinkedList<>();
		for (Iterator<Object> it = this.targetMap.values().iterator(); it.hasNext();) {
			Object value = it.next();
			if (value instanceof Reference) {
				value = ((Reference) value).get();
				if (value == null) {
					it.remove();
					continue;
				}
			}
			values.add(value == NULL_VALUE ? null : (V) value);
		}
		return values;
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" line="45">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="35:4:4" line-data="public class MethodInvoker {">`MethodInvoker`</SwmToken> class, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="48:3:3" line-data="	private AbstractCachingMapDecorator&lt;MethodKey, Method&gt; methodCache = new AbstractCachingMapDecorator&lt;MethodKey, Method&gt;(true) {">`AbstractCachingMapDecorator`</SwmToken> is used to create a cache for invoked bean methods. This cache is keyed weakly, meaning that the keys can be garbage collected when they are no longer in use. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="49:5:5" line-data="		public Method create(MethodKey key) {">`create`</SwmToken> method of the decorator is overridden to return the method associated with the given <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="48:5:5" line-data="	private AbstractCachingMapDecorator&lt;MethodKey, Method&gt; methodCache = new AbstractCachingMapDecorator&lt;MethodKey, Method&gt;(true) {">`MethodKey`</SwmToken>.

```java
	 * A cache of invoked bean methods, keyed weakly.
	 */
	@SuppressWarnings("serial")
	private AbstractCachingMapDecorator<MethodKey, Method> methodCache = new AbstractCachingMapDecorator<MethodKey, Method>(true) {
		public Method create(MethodKey key) {
			return key.getMethod();
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="46">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="40:4:4" line-data="public class DefaultMessageContext implements StateManageableMessageContext {">`DefaultMessageContext`</SwmToken> class, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="48:3:3" line-data="			new AbstractCachingMapDecorator&lt;Object, List&lt;Message&gt;&gt;(new LinkedHashMap&lt;&gt;()) {">`AbstractCachingMapDecorator`</SwmToken> is used to manage a map of source messages. The map is initialized with a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="48:15:15" line-data="			new AbstractCachingMapDecorator&lt;Object, List&lt;Message&gt;&gt;(new LinkedHashMap&lt;&gt;()) {">`LinkedHashMap`</SwmToken>, and the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="50:8:8" line-data="				protected List&lt;Message&gt; create(Object source) {">`create`</SwmToken> method is overridden to return a new <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="51:5:5" line-data="					return new ArrayList&lt;&gt;();">`ArrayList`</SwmToken> for each source.

```java
	@SuppressWarnings("serial")
	private Map<Object, List<Message>> sourceMessages =
			new AbstractCachingMapDecorator<Object, List<Message>>(new LinkedHashMap<>()) {

				protected List<Message> create(Object source) {
					return new ArrayList<>();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/action/DispatchMethodInvoker.java" line="47">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/DispatchMethodInvoker.java" pos="34:2:2" line-data="class DispatchMethodInvoker {">`DispatchMethodInvoker`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/DispatchMethodInvoker.java" pos="50:17:17" line-data="	private Map&lt;String, Method&gt; methodCache = new AbstractCachingMapDecorator&lt;String, Method&gt;() {">`AbstractCachingMapDecorator`</SwmToken> is used to cache resolved methods. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/DispatchMethodInvoker.java" pos="51:5:5" line-data="		public Method create(String key) {">`create`</SwmToken> method is overridden to find and return the method associated with the given key, which is the method name.

```java
	 * The resolved method cache.
	 */
	@SuppressWarnings("serial")
	private Map<String, Method> methodCache = new AbstractCachingMapDecorator<String, Method>() {
		public Method create(String key) {
			String methodName = key;
			try {
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
