---
title: The ArrayToCollection class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="56:3:3" line-data="	public ArrayToCollection(ConversionService conversionService) {">`ArrayToCollection`</SwmToken> in the Spring Web Flow project. We will cover:

1. What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="56:3:3" line-data="	public ArrayToCollection(ConversionService conversionService) {">`ArrayToCollection`</SwmToken>
2. Variables and functions in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="56:3:3" line-data="	public ArrayToCollection(ConversionService conversionService) {">`ArrayToCollection`</SwmToken>

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="56:3:3" line-data="	public ArrayToCollection(ConversionService conversionService) {">`ArrayToCollection`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="56:3:3" line-data="	public ArrayToCollection(ConversionService conversionService) {">`ArrayToCollection`</SwmToken> class is a special converter that converts a source array to a target collection. It supports the selection of an approximate collection implementation when a target collection interface such as <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="121:4:6" line-data="			if (List.class.equals(targetClass)) {">`List.class`</SwmToken> is specified. It also supports type conversion of array elements when a concrete parameterized collection class is provided, such as <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="36:11:15" line-data=" * such as {@code IntegerList&lt;Integer&gt;.class}.">`IntegerList<Integer>.class`</SwmToken>. This class is mainly used internally by <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="56:5:5" line-data="	public ArrayToCollection(ConversionService conversionService) {">`ConversionService`</SwmToken> implementations.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" line="56">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="56:3:3" line-data="	public ArrayToCollection(ConversionService conversionService) {">`ArrayToCollection`</SwmToken> constructor initializes the converter with a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="56:5:5" line-data="	public ArrayToCollection(ConversionService conversionService) {">`ConversionService`</SwmToken> to look up the converter to apply to array elements added to the target collection.

```java
	public ArrayToCollection(ConversionService conversionService) {
		this.conversionService = conversionService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" line="64">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="64:3:3" line-data="	public ArrayToCollection(ConversionExecutor elementConverter) {">`ArrayToCollection`</SwmToken> constructor initializes the converter with a specific <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="64:5:5" line-data="	public ArrayToCollection(ConversionExecutor elementConverter) {">`ConversionExecutor`</SwmToken> to use on array elements when adding them to the target collection.

```java
	public ArrayToCollection(ConversionExecutor elementConverter) {
		this.elementConverter = elementConverter;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" line="68">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="68:6:6" line-data="	public Class&lt;?&gt; getSourceClass() {">`getSourceClass`</SwmToken> function returns the source class type, which is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="69:3:7" line-data="		return Object[].class;">`Object[].class`</SwmToken>.

```java
	public Class<?> getSourceClass() {
		return Object[].class;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" line="72">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="72:6:6" line-data="	public Class&lt;?&gt; getTargetClass() {">`getTargetClass`</SwmToken> function returns the target class type, which is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="73:3:5" line-data="		return Collection.class;">`Collection.class`</SwmToken>.

```java
	public Class<?> getTargetClass() {
		return Collection.class;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" line="77">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="77:5:5" line-data="	public Object convertSourceToTargetClass(Object source, Class&lt;?&gt; targetClass) throws Exception {">`convertSourceToTargetClass`</SwmToken> function converts the source array to the target collection class. It handles null sources, determines the appropriate collection implementation class, and converts each array element to the target collection.

```java
	public Object convertSourceToTargetClass(Object source, Class<?> targetClass) throws Exception {
		if (source == null) {
			return null;
		}
		Class<?> collectionImplClass = getCollectionImplClass(targetClass);
		Constructor<?> constructor = collectionImplClass.getConstructor();
		Collection<Object> collection = (Collection<Object>) constructor.newInstance();
		ConversionExecutor converter = getArrayElementConverter(source, targetClass);
		int length = Array.getLength(source);
		for (int i = 0; i < length; i++) {
			Object value = Array.get(source, i);
			if (converter != null) {
				value = converter.execute(value);
			}
			collection.add(value);
		}
		return collection;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" line="96">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="96:5:5" line-data="	public Object convertTargetToSourceClass(Object target, Class&lt;?&gt; sourceClass) {">`convertTargetToSourceClass`</SwmToken> function converts the target collection back to the source array class. It handles null targets, creates a new array instance, and converts each collection element back to the array.

```java
	public Object convertTargetToSourceClass(Object target, Class<?> sourceClass) {
		if (target == null) {
			return null;
		}
		Collection<?> collection = (Collection<?>) target;
		Object array = Array.newInstance(sourceClass.getComponentType(), collection.size());
		int i = 0;
		for (Object value : collection) {
			if (value != null) {
				ConversionExecutor converter;
				if (elementConverter != null) {
					converter = elementConverter;
				} else {
					converter = conversionService.getConversionExecutor(value.getClass(),
							sourceClass.getComponentType());
				}
				value = converter.execute(value);
			}
			Array.set(array, i++, value);
		}
		return array;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" line="119">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="119:6:6" line-data="	private Class&lt;?&gt; getCollectionImplClass(Class&lt;?&gt; targetClass) {">`getCollectionImplClass`</SwmToken> function determines the appropriate collection implementation class based on the target class. It supports interfaces like `List`, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="123:8:8" line-data="			} else if (Set.class.equals(targetClass)) {">`Set`</SwmToken>, and <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="125:8:8" line-data="			} else if (SortedSet.class.equals(targetClass)) {">`SortedSet`</SwmToken>.

```java
	private Class<?> getCollectionImplClass(Class<?> targetClass) {
		if (targetClass.isInterface()) {
			if (List.class.equals(targetClass)) {
				return ArrayList.class;
			} else if (Set.class.equals(targetClass)) {
				return LinkedHashSet.class;
			} else if (SortedSet.class.equals(targetClass)) {
				return TreeSet.class;
			} else {
				throw new IllegalArgumentException("Unsupported collection interface [" + targetClass.getName() + "]");
			}
		} else {
			return targetClass;
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" line="136">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="136:5:5" line-data="	private ConversionExecutor getArrayElementConverter(Object source, Class&lt;?&gt; targetClass) {">`getArrayElementConverter`</SwmToken> function retrieves the appropriate converter for array elements based on the target class. It uses the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="137:4:4" line-data="		if (elementConverter != null) {">`elementConverter`</SwmToken> if provided, otherwise it looks up the converter using the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/ArrayToCollection.java" pos="143:3:3" line-data="				return conversionService.getConversionExecutor(componentType, elementType);">`conversionService`</SwmToken>.

```java
	private ConversionExecutor getArrayElementConverter(Object source, Class<?> targetClass) {
		if (elementConverter != null) {
			return elementConverter;
		} else {
			Class<?> elementType = ResolvableType.forClass(targetClass).asCollection().resolveGeneric(0);
			if (elementType != null) {
				Class<?> componentType = source.getClass().getComponentType();
				return conversionService.getConversionExecutor(componentType, elementType);
			}
			return null;
		}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" line="221">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="45:4:4" line-data="public class GenericConversionService implements ConversionService {">`GenericConversionService`</SwmToken> class, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="223:15:15" line-data="					return new StaticConversionExecutor(sourceClass, targetClass, new ArrayToCollection(">`ArrayToCollection`</SwmToken> is used to create a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="221:9:9" line-data="					ConversionExecutor elementConverter = new StaticConversionExecutor(sourceComponentType,">`StaticConversionExecutor`</SwmToken> for converting an array to a collection. This is done by passing an <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="221:3:3" line-data="					ConversionExecutor elementConverter = new StaticConversionExecutor(sourceComponentType,">`elementConverter`</SwmToken> to the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="223:15:15" line-data="					return new StaticConversionExecutor(sourceClass, targetClass, new ArrayToCollection(">`ArrayToCollection`</SwmToken> constructor.

```java
					ConversionExecutor elementConverter = new StaticConversionExecutor(sourceComponentType,
							converter.getTargetClass(), converter);
					return new StaticConversionExecutor(sourceClass, targetClass, new ArrayToCollection(
							elementConverter));
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" line="228">

---

Another usage in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="45:4:4" line-data="public class GenericConversionService implements ConversionService {">`GenericConversionService`</SwmToken> class involves handling two-way converters. Here, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="230:15:15" line-data="					return new StaticConversionExecutor(sourceClass, targetClass, new ArrayToCollection(">`ArrayToCollection`</SwmToken> is again used to create a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="228:9:9" line-data="					ConversionExecutor elementConverter = new StaticConversionExecutor(sourceComponentType,">`StaticConversionExecutor`</SwmToken>, but this time it is combined with a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="229:10:10" line-data="							converter.getSourceClass(), new ReverseConverter(twoWay));">`ReverseConverter`</SwmToken> to facilitate the conversion process.

```java
					ConversionExecutor elementConverter = new StaticConversionExecutor(sourceComponentType,
							converter.getSourceClass(), new ReverseConverter(twoWay));
					return new StaticConversionExecutor(sourceClass, targetClass, new ArrayToCollection(
							elementConverter));
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" line="248">

---

Additionally, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="248:13:13" line-data="					Converter collectionToArray = new ReverseConverter(new ArrayToCollection(elementConverter));">`ArrayToCollection`</SwmToken> is used in conjunction with a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="248:9:9" line-data="					Converter collectionToArray = new ReverseConverter(new ArrayToCollection(elementConverter));">`ReverseConverter`</SwmToken> to convert a collection back to an array. This is achieved by creating a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="249:5:5" line-data="					return new StaticConversionExecutor(sourceClass, targetClass, collectionToArray);">`StaticConversionExecutor`</SwmToken> with the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/GenericConversionService.java" pos="248:3:3" line-data="					Converter collectionToArray = new ReverseConverter(new ArrayToCollection(elementConverter));">`collectionToArray`</SwmToken> converter.

```java
					Converter collectionToArray = new ReverseConverter(new ArrayToCollection(elementConverter));
					return new StaticConversionExecutor(sourceClass, targetClass, collectionToArray);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
