---
title: The TransitionableState class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="54:3:3" line-data="	protected TransitionableState(Flow flow, String id) throws IllegalArgumentException {">`TransitionableState`</SwmToken> in the Spring Web Flow project. We will discuss:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="54:3:3" line-data="	protected TransitionableState(Flow flow, String id) throws IllegalArgumentException {">`TransitionableState`</SwmToken> is.
2. The variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="54:3:3" line-data="	protected TransitionableState(Flow flow, String id) throws IllegalArgumentException {">`TransitionableState`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="54:3:3" line-data="	protected TransitionableState(Flow flow, String id) throws IllegalArgumentException {">`TransitionableState`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="54:3:3" line-data="	protected TransitionableState(Flow flow, String id) throws IllegalArgumentException {">`TransitionableState`</SwmToken> class is an abstract superclass for states that can execute a transition in response to an event. It is used within the Spring Web Flow framework to manage state transitions within a flow. This class provides the foundational behavior for states that can transition to other states based on events.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="45">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="54:3:3" line-data="	protected TransitionableState(Flow flow, String id) throws IllegalArgumentException {">`TransitionableState`</SwmToken> is a constructor that initializes a new transitionable state with a given flow and state identifier. It ensures that the state identifier is unique within the flow.

```java
	/**
	 * Create a new transitionable state.
	 * @param flow the owning flow
	 * @param id the state identifier (must be unique to the flow)
	 * @throws IllegalArgumentException when this state cannot be added to given flow, for instance when the id is not
	 * unique
	 * @see State#State(Flow, String)
	 * @see #getTransitionSet()
	 */
	protected TransitionableState(Flow flow, String id) throws IllegalArgumentException {
		super(flow, id);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="60">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="60:7:7" line-data="	public TransitionDefinition[] getTransitions() {">`getTransitions`</SwmToken> returns an array of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="60:3:3" line-data="	public TransitionDefinition[] getTransitions() {">`TransitionDefinition`</SwmToken> objects representing the possible transitions out of this state.

```java
	public TransitionDefinition[] getTransitions() {
		return getTransitionSet().toArray();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="64">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="64:5:5" line-data="	public TransitionDefinition getTransition(String eventId) {">`getTransition`</SwmToken> retrieves a specific transition based on the provided event ID. It iterates through the transitions set to find a match.

```java
	public TransitionDefinition getTransition(String eventId) {
		for (Transition transition : transitions) {
			if (transition.getId().equals(eventId)) {
				return transition;
			}
		}
		return null;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="75">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="78:5:5" line-data="	public TransitionSet getTransitionSet() {">`getTransitionSet`</SwmToken> returns the set of transitions associated with this state. The returned set is mutable.

```java
	/**
	 * Returns the set of transitions. The returned set is mutable.
	 */
	public TransitionSet getTransitionSet() {
		return transitions;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="87">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="87:5:5" line-data="	public Transition getRequiredTransition(RequestContext context) throws NoMatchingTransitionException {">`getRequiredTransition`</SwmToken> retrieves a transition for the given flow execution request context. It throws a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="87:14:14" line-data="	public Transition getRequiredTransition(RequestContext context) throws NoMatchingTransitionException {">`NoMatchingTransitionException`</SwmToken> if no matching transition is found.

```java
	public Transition getRequiredTransition(RequestContext context) throws NoMatchingTransitionException {
		Transition transition = getTransitionSet().getTransition(context);
		if (transition == null) {
			throw new NoMatchingTransitionException(getFlow().getId(), getId(), context.getCurrentEvent(),
					"No transition found on occurence of event '" + context.getCurrentEvent() + "' in state '"
							+ getId() + "' of flow '" + getFlow().getId() + "' -- valid transitional criteria are "
							+ StylerUtils.style(getTransitionSet().getTransitionCriterias())
							+ " -- likely programmer error, check the set of TransitionCriteria for this state");
		}
		return transition;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="99">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="103:5:5" line-data="	public ActionList getExitActionList() {">`getExitActionList`</SwmToken> returns the list of actions executed by this state when it is exited. The returned list is mutable.

```java
	/**
	 * Returns the list of actions executed by this state when it is exited. The returned list is mutable.
	 * @return the state exit action list
	 */
	public ActionList getExitActionList() {
		return exitActionList;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="115">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="115:5:5" line-data="	public boolean handleEvent(RequestControlContext context) throws NoMatchingTransitionException {">`handleEvent`</SwmToken> informs this state definition that an event was signaled in it. It executes the required transition based on the current event in the request context.

```java
	public boolean handleEvent(RequestControlContext context) throws NoMatchingTransitionException {
		return context.execute(getRequiredTransition(context));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="119">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="121:15:15" line-data="	 * By default just executes any registered exit actions.">`exit`</SwmToken> is called when a transition takes the flow out of this state into another state. It executes any registered exit actions.

```java
	/**
	 * Exit this state. This is typically called when a transition takes the flow out of this state into another state.
	 * By default just executes any registered exit actions.
	 * @param context the flow control context
	 */
	public void exit(RequestControlContext context) {
		exitActionList.execute(context);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="128">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="128:5:5" line-data="	protected void appendToString(ToStringCreator creator) {">`appendToString`</SwmToken> appends the transitions and exit action list to the string representation of this state.

```java
	protected void appendToString(ToStringCreator creator) {
		creator.append("transitions", transitions).append("exitActionList", exitActionList);
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="224">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="65:4:4" line-data="		for (Transition transition : transitions) {">`Transition`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="224:8:8" line-data="						if (sourceState instanceof TransitionableState) {">`TransitionableState`</SwmToken> is used to handle the exit of a state. When a state transition occurs, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="225:9:9" line-data="							((TransitionableState) sourceState).exit(context);">`exit`</SwmToken> method of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="224:8:8" line-data="						if (sourceState instanceof TransitionableState) {">`TransitionableState`</SwmToken> is called to perform any necessary cleanup or actions before leaving the state.

```java
						if (sourceState instanceof TransitionableState) {
							((TransitionableState) sourceState).exit(context);
						}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/DecisionState.java" line="29">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/DecisionState.java" pos="29:4:4" line-data="public class DecisionState extends TransitionableState {">`DecisionState`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/DecisionState.java" pos="29:8:8" line-data="public class DecisionState extends TransitionableState {">`TransitionableState`</SwmToken>, indicating that it inherits the properties and behaviors of a transitionable state. This allows <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/DecisionState.java" pos="29:4:4" line-data="public class DecisionState extends TransitionableState {">`DecisionState`</SwmToken> to participate in state transitions within a flow.

```java
public class DecisionState extends TransitionableState {

	/**
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" line="223">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" pos="48:4:4" line-data="public class FlowArtifactFactory {">`FlowArtifactFactory`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" pos="223:7:7" line-data="	private void configureCommonProperties(TransitionableState state, Action[] entryActions, Transition[] transitions,">`TransitionableState`</SwmToken> is configured with common properties such as entry actions, transitions, exception handlers, exit actions, and attributes. This setup ensures that the state is properly initialized and ready for transitions.

```java
	private void configureCommonProperties(TransitionableState state, Action[] entryActions, Transition[] transitions,
			FlowExecutionExceptionHandler[] exceptionHandlers, Action[] exitActions, AttributeMap<?> attributes) {
		configureCommonProperties(state, entryActions, exceptionHandlers, attributes);
		state.getTransitionSet().addAll(transitions);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="318">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="51:10:10" line-data="	 * @see State#State(Flow, String)">`Flow`</SwmToken> class provides a method to retrieve a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="318:3:3" line-data="	public TransitionableState getTransitionableState(String stateId) throws IllegalArgumentException,">`TransitionableState`</SwmToken> by its state ID. This method ensures that the state is transitionable and throws exceptions if the state cannot be found or is not transitionable.

```java
	public TransitionableState getTransitionableState(String stateId) throws IllegalArgumentException,
			ClassCastException {
		State state = getStateInstance(stateId);
		if (state != null && !(state instanceof TransitionableState)) {
			throw new ClassCastException("The state '" + stateId + "' of flow '" + getId() + "' must be transitionable");
		}
		return (TransitionableState) state;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="443">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="73:4:4" line-data="public class FlowExecutionImpl implements FlowExecution, Externalizable {">`FlowExecutionImpl`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="443:1:1" line-data="		TransitionableState currentState = (TransitionableState) session.getState();">`TransitionableState`</SwmToken> is used to get the current state of a session and retrieve the transition definition for a given event ID. This allows the flow execution to determine the next state based on the event.

```java
		TransitionableState currentState = (TransitionableState) session.getState();
		TransitionDefinition transition = currentState.getTransition(eventId);
		if (transition == null) {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/SubflowState.java" line="41">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/SubflowState.java" pos="41:4:4" line-data="public class SubflowState extends TransitionableState {">`SubflowState`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/SubflowState.java" pos="41:8:8" line-data="public class SubflowState extends TransitionableState {">`TransitionableState`</SwmToken>, indicating that it can spawn a subflow when entered. This allows for nested flows within a larger flow, providing modularity and reusability of flow logic.

```java
public class SubflowState extends TransitionableState {

	/**
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/ActionState.java" line="44">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ActionState.java" pos="44:4:4" line-data="public class ActionState extends TransitionableState {">`ActionState`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ActionState.java" pos="44:8:8" line-data="public class ActionState extends TransitionableState {">`TransitionableState`</SwmToken> and includes a list of actions to be executed when the state is entered. This allows for specific actions to be performed as part of the state transition process.

```java
public class ActionState extends TransitionableState {

	/**
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" line="41">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" pos="41:4:4" line-data="public class ViewState extends TransitionableState {">`ViewState`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" pos="41:8:8" line-data="public class ViewState extends TransitionableState {">`TransitionableState`</SwmToken> and includes a list of actions to be executed before the view is rendered. This ensures that any necessary preparations are made before displaying the view to the user.

```java
public class ViewState extends TransitionableState {

	/**
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
