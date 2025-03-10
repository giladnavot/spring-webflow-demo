---
title: The State class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="87:3:3" line-data="	protected State(Flow flow, String id) throws IllegalArgumentException {">`State`</SwmToken> in the Spring Web Flow project. We will cover:

1. What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="87:3:3" line-data="	protected State(Flow flow, String id) throws IllegalArgumentException {">`State`</SwmToken>
2. Variables and functions in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="87:3:3" line-data="	protected State(Flow flow, String id) throws IllegalArgumentException {">`State`</SwmToken>

# What is State

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="87:3:3" line-data="	protected State(Flow flow, String id) throws IllegalArgumentException {">`State`</SwmToken> class in <SwmPath>[spring-webflow/…/engine/State.java](spring-webflow/src/main/java/org/springframework/webflow/engine/State.java)</SwmPath> represents a point in a flow where something happens. The specific behavior of a state is determined by its type, such as action states, view states, subflow states, and end states. Each state is associated with exactly one owning flow definition, and subclasses of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="87:3:3" line-data="	protected State(Flow flow, String id) throws IllegalArgumentException {">`State`</SwmToken> capture all the configuration information needed for a specific kind of state. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="87:3:3" line-data="	protected State(Flow flow, String id) throws IllegalArgumentException {">`State`</SwmToken> class follows the classic <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="36:13:13" line-data=" * different behaviors is the classic GoF state pattern.">`GoF`</SwmToken> state pattern, allowing custom state types to execute different behaviors.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="77">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="87:3:3" line-data="	protected State(Flow flow, String id) throws IllegalArgumentException {">`State`</SwmToken> is a constructor that creates a state for the provided <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="78:18:18" line-data="	 * Creates a state for the provided &lt;code&gt;flow&lt;/code&gt; identified by the provided &lt;code&gt;id&lt;/code&gt;. The id must be">`flow`</SwmToken> identified by the provided <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="78:34:34" line-data="	 * Creates a state for the provided &lt;code&gt;flow&lt;/code&gt; identified by the provided &lt;code&gt;id&lt;/code&gt;. The id must be">`id`</SwmToken>. The id must be locally unique to the owning flow. The state will be automatically added to the flow.

```java
	/**
	 * Creates a state for the provided <code>flow</code> identified by the provided <code>id</code>. The id must be
	 * locally unique to the owning flow. The state will be automatically added to the flow.
	 * @param flow the owning flow
	 * @param id the state identifier (must be unique to the flow)
	 * @throws IllegalArgumentException if this state cannot be added to the flow, for instance when the provided id is
	 * not unique in the owning flow
	 * @see #getEntryActionList()
	 * @see #getExceptionHandlerSet()
	 */
	protected State(Flow flow, String id) throws IllegalArgumentException {
		setId(id);
		setFlow(flow);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="94">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="94:5:5" line-data="	public FlowDefinition getOwner() {">`getOwner`</SwmToken> returns the owning flow definition of the state.

```java
	public FlowDefinition getOwner() {
		return flow;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="98">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="98:5:5" line-data="	public String getId() {">`getId`</SwmToken> returns the unique identifier of the state within its owning flow.

```java
	public String getId() {
		return id;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="102">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="102:5:5" line-data="	public boolean isViewState() {">`isViewState`</SwmToken> returns `false` indicating that this state is not a view state by default.

```java
	public boolean isViewState() {
		return false;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="108">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="111:5:5" line-data="	public Flow getFlow() {">`getFlow`</SwmToken> returns the owning flow of the state.

```java
	/**
	 * Returns the owning flow.
	 */
	public Flow getFlow() {
		return flow;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="115">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="119:5:5" line-data="	private void setFlow(Flow flow) throws IllegalArgumentException {">`setFlow`</SwmToken> sets the owning flow of the state and ensures that the state is added to the flow.

```java
	/**
	 * Set the owning flow.
	 * @throws IllegalArgumentException if this state cannot be added to the flow
	 */
	private void setFlow(Flow flow) throws IllegalArgumentException {
		Assert.hasText(getId(), "The id of the state should be set before adding the state to a flow");
		Assert.notNull(flow, "The owning flow is required");
		this.flow = flow;
		flow.add(this);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="126">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="130:5:5" line-data="	private void setId(String id) {">`setId`</SwmToken> sets the unique identifier of the state within its owning flow.

```java
	/**
	 * Set the state identifier, unique to the owning flow.
	 * @param id the state identifier
	 */
	private void setId(String id) {
		Assert.hasText(id, "This state must have a valid identifier");
		this.id = id;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="135">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="139:5:5" line-data="	public ActionList getEntryActionList() {">`getEntryActionList`</SwmToken> returns the list of actions executed by this state when it is entered.

```java
	/**
	 * Returns the list of actions executed by this state when it is entered. The returned list is mutable.
	 * @return the state entry action list
	 */
	public ActionList getEntryActionList() {
		return entryActionList;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="143">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="151:5:5" line-data="	public FlowExecutionExceptionHandlerSet getExceptionHandlerSet() {">`getExceptionHandlerSet`</SwmToken> returns a mutable set of exception handlers for this state.

```java
	/**
	 * Returns a mutable set of exception handlers, allowing manipulation of how exceptions are handled when thrown
	 * within this state.
	 * <p>
	 * Exception handlers are invoked when an exception occurs when this state is entered, and can execute custom
	 * exception handling logic as well as select an error view to display.
	 * @return the state exception handler set
	 */
	public FlowExecutionExceptionHandlerSet getExceptionHandlerSet() {
		return exceptionHandlerSet;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="155">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="159:5:5" line-data="	public boolean isStartState() {">`isStartState`</SwmToken> returns a flag indicating if this state is the start state of its owning flow.

```java
	/**
	 * Returns a flag indicating if this state is the start state of its owning flow.
	 * @return true if the flow is the start state, false otherwise
	 */
	public boolean isStartState() {
		return flow.getStartState() == this;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="165">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="165:5:5" line-data="	public boolean equals(Object o) {">`equals`</SwmToken> checks if two states are equal based on their id and owning flow.

```java
	public boolean equals(Object o) {
		if (!(o instanceof State)) {
			return false;
		}
		State other = (State) o;
		return id.equals(other.id) && flow.equals(other.flow);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="173">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="173:5:5" line-data="	public int hashCode() {">`hashCode`</SwmToken> returns the hash code of the state based on its id and owning flow.

```java
	public int hashCode() {
		return id.hashCode() + flow.hashCode();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="179">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="187:7:7" line-data="	public final void enter(RequestControlContext context) throws FlowExecutionException {">`enter`</SwmToken> is used to enter this state in the provided flow control context. It executes the entry actions and calls the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="181:8:8" line-data="	 * {@link #doEnter(RequestControlContext)} hook method, which should be implemented by subclasses, after executing">`doEnter`</SwmToken> hook method.

```java
	/**
	 * Enter this state in the provided flow control context. This implementation just calls the
	 * {@link #doEnter(RequestControlContext)} hook method, which should be implemented by subclasses, after executing
	 * the entry actions.
	 * @param context the control context for the currently executing flow, used by this state to manipulate the flow
	 * execution
	 * @throws FlowExecutionException if an exception occurs in this state
	 */
	public final void enter(RequestControlContext context) throws FlowExecutionException {
		if (logger.isDebugEnabled()) {
			logger.debug("Entering state '" + getId() + "' of flow '" + getFlow().getId() + "'");
		}
		context.setCurrentState(this);
		doPreEntryActions(context);
		entryActionList.execute(context);
		doEnter(context);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="197">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="203:5:5" line-data="	protected void doPreEntryActions(RequestControlContext context) throws FlowExecutionException {">`doPreEntryActions`</SwmToken> is a hook method to execute before running state entry actions upon state entry. It does nothing by default and can be overridden by subclasses.

```java
	/**
	 * Hook method to execute before running state entry actions upon state entry. Does nothing by default. Subclasses
	 * may override.
	 * @param context the request control context
	 * @throws FlowExecutionException if an exception occurs
	 */
	protected void doPreEntryActions(RequestControlContext context) throws FlowExecutionException {

	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="207">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="214:7:7" line-data="	protected abstract void doEnter(RequestControlContext context) throws FlowExecutionException;">`doEnter`</SwmToken> is an abstract hook method to execute custom behavior as a result of entering this state. Subclasses must implement this method.

```java
	/**
	 * Hook method to execute custom behavior as a result of entering this state. By implementing this method subclasses
	 * specialize the behavior of the state.
	 * @param context the control context for the currently executing flow, used by this state to manipulate the flow
	 * execution
	 * @throws FlowExecutionException if an exception occurs in this state
	 */
	protected abstract void doEnter(RequestControlContext context) throws FlowExecutionException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="217">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="221:5:5" line-data="	public boolean handleException(FlowExecutionException exception, RequestControlContext context) {">`handleException`</SwmToken> handles an exception that occurred in this state during the context of the current flow execution request.

```java
	 * Handle an exception that occurred in this state during the context of the current flow execution request.
	 * @param exception the exception that occurred
	 * @param context the flow execution control context
	 */
	public boolean handleException(FlowExecutionException exception, RequestControlContext context) {
		return getExceptionHandlerSet().handleException(exception, context);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="225">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="225:5:5" line-data="	public String toString() {">`toString`</SwmToken> returns a string representation of the state, including its id, flow, entry action list, and exception handler set.

```java
	public String toString() {
		ToStringCreator creator = new ToStringCreator(this).append("id", getId()).append("flow", flow.getId())
				.append("entryActionList", entryActionList).append("exceptionHandlerSet", exceptionHandlerSet);
		appendToString(creator);
		return creator.toString();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="232">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="238:5:5" line-data="	protected void appendToString(ToStringCreator creator) {">`appendToString`</SwmToken> is a hook method that subclasses may override to print their internal state to a string. The default implementation does nothing.

```java
	/**
	 * Subclasses may override this hook method to print their internal state to a string. This default implementation
	 * does nothing.
	 * @param creator the toString creator, to print properties to string
	 * @see #toString()
	 */
	protected void appendToString(ToStringCreator creator) {
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" line="33">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" pos="26:4:4" line-data="public interface TargetStateResolver {">`TargetStateResolver`</SwmToken> interface, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" pos="36:1:1" line-data="	State resolveTargetState(Transition transition, State sourceState, RequestContext context);">`State`</SwmToken> class is used to resolve the target state of a transition. The method <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" pos="36:3:3" line-data="	State resolveTargetState(Transition transition, State sourceState, RequestContext context);">`resolveTargetState`</SwmToken> takes a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" pos="36:5:5" line-data="	State resolveTargetState(Transition transition, State sourceState, RequestContext context);">`Transition`</SwmToken>, a source <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" pos="36:1:1" line-data="	State resolveTargetState(Transition transition, State sourceState, RequestContext context);">`State`</SwmToken>, and a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" pos="36:15:15" line-data="	State resolveTargetState(Transition transition, State sourceState, RequestContext context);">`RequestContext`</SwmToken> as parameters and returns the target <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" pos="36:1:1" line-data="	State resolveTargetState(Transition transition, State sourceState, RequestContext context);">`State`</SwmToken>.

```java
	 * @param context the current request context
	 * @return the transition's target state - may be null if no state change should occur
	 */
	State resolveTargetState(Transition transition, State sourceState, RequestContext context);
}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="123">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="87:5:5" line-data="	protected State(Flow flow, String id) throws IllegalArgumentException {">`Flow`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="126:5:5" line-data="	private Set&lt;State&gt; states = new LinkedHashSet&lt;&gt;(9);">`State`</SwmToken> is used to define the set of state definitions for the flow. It also specifies the default start state for the flow.

```java
	/**
	 * The set of state definitions for this flow.
	 */
	private Set<State> states = new LinkedHashSet<>(9);

	/**
	 * The default start state for this flow.
	 */
	private State startState;

	/**
	 * The set of flow variables created by this flow.
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="48">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="52:10:10" line-data="	 * @see State#enter(RequestControlContext)">`RequestControlContext`</SwmToken> interface, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="50:11:11" line-data="	 * new state by the State type itself.">`State`</SwmToken> class is used to record the current state that has been entered in the executing flow. The method <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="54:3:3" line-data="	void setCurrentState(State state);">`setCurrentState`</SwmToken> is called as part of entering a new state by the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="50:11:11" line-data="	 * new state by the State type itself.">`State`</SwmToken> type itself.

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

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/EndState.java" line="43">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/EndState.java" pos="46:4:4" line-data="public class EndState extends State {">`EndState`</SwmToken> class extends the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/EndState.java" pos="46:8:8" line-data="public class EndState extends State {">`State`</SwmToken> class and represents the final state of a flow execution. It includes a renderer that will render the final response when a flow execution terminates.

```java
 * @author Colin Sampaleanu
 * @author Erwin Vervaet
 */
public class EndState extends State {

	/**
	 * The renderer that will render the final response when a flow execution terminates.
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="208">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" pos="36:5:5" line-data="	State resolveTargetState(Transition transition, State sourceState, RequestContext context);">`Transition`</SwmToken> class, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="211:7:7" line-data="	public boolean execute(State sourceState, RequestControlContext context) throws FlowExecutionException {">`State`</SwmToken> class is used to execute a transition from a source state to a target state. The method <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="211:5:5" line-data="	public boolean execute(State sourceState, RequestControlContext context) throws FlowExecutionException {">`execute`</SwmToken> takes a source <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="211:7:7" line-data="	public boolean execute(State sourceState, RequestControlContext context) throws FlowExecutionException {">`State`</SwmToken> and a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="211:12:12" line-data="	public boolean execute(State sourceState, RequestControlContext context) throws FlowExecutionException {">`RequestControlContext`</SwmToken> as parameters and performs the transition.

```java
	 * enter
	 * @throws FlowExecutionException when transition execution fails
	 */
	public boolean execute(State sourceState, RequestControlContext context) throws FlowExecutionException {
		if (canExecute(context)) {
			if (logger.isDebugEnabled()) {
				logger.debug("Executing " + this);
			}
			context.setCurrentTransition(this);
			if (targetStateResolver != null) {
				State targetState = targetStateResolver.resolveTargetState(this, sourceState, context);
				if (targetState != null) {
					if (sourceState != null) {
						if (logger.isDebugEnabled()) {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" line="76">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" pos="48:4:4" line-data="public class FlowArtifactFactory {">`FlowArtifactFactory`</SwmToken> class, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" pos="79:18:18" line-data="	 * @param attributes attributes to assign to the State, which may also be used to affect state construction; may be">`State`</SwmToken> class is used to create and initialize various state instances, such as view states, with specific attributes and actions.

```java
	 * @param transitions any transitions (paths) out of this state; may be null
	 * @param exceptionHandlers any exception handlers; may be null
	 * @param exitActions any state exit actions; may be null
	 * @param attributes attributes to assign to the State, which may also be used to affect state construction; may be
	 * null
	 * @return the fully initialized view state instance
	 */
	public State createViewState(String id, Flow flow, ViewVariable[] variables, Action[] entryActions,
			ViewFactory viewFactory, Boolean redirect, boolean popup, Action[] renderActions, Transition[] transitions,
			FlowExecutionExceptionHandler[] exceptionHandlers, Action[] exitActions, AttributeMap<?> attributes) {
		ViewState viewState = new ViewState(flow, id, viewFactory);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="30">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="33:6:6" line-data="public abstract class TransitionableState extends State implements TransitionableStateDefinition {">`TransitionableState`</SwmToken> class extends the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="33:10:10" line-data="public abstract class TransitionableState extends State implements TransitionableStateDefinition {">`State`</SwmToken> class and defines the set of possible transitions out of this state. It serves as a base class for states that can transition to other states.

```java
 * @author Keith Donald
 * @author Erwin Vervaet
 */
public abstract class TransitionableState extends State implements TransitionableStateDefinition {

	/**
	 * The set of possible transitions out of this state.
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="369">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowSessionImpl.java" pos="187:6:6" line-data="	 * @see FlowExecutionImpl#setCurrentState(State)">`FlowExecutionImpl`</SwmToken> class, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="372:5:5" line-data="	void setCurrentState(State newState, RequestContext context) {">`State`</SwmToken> class is used to manage the current state of the flow execution. Methods like <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="372:3:3" line-data="	void setCurrentState(State newState, RequestContext context) {">`setCurrentState`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="393:3:3" line-data="	boolean execute(Transition transition, RequestControlContext context) {">`execute`</SwmToken> handle state transitions and state management within the flow execution.

```java
		listeners.fireSessionStarted(context, session);
	}

	void setCurrentState(State newState, RequestContext context) {
		listeners.fireStateEntering(context, newState);
		FlowSessionImpl session = getActiveSessionInternal();
		State previousState = (State) session.getState();
		session.setCurrentState(newState);
		listeners.fireStateEntered(context, previousState);
	}

	public void viewRendering(View view, RequestContext context) {
		listeners.fireViewRendering(context, view);
	}

	public void viewRendered(View view, RequestContext context) {
		listeners.fireViewRendered(context, view);
	}

	boolean handleEvent(Event event, RequestControlContext context) {
		listeners.fireEventSignaled(context, event);
		return getActiveSessionInternal().getFlow().handleEvent(context);
	}

	boolean execute(Transition transition, RequestControlContext context) {
		listeners.fireTransitionExecuting(context, transition);
		return transition.execute((State) getActiveSession().getState(), context);
	}

	void endActiveFlowSession(String outcome, MutableAttributeMap<Object> output, RequestControlContext context) {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/support/DefaultTargetStateResolver.java" line="54">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/support/DefaultTargetStateResolver.java" pos="33:4:4" line-data="public class DefaultTargetStateResolver implements TargetStateResolver {">`DefaultTargetStateResolver`</SwmToken> class, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/support/DefaultTargetStateResolver.java" pos="57:3:3" line-data="	public State resolveTargetState(Transition transition, State sourceState, RequestContext context) {">`State`</SwmToken> class is used to resolve the target state based on a given transition, source state, and request context. The method <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/support/DefaultTargetStateResolver.java" pos="57:5:5" line-data="	public State resolveTargetState(Transition transition, State sourceState, RequestContext context) {">`resolveTargetState`</SwmToken> retrieves the target state ID and returns the corresponding <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/support/DefaultTargetStateResolver.java" pos="57:3:3" line-data="	public State resolveTargetState(Transition transition, State sourceState, RequestContext context) {">`State`</SwmToken> instance.

```java
		this.targetStateIdExpression = targetStateIdExpression;
	}

	public State resolveTargetState(Transition transition, State sourceState, RequestContext context) {
		String targetStateId = (String) targetStateIdExpression.getValue(context);
		if (targetStateId != null) {
			return ((Flow) context.getActiveFlow()).getStateInstance(targetStateId);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowSessionImpl.java" line="56">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowSessionImpl.java" pos="69:3:3" line-data="	private FlowSessionImpl parent;">`FlowSessionImpl`</SwmToken> class, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowSessionImpl.java" pos="59:5:5" line-data="	private transient State state;">`State`</SwmToken> class is used to manage the current state of the flow session. Methods like <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowSessionImpl.java" pos="139:5:5" line-data="	public void setCurrentState(State state) {">`setCurrentState`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowSessionImpl.java" pos="190:3:3" line-data="	void setState(State state) {">`setState`</SwmToken> handle state transitions and ensure the state belongs to the associated flow.

```java
	 * <p>
	 * Transient to support restoration by the {@link FlowExecutionImplFactory}.
	 */
	private transient State state;

	/**
	 * The session data model ("flow scope").
	 */
	private MutableAttributeMap<Object> scope = new LocalAttributeMap<>();

	/**
	 * The parent session of this session (may be <code>null</code> if this is a root session.)
	 */
	private FlowSessionImpl parent;

	/**
	 * Set so the transient {@link #flow} field can be restored by the {@link FlowExecutionImplFactory}.
	 */
	private String flowId;

	/**
	 * Set so the transient {@link #state} field can be restored by the {@link FlowExecutionImplFactory}.
	 */
	private String stateId;

	/**
	 * Default constructor required for externalizable serialization. Should NOT be called programmatically.
	 */
	public FlowSessionImpl() {
	}

	/**
	 * Create a new flow session.
	 * @param flow the flow definition associated with this flow session
	 * @param parent this session's parent (may be null)
	 */
	public FlowSessionImpl(Flow flow, FlowSessionImpl parent) {
		Assert.notNull(flow, "The flow is required");
		this.flow = flow;
		this.parent = parent;
	}

	// implementing FlowSession

	public FlowDefinition getDefinition() {
		return flow;
	}

	public StateDefinition getState() {
		return state;
	}

	public MutableAttributeMap<Object> getScope() {
		return scope;
	}

	@SuppressWarnings("unchecked")
	public MutableAttributeMap<Object> getViewScope() throws IllegalStateException {
		if (state == null) {
			throw new IllegalStateException("The current state of this flow '" + flow.getId()
					+ "' is [null] - cannot access view scope");
		}
		if (!state.isViewState()) {
			throw new IllegalStateException("The current state '" + state.getId() + "' of this flow '" + flow.getId()
					+ "' is not a view state - view scope not accessible");
		}
		return (MutableAttributeMap<Object>) scope.get(VIEW_SCOPE_ATTRIBUTE);
	}

	public boolean isEmbeddedMode() {
		return (Boolean) scope.get(EMBEDDED_MODE_ATTRIBUTE, false);
	}

	public FlowSession getParent() {
		return parent;
	}

	public boolean isRoot() {
		return parent == null;
	}

	// public impl

	public void setCurrentState(State state) {
		if (this.state != null && this.state.isViewState()) {
			destroyViewScope();
		}
		this.state = state;
		if (this.state.isViewState()) {
			initViewScope();
		}
	}

	// custom serialization

	@SuppressWarnings("unchecked")
	public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
		flowId = (String) in.readObject();
		stateId = (String) in.readObject();
		scope = (MutableAttributeMap<Object>) in.readObject();
		parent = (FlowSessionImpl) in.readObject();
	}

	public void writeExternal(ObjectOutput out) throws IOException {
		out.writeObject(flow.getId());
		out.writeObject(state != null ? state.getId() : null);
		out.writeObject(scope);
		out.writeObject(parent);
	}

	// package-private

	Flow getFlow() {
		return flow;
	}

	// package private setters used by FlowExecutionImplFactory for setting/updating internal state

	/**
	 * Restores the definition of this flow session.
	 * @param flow the flow sessions definition
	 * @see FlowExecutionImplStateRestorer
	 */
	void setFlow(Flow flow) {
		Assert.notNull(flow, "The flow is required");
		this.flow = flow;
	}

	/**
	 * Set the current state of this flow session.
	 * @param state the state that is currently active in this flow session
	 * @see FlowExecutionImpl#setCurrentState(State)
	 * @see FlowExecutionImplStateRestorer
	 */
	void setState(State state) {
		Assert.notNull(state, "The state is required");
		Assert.isTrue(flow == state.getOwner(),
				"The state does not belong to the flow associated with this flow session");
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
