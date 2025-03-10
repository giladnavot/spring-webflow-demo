---
title: Getting Started with Flow Execution Implementation
---
# Overview of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="16:10:10" line-data="package org.springframework.webflow.engine.impl;">`impl`</SwmToken> Package

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="16:10:10" line-data="package org.springframework.webflow.engine.impl;">`impl`</SwmToken> package in the Engine directory contains implementation classes for the flow execution mechanism in Spring Web Flow. These classes provide concrete implementations of interfaces and abstract classes defined in the framework, ensuring that the flow execution is managed correctly.

## Key Classes in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="16:10:10" line-data="package org.springframework.webflow.engine.impl;">`impl`</SwmToken> Package

One of the key classes in this package is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="347:3:3" line-data="	protected FlowSessionImpl createFlowSession(Flow flow, FlowSessionImpl parent) {">`FlowSessionImpl`</SwmToken>, which implements the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="53:10:10" line-data="import org.springframework.webflow.execution.FlowSession;">`FlowSession`</SwmToken> interface and is used internally by <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="73:4:4" line-data="public class FlowExecutionImpl implements FlowExecution, Externalizable {">`FlowExecutionImpl`</SwmToken>. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="347:3:3" line-data="	protected FlowSessionImpl createFlowSession(Flow flow, FlowSessionImpl parent) {">`FlowSessionImpl`</SwmToken> class is closely coupled with <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="73:4:4" line-data="public class FlowExecutionImpl implements FlowExecution, Externalizable {">`FlowExecutionImpl`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="60:30:30" line-data=" * class is closely coupled with package-private &lt;code&gt;FlowSessionImpl&lt;/code&gt; and &lt;code&gt;RequestControlContextImpl&lt;/code&gt;">`RequestControlContextImpl`</SwmToken>, working together to form a complete flow execution implementation.

## Functionality of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="347:3:3" line-data="	protected FlowSessionImpl createFlowSession(Flow flow, FlowSessionImpl parent) {">`FlowSessionImpl`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="347:3:3" line-data="	protected FlowSessionImpl createFlowSession(Flow flow, FlowSessionImpl parent) {">`FlowSessionImpl`</SwmToken> class manages the flow definition, the current state of the flow session, and the session data model, also known as 'flow scope'. It ensures that the flow's state and data are correctly maintained throughout its execution.

## Usage in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="73:4:4" line-data="public class FlowExecutionImpl implements FlowExecution, Externalizable {">`FlowExecutionImpl`</SwmToken>

Another important class in this package is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="73:4:4" line-data="public class FlowExecutionImpl implements FlowExecution, Externalizable {">`FlowExecutionImpl`</SwmToken>, which represents the execution of a flow and manages the flow's lifecycle, including starting, resuming, and ending the flow. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="73:4:4" line-data="public class FlowExecutionImpl implements FlowExecution, Externalizable {">`FlowExecutionImpl`</SwmToken> class uses <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="347:3:3" line-data="	protected FlowSessionImpl createFlowSession(Flow flow, FlowSessionImpl parent) {">`FlowSessionImpl`</SwmToken> to create and manage flow sessions.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="347">

---

For example, in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="73:4:4" line-data="public class FlowExecutionImpl implements FlowExecution, Externalizable {">`FlowExecutionImpl`</SwmToken> class, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="347:5:5" line-data="	protected FlowSessionImpl createFlowSession(Flow flow, FlowSessionImpl parent) {">`createFlowSession`</SwmToken> method creates a new <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="347:3:3" line-data="	protected FlowSessionImpl createFlowSession(Flow flow, FlowSessionImpl parent) {">`FlowSessionImpl`</SwmToken> instance to manage a flow session.

```java
	protected FlowSessionImpl createFlowSession(Flow flow, FlowSessionImpl parent) {
		return new FlowSessionImpl(flow, parent);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
