---
title: The FlowExecutionImpl class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="75:17:17" line-data="	private static final Log logger = LogFactory.getLog(FlowExecutionImpl.class);">`FlowExecutionImpl`</SwmToken> in the Spring Web Flow project. We will cover:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="75:17:17" line-data="	private static final Log logger = LogFactory.getLog(FlowExecutionImpl.class);">`FlowExecutionImpl`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="75:17:17" line-data="	private static final Log logger = LogFactory.getLog(FlowExecutionImpl.class);">`FlowExecutionImpl`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="75:17:17" line-data="	private static final Log logger = LogFactory.getLog(FlowExecutionImpl.class);">`FlowExecutionImpl`</SwmToken>

<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="75:17:17" line-data="	private static final Log logger = LogFactory.getLog(FlowExecutionImpl.class);">`FlowExecutionImpl`</SwmToken> is the default implementation of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="189:15:15" line-data="						&quot;No active FlowSession to access; this FlowExecution has not been started&quot;);">`FlowExecution`</SwmToken> interface in the Spring Web Flow project. It uses a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="59:17:19" line-data=" * Default implementation of FlowExecution that uses a stack-based data structure to manage spawned flow sessions. This">`stack-based`</SwmToken> data structure to manage spawned flow sessions and is closely coupled with <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="95:5:5" line-data="	private LinkedList&lt;FlowSessionImpl&gt; flowSessions;">`FlowSessionImpl`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="96:3:3" line-data="	public RequestControlContextImpl(FlowExecutionImpl flowExecution, ExternalContext externalContext,">`RequestControlContextImpl`</SwmToken>. This class is serializable, allowing it to be stored in an HTTP session or other persistent stores such as a file, database, or <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="64:21:23" line-data=" * persistent store such as a file, database, or client-side form field. Once deserialized, the">`client-side`</SwmToken> form field. Once deserialized, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="65:7:7" line-data=" * {@link FlowExecutionImplFactory} is expected to be used to restore the execution to a usable state.">`FlowExecutionImplFactory`</SwmToken> is used to restore the execution to a usable state.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="75">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="75:9:9" line-data="	private static final Log logger = LogFactory.getLog(FlowExecutionImpl.class);">`logger`</SwmToken> is used for logging purposes within the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="75:17:17" line-data="	private static final Log logger = LogFactory.getLog(FlowExecutionImpl.class);">`FlowExecutionImpl`</SwmToken> class.

```java
	private static final Log logger = LogFactory.getLog(FlowExecutionImpl.class);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="77">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="77:9:9" line-data="	private static final String FLASH_SCOPE_ATTRIBUTE = &quot;flashScope&quot;;">`FLASH_SCOPE_ATTRIBUTE`</SwmToken> is a constant string used to identify the flash scope attribute.

```java
	private static final String FLASH_SCOPE_ATTRIBUTE = "flashScope";
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="84">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="84:7:7" line-data="	private transient Flow flow;">`flow`</SwmToken> represents the root flow of this flow execution. It is marked as transient to support restoration by the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="65:7:7" line-data=" * {@link FlowExecutionImplFactory} is expected to be used to restore the execution to a usable state.">`FlowExecutionImplFactory`</SwmToken>.

```java
	private transient Flow flow;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="89">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="89:5:5" line-data="	private FlowExecutionStatus status;">`status`</SwmToken> is an enum tracking the status of this flow execution.

```java
	private FlowExecutionStatus status;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="95">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="95:8:8" line-data="	private LinkedList&lt;FlowSessionImpl&gt; flowSessions;">`flowSessions`</SwmToken> is a stack of active, currently executing flow sessions. As subflows are spawned, they are pushed onto the stack. As they end, they are popped off the stack.

```java
	private LinkedList<FlowSessionImpl> flowSessions;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="102">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="102:7:7" line-data="	private transient FlowExecutionListeners listeners;">`listeners`</SwmToken> is a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="98:5:7" line-data="	 * A thread-safe listener list, holding listeners monitoring the lifecycle of this flow execution.">`thread-safe`</SwmToken> listener list holding listeners monitoring the lifecycle of this flow execution. It is marked as transient to support restoration by the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="65:7:7" line-data=" * {@link FlowExecutionImplFactory} is expected to be used to restore the execution to a usable state.">`FlowExecutionImplFactory`</SwmToken>.

```java
	private transient FlowExecutionListeners listeners;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="107">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="107:7:7" line-data="	private transient FlowExecutionKeyFactory keyFactory;">`keyFactory`</SwmToken> is the factory for getting the key to assign this flow execution when needed for persistence.

```java
	private transient FlowExecutionKeyFactory keyFactory;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="112">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="112:7:7" line-data="	private transient FlowExecutionKey key;">`key`</SwmToken> is the key assigned to this flow execution. It may be null if a key has not been assigned.

```java
	private transient FlowExecutionKey key;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="119">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="119:10:10" line-data="	private transient MutableAttributeMap&lt;Object&gt; conversationScope;">`conversationScope`</SwmToken> is a data structure for attributes shared by all flow sessions. It is marked as transient to support restoration by the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="65:7:7" line-data=" * {@link FlowExecutionImplFactory} is expected to be used to restore the execution to a usable state.">`FlowExecutionImplFactory`</SwmToken>.

```java
	private transient MutableAttributeMap<Object> conversationScope;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="126">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="126:10:10" line-data="	private transient AttributeMap&lt;Object&gt; attributes;">`attributes`</SwmToken> is a data structure for runtime system execution attributes. It is marked as transient to support restoration by the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="65:7:7" line-data=" * {@link FlowExecutionImplFactory} is expected to be used to restore the execution to a usable state.">`FlowExecutionImplFactory`</SwmToken>.

```java
	private transient AttributeMap<Object> attributes;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="131">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="131:7:7" line-data="	private transient FlowExecutionOutcome outcome;">`outcome`</SwmToken> represents the outcome reached by this flow execution when it ends.

```java
	private transient FlowExecutionOutcome outcome;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="136">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="136:3:3" line-data="	public FlowExecutionImpl() {">`FlowExecutionImpl`</SwmToken> is the default constructor required for externalizable serialization. It should not be called programmatically.

```java
	public FlowExecutionImpl() {
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="139">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="144:3:3" line-data="	public FlowExecutionImpl(Flow flow) {">`FlowExecutionImpl`</SwmToken> creates a new flow execution executing the provided flow. Flow executions are normally created by a flow execution factory.

```java
	/**
	 * Create a new flow execution executing the provided flow. Flow executions are normally created by a flow execution
	 * factory.
	 * @param flow the root flow of this flow execution
	 */
	public FlowExecutionImpl(Flow flow) {
		Assert.notNull(flow, "The flow definition is required");
		this.flow = flow;
		status = FlowExecutionStatus.NOT_STARTED;
		listeners = new FlowExecutionListeners();
		attributes = CollectionUtils.EMPTY_ATTRIBUTE_MAP;
		flowSessions = new LinkedList<>();
		conversationScope = new LocalAttributeMap<>();
		conversationScope.put(FLASH_SCOPE_ATTRIBUTE, new LocalAttributeMap<>());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="155">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="155:5:5" line-data="	public String getCaption() {">`getCaption`</SwmToken> returns a string caption for the flow execution.

```java
	public String getCaption() {
		return "execution of '" + flow.getId() + "'";
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="161">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="161:5:5" line-data="	public FlowExecutionKey getKey() {">`getKey`</SwmToken> returns the key assigned to this flow execution.

```java
	public FlowExecutionKey getKey() {
		return key;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="165">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="165:5:5" line-data="	public FlowDefinition getDefinition() {">`getDefinition`</SwmToken> returns the flow definition of this flow execution.

```java
	public FlowDefinition getDefinition() {
		return flow;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="169">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="169:5:5" line-data="	public boolean hasStarted() {">`hasStarted`</SwmToken> checks if the flow execution has started.

```java
	public boolean hasStarted() {
		return status == FlowExecutionStatus.ACTIVE || status == FlowExecutionStatus.ENDED;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="173">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="173:5:5" line-data="	public boolean isActive() {">`isActive`</SwmToken> checks if the flow execution is currently active.

```java
	public boolean isActive() {
		return status == FlowExecutionStatus.ACTIVE;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="177">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="177:5:5" line-data="	public boolean hasEnded() {">`hasEnded`</SwmToken> checks if the flow execution has ended.

```java
	public boolean hasEnded() {
		return status == FlowExecutionStatus.ENDED;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="181">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="181:5:5" line-data="	public FlowExecutionOutcome getOutcome() {">`getOutcome`</SwmToken> returns the outcome reached by this flow execution when it ends.

```java
	public FlowExecutionOutcome getOutcome() {
		return outcome;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="185">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="185:5:5" line-data="	public FlowSession getActiveSession() {">`getActiveSession`</SwmToken> returns the active session of the flow execution.

```java
	public FlowSession getActiveSession() {
		if (!isActive()) {
			if (status == FlowExecutionStatus.NOT_STARTED) {
				throw new IllegalStateException(
						"No active FlowSession to access; this FlowExecution has not been started");
			} else {
				throw new IllegalStateException("No active FlowSession to access; this FlowExecution has ended");
			}
		}
		return getActiveSessionInternal();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="197">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="198:8:8" line-data="	public MutableAttributeMap&lt;Object&gt; getFlashScope() {">`getFlashScope`</SwmToken> returns the flash scope of the flow execution.

```java
	@SuppressWarnings("unchecked")
	public MutableAttributeMap<Object> getFlashScope() {
		return (MutableAttributeMap<Object>) conversationScope.get(FLASH_SCOPE_ATTRIBUTE);
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" line="77">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="65:7:7" line-data=" * {@link FlowExecutionImplFactory} is expected to be used to restore the execution to a usable state.">`FlowExecutionImplFactory`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" pos="80:1:1" line-data="		FlowExecutionImpl execution = new FlowExecutionImpl((Flow) flowDefinition);">`FlowExecutionImpl`</SwmToken> is instantiated and configured with various attributes, listeners, and key factories. This setup is crucial for creating new flow executions and restoring existing ones.

```java
		if (logger.isDebugEnabled()) {
			logger.debug("Creating new execution of '" + flowDefinition.getId() + "'");
		}
		FlowExecutionImpl execution = new FlowExecutionImpl((Flow) flowDefinition);
		execution.setAttributes(executionAttributes);
		execution.setListeners(executionListenerLoader.getListeners(execution.getDefinition()));
		execution.setKeyFactory(executionKeyFactory);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" line="87">

---

Additionally, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" pos="87:5:5" line-data="	public FlowExecution restoreFlowExecution(FlowExecution flowExecution, FlowDefinition flowDefinition,">`restoreFlowExecution`</SwmToken> method in the same class ensures that the provided <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" pos="87:3:3" line-data="	public FlowExecution restoreFlowExecution(FlowExecution flowExecution, FlowDefinition flowDefinition,">`FlowExecution`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" pos="87:12:12" line-data="	public FlowExecution restoreFlowExecution(FlowExecution flowExecution, FlowDefinition flowDefinition,">`FlowDefinition`</SwmToken> are of the correct types before casting them to <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" pos="90:5:5" line-data="		Assert.isInstanceOf(FlowExecutionImpl.class, flowExecution, &quot;FlowExecution is of the wrong type: &quot;);">`FlowExecutionImpl`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" pos="91:5:5" line-data="		Assert.isInstanceOf(Flow.class, flowDefinition, &quot;FlowDefinition is of the wrong type: &quot;);">`Flow`</SwmToken>, respectively. This method is responsible for restoring the state of a flow execution.

```java
	public FlowExecution restoreFlowExecution(FlowExecution flowExecution, FlowDefinition flowDefinition,
			FlowExecutionKey flowExecutionKey, MutableAttributeMap<Object> conversationScope,
			FlowDefinitionLocator subflowDefinitionLocator) {
		Assert.isInstanceOf(FlowExecutionImpl.class, flowExecution, "FlowExecution is of the wrong type: ");
		Assert.isInstanceOf(Flow.class, flowDefinition, "FlowDefinition is of the wrong type: ");
		FlowExecutionImpl execution = (FlowExecutionImpl) flowExecution;
		Flow flow = (Flow) flowDefinition;
		execution.setFlow(flow);
		if (execution.hasSessions()) {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" line="49">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="96:3:3" line-data="	public RequestControlContextImpl(FlowExecutionImpl flowExecution, ExternalContext externalContext,">`RequestControlContextImpl`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="52:3:3" line-data="	private FlowExecutionImpl flowExecution;">`FlowExecutionImpl`</SwmToken> is used to carry out requests. It is passed as a parameter to the constructor and stored as a private member variable, indicating its role in managing the flow execution context during a request.

```java
	/**
	 * The owning flow execution carrying out this request.
	 */
	private FlowExecutionImpl flowExecution;

	/**
	 * A source context for the caller who initiated this request.
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" line="93">

---

The constructor of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="96:3:3" line-data="	public RequestControlContextImpl(FlowExecutionImpl flowExecution, ExternalContext externalContext,">`RequestControlContextImpl`</SwmToken> initializes the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="96:7:7" line-data="	public RequestControlContextImpl(FlowExecutionImpl flowExecution, ExternalContext externalContext,">`flowExecution`</SwmToken> member variable with the provided <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="96:5:5" line-data="	public RequestControlContextImpl(FlowExecutionImpl flowExecution, ExternalContext externalContext,">`FlowExecutionImpl`</SwmToken> instance, highlighting its importance in the execution of requests.

```java
	 * @param messageContext the message context for recording status or validation messages during the execution of
	 * this request
	 */
	public RequestControlContextImpl(FlowExecutionImpl flowExecution, ExternalContext externalContext,
			MessageContext messageContext) {
		this.flowExecution = flowExecution;
		this.externalContext = externalContext;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
