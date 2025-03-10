---
title: Basic Concepts of Core Components
---
# Core Overview

Core refers to the foundational, generic types that are usable by all other packages in the Web Flow framework. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/AnnotatedObject.java" pos="16:2:8" line-data="package org.springframework.webflow.core;">`org.springframework.webflow.core`</SwmToken> package contains essential classes and interfaces that provide the base functionality for the Web Flow system.

## Key Classes and Interfaces

One of the key classes in this package is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/AnnotatedObject.java" pos="28:6:6" line-data="public abstract class AnnotatedObject implements Annotated {">`AnnotatedObject`</SwmToken>, which serves as a base class for all objects in the web flow system that support annotation using arbitrary properties. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/AnnotatedObject.java" pos="28:6:6" line-data="public abstract class AnnotatedObject implements Annotated {">`AnnotatedObject`</SwmToken> class ensures consistent configuration of properties for all annotated objects, making it a crucial part of the core functionality.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/AnnotatedObject.java" line="5">

---

An example of the core functionality can be seen in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/AnnotatedObject.java" pos="28:6:6" line-data="public abstract class AnnotatedObject implements Annotated {">`AnnotatedObject`</SwmToken> class, which is used to support annotation using arbitrary properties.

```java
 * you may not use this file except in compliance with the License.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
