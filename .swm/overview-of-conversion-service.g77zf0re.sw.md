---
title: Overview of Conversion Service
---
# What is Conversion Service

A Conversion Service in Spring is a central interface for type conversion. It is used to convert objects from one type to another throughout the application.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" line="5">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" pos="27:4:4" line-data="public class RuntimeBindingConversionExecutor implements ConversionExecutor {">`RuntimeBindingConversionExecutor`</SwmToken> class is a conversion executor that defers the resolution of its converter until the time of conversion.

```java
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      https://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
```

---

</SwmSnippet>

It is initialized with a target class and a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" pos="20:10:10" line-data="import org.springframework.binding.convert.ConversionService;">`ConversionService`</SwmToken> from which it retrieves the appropriate converter.

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" pos="65:5:5" line-data="	public Object execute(Object source) throws ConversionExecutionException {">`execute`</SwmToken> method performs the conversion by obtaining a conversion executor from the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" pos="20:10:10" line-data="import org.springframework.binding.convert.ConversionService;">`ConversionService`</SwmToken> and executing the conversion.

## GenericConversionService

The `GenericConversionService` class is a base implementation of a conversion service that initially registers no converters.

It maintains a map of custom converters and aliases for target types, and can optionally have a parent conversion service.

## DefaultConversionService

The `DefaultConversionService` class extends `GenericConversionService` and automatically registers default converters and aliases for standard Java types.

# Service Classes

Service classes in the project are designed to handle various conversion tasks. They encapsulate the logic required to convert objects from one type to another, ensuring that the conversion process is consistent and reusable across the application.

## Usage of Service Classes

Service classes are used in different parts of the project where object conversion is necessary. For example, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" pos="27:4:4" line-data="public class RuntimeBindingConversionExecutor implements ConversionExecutor {">`RuntimeBindingConversionExecutor`</SwmToken> class utilizes a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" pos="20:10:10" line-data="import org.springframework.binding.convert.ConversionService;">`ConversionService`</SwmToken> to perform runtime conversions. This allows the application to defer the resolution of its converter until the time of conversion, providing flexibility and efficiency.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" line="5">

---

An example of a service class usage is the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" pos="27:4:4" line-data="public class RuntimeBindingConversionExecutor implements ConversionExecutor {">`RuntimeBindingConversionExecutor`</SwmToken> class. It is initialized with a target class and a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" pos="20:10:10" line-data="import org.springframework.binding.convert.ConversionService;">`ConversionService`</SwmToken> from which it retrieves the appropriate converter. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" pos="65:5:5" line-data="	public Object execute(Object source) throws ConversionExecutionException {">`execute`</SwmToken> method performs the conversion by obtaining a conversion executor from the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/service/RuntimeBindingConversionExecutor.java" pos="20:10:10" line-data="import org.springframework.binding.convert.ConversionService;">`ConversionService`</SwmToken> and executing the conversion.

```java
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      https://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
