---
title: The RequestControlContext interface
---
This document will cover the interface <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="52:10:10" line-data="	 * @see State#enter(RequestControlContext)">`RequestControlContext`</SwmToken> in the Spring Web Flow project. We will cover:

1. What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="52:10:10" line-data="	 * @see State#enter(RequestControlContext)">`RequestControlContext`</SwmToken>
2. Variables and functions in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="52:10:10" line-data="	 * @see State#enter(RequestControlContext)">`RequestControlContext`</SwmToken>

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="52:10:10" line-data="	 * @see State#enter(RequestControlContext)">`RequestControlContext`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="52:10:10" line-data="	 * @see State#enter(RequestControlContext)">`RequestControlContext`</SwmToken> interface in <SwmPath>[spring-webflow/…/engine/RequestControlContext.java](spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java)</SwmPath> is a mutable control interface used to manipulate an ongoing flow execution in the context of one client request. It is primarily used internally by various flow artifacts when they are invoked. This interface acts as a facade for core definition constructs such as the central <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="88:6:6" line-data="	 * @see Flow#handleEvent(RequestControlContext)">`Flow`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="50:11:11" line-data="	 * new state by the State type itself.">`State`</SwmToken> classes, abstracting away details about the runtime execution machine. Unlike <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="20:10:10" line-data="import org.springframework.webflow.execution.FlowExecutionContext;">`FlowExecutionContext`</SwmToken>, which provides information about a single flow execution (conversation) and is not local to a specific request, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="52:10:10" line-data="	 * @see State#enter(RequestControlContext)">`RequestControlContext`</SwmToken> is request-specific and provides a control interface for manipulating exactly one flow execution locally from exactly one request.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="48">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="54:3:3" line-data="	void setCurrentState(State state);">`setCurrentState`</SwmToken> records the current state that has entered in the executing flow. This method is called as part of entering a new state by the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="50:11:11" line-data="	 * new state by the State type itself.">`State`</SwmToken> type itself.

```java
	/**
	 * Record the current state that has entered in the executing flow. This method will be called as part of entering a
	 * new state by the State type itself.
	 * @param state the current state
	 * @see State#enter(RequestControlContext)
	 */
	void setCurrentState(State state);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="56">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="60:3:3" line-data="	FlowExecutionKey assignFlowExecutionKey();">`assignFlowExecutionKey`</SwmToken> assigns the ongoing flow execution its flow execution key. This method is called before a state is about to render a view and pause the flow execution.

```java
	/**
	 * Assign the ongoing flow execution its flow execution key. This method will be called before a state is about to
	 * render a view and pause the flow execution.
	 */
	FlowExecutionKey assignFlowExecutionKey();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="62">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="66:3:3" line-data="	void setCurrentView(View view);">`setCurrentView`</SwmToken> sets the current view. It can also mark the current view as <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="64:17:17" line-data="	 * @param view the current view, or null to mark the current view as &lt;code&gt;null&lt;/code&gt;">`null`</SwmToken>.

```java
	/**
	 * Sets the current view.
	 * @param view the current view, or null to mark the current view as <code>null</code>
	 */
	void setCurrentView(View view);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="68">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="72:3:3" line-data="	void viewRendering(View view);">`viewRendering`</SwmToken> is called when the current view is about to be rendered in the current view state.

```java
	/**
	 * Called when the current view is about to be rendered in the current view state.
	 * @param view the view to be rendered
	 */
	void viewRendering(View view);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="74">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="78:3:3" line-data="	void viewRendered(View view);">`viewRendered`</SwmToken> is called when the current view has completed rendering in the current view state.

```java
	/**
	 * Called when the current view has completed rendering in the current view state.
	 * @param view the view that rendered
	 */
	void viewRendered(View view);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="80">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="88:8:8" line-data="	 * @see Flow#handleEvent(RequestControlContext)">`handleEvent`</SwmToken> signals the occurrence of an event in the current state of this flow execution request context. This method should be called by clients that report internal event occurrences, such as action states.

```java
	/**
	 * Signals the occurrence of an event in the current state of this flow execution request context. This method
	 * should be called by clients that report internal event occurrences, such as action states. The
	 * <code>onEvent()</code> method of the flow involved in the flow execution will be called.
	 * @param event the event that occurred
	 * @return a boolean indicating if handling this event caused the current state to exit and a new state to enter
	 * @throws FlowExecutionException if an exception was thrown within a state of the flow during execution of this
	 * signalEvent operation
	 * @see Flow#handleEvent(RequestControlContext)
	 */
	boolean handleEvent(Event event) throws FlowExecutionException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="92">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="96:8:8" line-data="	 * @see Transition#execute(State, RequestControlContext)">`execute`</SwmToken> executes a transition out of the current source state. It allows for privileged execution of an arbitrary transition.

```java
	/**
	 * Execute this transition out of the current source state. Allows for privileged execution of an arbitrary
	 * transition.
	 * @param transition the transition
	 * @see Transition#execute(State, RequestControlContext)
	 */
	boolean execute(Transition transition);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="100">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="106:3:3" line-data="	void setCurrentTransition(Transition transition);">`setCurrentTransition`</SwmToken> records the transition executing in the flow. This method is called as part of executing a transition from one state to another.

```java
	/**
	 * Record the transition executing in the flow. This method will be called as part of executing a transition from
	 * one state to another.
	 * @param transition the transition being executed
	 * @see Transition#execute(State, RequestControlContext)
	 */
	void setCurrentTransition(Transition transition);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="108">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="111:3:3" line-data="	void updateCurrentFlowExecutionSnapshot();">`updateCurrentFlowExecutionSnapshot`</SwmToken> updates the current flow execution snapshot to save the current state.

```java
	/**
	 * Update the current flow execution snapshot to save the current state.
	 */
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="112">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="116:3:3" line-data="	void removeCurrentFlowExecutionSnapshot();">`removeCurrentFlowExecutionSnapshot`</SwmToken> removes the current flow execution snapshot to invalidate the current state.

```java

	/**
	 * Remove the current flow execution snapshot to invalidate the current state.
	 */
	void removeCurrentFlowExecutionSnapshot();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="118">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="121:3:3" line-data="	void removeAllFlowExecutionSnapshots();">`removeAllFlowExecutionSnapshots`</SwmToken> removes all flow execution snapshots associated with the ongoing conversation, invalidating previous states.

```java
	/**
	 * Remove all flow execution snapshots associated with the ongoing conversation. Invalidates previous states.
	 */
	void removeAllFlowExecutionSnapshots();

```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="124">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="125:5:5" line-data="	 * its start state. This method should be called by clients that wish to spawn new flows, such as subflow states.">`start`</SwmToken> spawns a new flow session and activates it in the currently executing flow. It also transitions the spawned flow to its start state.

```java
	 * Spawn a new flow session and activate it in the currently executing flow. Also transitions the spawned flow to
	 * its start state. This method should be called by clients that wish to spawn new flows, such as subflow states.
	 * <p>
	 * This will start a new flow session in the current flow execution, which is already active.
	 * @param flow the flow to start, its <code>start()</code> method will be called
	 * @param input initial contents of the newly created flow session (may be <code>null</code>, e.g. empty)
	 * @throws FlowExecutionException if an exception was thrown within a state of the flow during execution of this
	 * start operation
	 * @see Flow#start(RequestControlContext, MutableAttributeMap)
	 */
	void start(Flow flow, MutableAttributeMap<?> input) throws FlowExecutionException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="136">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="145:3:3" line-data="	void endActiveFlowSession(String outcome, MutableAttributeMap&lt;Object&gt; output) throws IllegalStateException;">`endActiveFlowSession`</SwmToken> ends the active flow session of the current flow execution. This method should be called by clients that terminate flows, such as end states.

```java
	/**
	 * End the active flow session of the current flow execution. This method should be called by clients that terminate
	 * flows, such as end states. The <code>end()</code> method of the flow involved in the flow execution will be
	 * called.
	 * @param outcome the logical outcome the ending session should return
	 * @param output output the ending session should return
	 * @throws IllegalStateException when the flow execution is not active
	 * @see Flow#end(RequestControlContext, String, MutableAttributeMap)
	 */
	void endActiveFlowSession(String outcome, MutableAttributeMap<Object> output) throws IllegalStateException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="147">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="151:3:3" line-data="	boolean getRedirectOnPause();">`getRedirectOnPause`</SwmToken> returns true if the 'redirect on pause' flow execution attribute is set to true, false otherwise.

```java
	/**
	 * Returns true if the 'redirect on pause' flow execution attribute is set to true, false otherwise.
	 * @return true or false
	 */
	boolean getRedirectOnPause();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="153">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="158:3:3" line-data="	boolean getRedirectInSameState();">`getRedirectInSameState`</SwmToken> returns the value of the 'redirect in same state' flow execution attribute if set or otherwise it falls back on the value returned by <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="155:16:16" line-data="	 * the value returned by {@link #getRedirectOnPause()}.">`getRedirectOnPause`</SwmToken>.

```java
	/**
	 * Returns the value of the 'redirect in same state' flow execution attribute if set or otherwise it falls back on
	 * the value returned by {@link #getRedirectOnPause()}.
	 * @return true or false
	 */
	boolean getRedirectInSameState();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="160">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="164:3:3" line-data="	boolean getEmbeddedMode();">`getEmbeddedMode`</SwmToken> returns true if the current flow execution was launched in embedded page mode. When a flow is embedded on a page, it can make different assumptions with regards to whether redirect after post is necessary.

```java
	/**
	 * Returns true if the flow current flow execution was launched in embedded page mode. When a flow is embedded on a
	 * page it can make different assumptions with regards to whether redirect after post is necessary.
	 */
	boolean getEmbeddedMode();
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" line="165">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" pos="34:11:11" line-data=" * this, a &lt;code&gt;ViewState&lt;/code&gt; delegates to a {@link ViewFactory}.">`ViewState`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" pos="165:7:7" line-data="	protected void doPreEntryActions(RequestControlContext context) throws FlowExecutionException {">`RequestControlContext`</SwmToken> is used in several methods to manage the state transitions and actions. For instance, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" pos="165:5:5" line-data="	protected void doPreEntryActions(RequestControlContext context) throws FlowExecutionException {">`doPreEntryActions`</SwmToken> method uses <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" pos="165:7:7" line-data="	protected void doPreEntryActions(RequestControlContext context) throws FlowExecutionException {">`RequestControlContext`</SwmToken> to create variables before entering a state.

```java
	protected void doPreEntryActions(RequestControlContext context) throws FlowExecutionException {
		createVariables(context);
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
