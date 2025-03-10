---
title: Exploring Flow Execution
---
# Exploring Flow Execution

Flow execution in Spring Web Flow refers to the process of running an instance of a flow definition. It is a central interface for manipulating an instance of a flow definition.

## FlowExecution Interface

The `FlowExecution` interface provides methods to start and resume the flow execution. When the `start` method is called, the execution status can either be 'paused' or 'ended'. If the flow execution is paused, it can be resumed using the `resume` method.

## FlowExecutionKeyFactory

The `FlowExecutionKeyFactory` is responsible for creating keys that provide a persistent identity for a flow execution. This factory generates the key but does not perform the key assignment.

## Managing Snapshots

The `FlowExecutionKeyFactory` also manages the snapshots of the flow execution. It can update, remove, or remove all snapshots associated with a flow execution.

## <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/Action.java" pos="63:12:12" line-data="	 * Note: The {@link RequestContext} argument to this method provides access to data about the active flow execution">`RequestContext`</SwmToken> Interface

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/Action.java" pos="63:12:12" line-data="	 * Note: The {@link RequestContext} argument to this method provides access to data about the active flow execution">`RequestContext`</SwmToken> interface provides a context for a single request to manipulate a flow execution. It allows access to contextual information about the executing request and the active flow execution.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/Action.java" line="53">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/Action.java" pos="86:22:22" line-data="	 * such result collections in request scope, and ensure you execute this action again each time you wish to view">`execute`</SwmToken> method in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/Action.java" pos="53:4:4" line-data="public interface Action {">`Action`</SwmToken> interface is a key endpoint for executing a behavior within the context of a request associated with an active flow execution. This method is typically triggered by a state within a flow carrying out the execution of a flow definition.

```java
public interface Action {

	/**
	 * Execute this action. Action execution will occur in the context of a request associated with an active flow
	 * execution.
	 * <p>
	 * Action invocation is typically triggered in a production environment by a state within a flow carrying out the
	 * execution of a flow definition. The result of action execution, a logical outcome event, can be used as grounds
	 * for a transition out of the calling state.
	 * <p>
	 * Note: The {@link RequestContext} argument to this method provides access to data about the active flow execution
	 * in the context of the currently executing thread. Among other things, this allows this action to access
	 * {@link RequestContext#getRequestScope() data} set by other actions, as well as set its own attributes it wishes
	 * to expose in a given scope.
	 * <p>
	 * Some notes about actions and their usage of the attribute scope types:
	 * <ul>
	 * <li>Attributes set in {@link RequestContext#getRequestScope() request scope} exist for the life of the currently
	 * executing request only.
	 * <li>Attributes set in {@link RequestContext#getFlashScope() flash scope} exist until after view rendering is
	 * completed. That time includes the current request plus any redirect required for the view render to complete.
	 * <li>Attributes set in {@link RequestContext#getFlowScope() flow scope} exist for the life of the flow session and
	 * will be cleaned up automatically when the flow session ends.
	 * <li>Attributes set in {@link RequestContext#getConversationScope() conversation scope} exist for the life of the
	 * entire flow execution representing a single logical "conversation" with a user.
	 * </ul>
	 * <p>
	 * All attributes present in any scope are typically exposed in a model for access by a view when an "interactive"
	 * state type such as a view state is entered.
	 * <p>
	 * Note: flow scope should generally not be used as a general purpose cache, but rather as a context for data needed
	 * locally by other states of the flow this action participates in. For example, it would be inappropriate to stuff
	 * large collections of objects (like those returned to support a search results view) into flow scope. Instead, put
	 * such result collections in request scope, and ensure you execute this action again each time you wish to view
	 * those results. 2nd level caches managed outside of SWF are more general cache solutions.
	 * <p>
	 * Note: as flow scoped attributes are eligible for serialization they should be <code>Serializable</code>.
	 * 
	 * @param context the action execution context, for accessing and setting data in a {@link ScopeType scope type}, as
	 * well as obtaining other flow contextual information (e.g. request context attributes and flow execution context
	 * information)
	 * @return a logical result outcome, used as grounds for a transition in the calling flow (e.g. "success", "error",
	 * "yes", "no", * ...)
	 * @throws Exception a exception occurred during action execution, either checked or unchecked; note, any
	 * <i>recoverable</i> exceptions should be caught within this method and an appropriate result outcome returned
	 * <i>or</i> be handled by the current state of the calling flow execution.
	 */
	Event execute(RequestContext context) throws Exception;
}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
