---
title: Introduction to Support Utilities
---
# Introduction to Support Utilities

Support utilities in Spring Web Flow refer to various helper classes and utilities designed to facilitate the execution of flow repositories within the framework.

## Location of Support Classes

These support classes are located in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/support/AbstractFlowExecutionRepository.java" pos="16:2:12" line-data="package org.springframework.webflow.execution.repository.support;">`org.springframework.webflow.execution.repository.support`</SwmToken> package.

## Key Support Classes

The package includes several important classes such as <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/support/AbstractFlowExecutionRepository.java" pos="43:32:32" line-data=" * medium used to store active flow executions. Mandates the use of a {@link FlowExecutionStateRestorer}, used to">`FlowExecutionStateRestorer`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/support/AbstractFlowExecutionRepository.java" pos="97:1:1" line-data="		CompositeFlowExecutionKey key = (CompositeFlowExecutionKey) execution.getKey();">`CompositeFlowExecutionKey`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/support/AbstractFlowExecutionRepository.java" pos="125:5:5" line-data="		return new ConversationBackedFlowExecutionLock(getConversation(key));">`ConversationBackedFlowExecutionLock`</SwmToken>, and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/support/AbstractFlowExecutionRepository.java" pos="52:6:6" line-data="public abstract class AbstractFlowExecutionRepository implements FlowExecutionRepository, FlowExecutionKeyFactory {">`AbstractFlowExecutionRepository`</SwmToken>.

## Role of Support Classes

Each of these classes plays a specific role in managing the state, keys, locks, and overall execution of flow repositories.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/repository/support/AbstractFlowExecutionRepository.java" line="43">

---

For example, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/support/AbstractFlowExecutionRepository.java" pos="52:6:6" line-data="public abstract class AbstractFlowExecutionRepository implements FlowExecutionRepository, FlowExecutionKeyFactory {">`AbstractFlowExecutionRepository`</SwmToken> class mandates the use of a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/support/AbstractFlowExecutionRepository.java" pos="43:32:32" line-data=" * medium used to store active flow executions. Mandates the use of a {@link FlowExecutionStateRestorer}, used to">`FlowExecutionStateRestorer`</SwmToken> to store active flow executions.

```java
 * medium used to store active flow executions. Mandates the use of a {@link FlowExecutionStateRestorer}, used to
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
