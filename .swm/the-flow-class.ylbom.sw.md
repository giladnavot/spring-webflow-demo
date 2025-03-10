---
title: The Flow class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="180:3:3" line-data="	public Flow(String id) {">`Flow`</SwmToken> in the Spring Web Flow project. We will explain:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="180:3:3" line-data="	public Flow(String id) {">`Flow`</SwmToken> is and its purpose.
2. The variables and functions defined in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="180:3:3" line-data="	public Flow(String id) {">`Flow`</SwmToken> class.

# What is Flow

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="180:3:3" line-data="	public Flow(String id) {">`Flow`</SwmToken> class in <SwmPath>[spring-webflow/…/engine/Flow.java](spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java)</SwmPath> is a reusable, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="46:25:27" line-data=" * A single flow definition. A Flow definition is a reusable, self-contained controller module that provides the blue">`self-contained`</SwmToken> controller module that provides the blueprint for a user dialog or conversation. Flows typically drive controlled navigations within web applications to guide users through the fulfillment of a business process or goal that takes place over a series of steps, modeled as states. A simple <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="180:3:3" line-data="	public Flow(String id) {">`Flow`</SwmToken> definition could execute an action and display a view in one request, while a more elaborate <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="180:3:3" line-data="	public Flow(String id) {">`Flow`</SwmToken> definition may be <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="52:13:15" line-data=" * elaborate Flow definition may be long-lived and execute across a series of requests, invoking many possible paths,">`long-lived`</SwmToken> and execute across a series of requests, invoking many possible paths, actions, and subflows.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="176">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="180:3:3" line-data="	public Flow(String id) {">`Flow`</SwmToken> constructs a new flow definition with the given id. The id should be unique among all flows.

```java
	/**
	 * Construct a new flow definition with the given id. The id should be unique among all flows.
	 * @param id the flow identifier
	 */
	public Flow(String id) {
		Assert.hasText(id, "This flow must be uniquely identified");
		this.id = id;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="188">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="193:7:7" line-data="	public static Flow create(String id, AttributeMap&lt;?&gt; attributes) {">`create`</SwmToken> creates a new flow with the given id and attributes.

```java
	 * Create a new flow with the given id and attributes.
	 * @param id the flow id
	 * @param attributes the attributes
	 * @return the flow
	 */
	public static Flow create(String id, AttributeMap<?> attributes) {
		Flow flow = new Flow(id);
		flow.getAttributes().putAll(attributes);
		return flow;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="201">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="201:5:5" line-data="	public String getId() {">`getId`</SwmToken> returns the id of the flow.

```java
	public String getId() {
		return id;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="205">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="205:5:5" line-data="	public StateDefinition getStartState() {">`getStartState`</SwmToken> returns the start state of the flow.

```java
	public StateDefinition getStartState() {
		if (startState == null) {
			throw new IllegalStateException("No start state has been set for this flow ('" + getId()
					+ "') -- flow builder configuration error?");
		}
		return startState;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="213">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="213:5:5" line-data="	public StateDefinition getState(String stateId) {">`getState`</SwmToken> returns the state definition for the given state id.

```java
	public StateDefinition getState(String stateId) {
		return getStateInstance(stateId);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="217">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="217:7:7" line-data="	public String[] getPossibleOutcomes() {">`getPossibleOutcomes`</SwmToken> returns the possible outcomes of the flow.

```java
	public String[] getPossibleOutcomes() {
		List<String> possibleOutcomes = new ArrayList<>();
		for (State state : states) {
			if (state instanceof EndState) {
				possibleOutcomes.add(state.getId());
			}
		}
		return possibleOutcomes.toArray(new String[possibleOutcomes.size()]);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="227">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="227:5:5" line-data="	public ClassLoader getClassLoader() {">`getClassLoader`</SwmToken> returns the class loader of the flow.

```java
	public ClassLoader getClassLoader() {
		if (applicationContext != null) {
			return applicationContext.getClassLoader();
		} else {
			return ClassUtils.getDefaultClassLoader();
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="235">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="235:5:5" line-data="	public ApplicationContext getApplicationContext() {">`getApplicationContext`</SwmToken> returns the application context of the flow.

```java
	public ApplicationContext getApplicationContext() {
		return applicationContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="239">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="239:5:5" line-data="	public boolean inDevelopment() {">`inDevelopment`</SwmToken> checks if the flow is in development mode.

```java
	public boolean inDevelopment() {
		return getAttributes().getBoolean("development", false);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="243">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="246:14:14" line-data="	 * @param state the state to add">`add`</SwmToken> adds a state definition to the flow.

```java
	/**
	 * Add given state definition to this flow definition. Marked protected, as this method is to be called by the
	 * (privileged) state definition classes themselves during state construction as part of a FlowBuilder invocation.
	 * @param state the state to add
	 * @throws IllegalArgumentException when the state cannot be added to the flow; for instance if another state shares
	 * the same id as the one provided or if given state already belongs to another flow
	 */
	protected void add(State state) throws IllegalArgumentException {
		if (this != state.getFlow() && state.getFlow() != null) {
			throw new IllegalArgumentException("State " + state + " cannot be added to this flow '" + getId()
					+ "' -- it already belongs to a different flow: '" + state.getFlow().getId() + "'");
		}
		if (this.states.contains(state) || this.containsState(state.getId())) {
			throw new IllegalArgumentException("This flow '" + getId() + "' already contains a state with id '"
					+ state.getId() + "' -- state ids must be locally unique to the flow definition; "
					+ "existing state-ids of this flow include: " + StylerUtils.style(getStateIds()));
		}
		boolean firstAdd = states.isEmpty();
		states.add(state);
		if (firstAdd) {
			setStartState(state);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="267">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="271:5:5" line-data="	public int getStateCount() {">`getStateCount`</SwmToken> returns the number of states defined in the flow.

```java
	/**
	 * Returns the number of states defined in this flow.
	 * @return the state count
	 */
	public int getStateCount() {
		return states.size();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="275">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="280:5:5" line-data="	public boolean containsState(String stateId) {">`containsState`</SwmToken> checks if a state with the provided id is present in the flow.

```java
	/**
	 * Is a state with the provided id present in this flow?
	 * @param stateId the state id
	 * @return true if yes, false otherwise
	 */
	public boolean containsState(String stateId) {
		for (State state : states) {
			if (state.getId().equals(stateId)) {
				return true;
			}
		}
		return false;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="289">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="295:5:5" line-data="	public void setStartState(String stateId) throws IllegalArgumentException {">`setStartState`</SwmToken> sets the start state for the flow to the state with the provided state id.

```java
	/**
	 * Set the start state for this flow to the state with the provided <code>stateId</code>; a state must exist by the
	 * provided <code>stateId</code>.
	 * @param stateId the id of the new start state
	 * @throws IllegalArgumentException when no state exists with the id you provided
	 */
	public void setStartState(String stateId) throws IllegalArgumentException {
		setStartState(getStateInstance(stateId));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="299">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="304:5:5" line-data="	public void setStartState(State state) throws IllegalArgumentException {">`setStartState`</SwmToken> sets the start state for the flow to the provided state.

```java
	/**
	 * Set the start state for this flow to the state provided; any state may be the start state.
	 * @param state the new start state
	 * @throws IllegalArgumentException given state has not been added to this flow
	 */
	public void setStartState(State state) throws IllegalArgumentException {
		if (!states.contains(state)) {
			throw new IllegalArgumentException("State '" + state + "' is not a state of flow '" + getId() + "'");
		}
		startState = state;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="311">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="318:5:5" line-data="	public TransitionableState getTransitionableState(String stateId) throws IllegalArgumentException,">`getTransitionableState`</SwmToken> returns the transitionable state with the given state id.

```java
	/**
	 * Return the <code>TransitionableState</code> with given <code>stateId</code>.
	 * @param stateId id of the state to look up
	 * @return the transitionable state
	 * @throws IllegalArgumentException if the identified state cannot be found
	 * @throws ClassCastException when the identified state is not transitionable
	 */
	public TransitionableState getTransitionableState(String stateId) throws IllegalArgumentException,
			ClassCastException {
		State state = getStateInstance(stateId);
		if (state != null && !(state instanceof TransitionableState)) {
			throw new ClassCastException("The state '" + stateId + "' of flow '" + getId() + "' must be transitionable");
		}
		return (TransitionableState) state;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="327">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="333:5:5" line-data="	public State getStateInstance(String stateId) throws IllegalArgumentException {">`getStateInstance`</SwmToken> looks up the identified state instance of the flow.

```java
	/**
	 * Lookup the identified state instance of this flow.
	 * @param stateId the state id
	 * @return the state
	 * @throws IllegalArgumentException if the identified state cannot be found
	 */
	public State getStateInstance(String stateId) throws IllegalArgumentException {
		if (!StringUtils.hasText(stateId)) {
			throw new IllegalArgumentException("The specified stateId is invalid: state identifiers must be non-blank");
		}
		for (State state : states) {
			if (state.getId().equals(stateId)) {
				return state;
			}
		}
		throw new IllegalArgumentException("Cannot find state with id '" + stateId + "' in flow '" + getId() + "' -- "
				+ "Known state ids are '" + StylerUtils.style(getStateIds()) + "'");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="346">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="351:7:7" line-data="	public String[] getStateIds() {">`getStateIds`</SwmToken> returns an ordered array of the state ids for the state definitions associated with the flow.

```java
	/**
	 * Convenience accessor that returns an ordered array of the String <code>ids</code> for the state definitions
	 * associated with this flow definition.
	 * @return the state ids
	 */
	public String[] getStateIds() {
		String[] stateIds = new String[getStateCount()];
		int i = 0;
		for (State state : states) {
			stateIds[i++] = state.getId();
		}
		return stateIds;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="360">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="364:5:5" line-data="	public void addVariable(FlowVariable variable) {">`addVariable`</SwmToken> adds a flow variable.

```java
	/**
	 * Adds a flow variable.
	 * @param variable the variable
	 */
	public void addVariable(FlowVariable variable) {
		variables.put(variable.getName(), variable);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="368">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="372:5:5" line-data="	public void addVariables(FlowVariable... variables) {">`addVariables`</SwmToken> adds flow variables.

```java
	/**
	 * Adds flow variables.
	 * @param variables the variables
	 */
	public void addVariables(FlowVariable... variables) {
		if (variables == null) {
			return;
		}
		for (FlowVariable variable : variables) {
			addVariable(variable);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="381">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="385:5:5" line-data="	public FlowVariable getVariable(String name) {">`getVariable`</SwmToken> returns the flow variable with the given name.

```java
	/**
	 * Returns the flow variable with the given name.
	 * @param name the name of the variable
	 */
	public FlowVariable getVariable(String name) {
		return variables.get(name);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="389">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="392:7:7" line-data="	public FlowVariable[] getVariables() {">`getVariables`</SwmToken> returns the flow variables.

```java
	/**
	 * Returns the flow variables.
	 */
	public FlowVariable[] getVariables() {
		return variables.values().toArray(new FlowVariable[variables.size()]);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="396">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="400:5:5" line-data="	public Mapper getInputMapper() {">`getInputMapper`</SwmToken> returns the configured flow input mapper, or null if none.

```java
	/**
	 * Returns the configured flow input mapper, or null if none.
	 * @return the input mapper
	 */
	public Mapper getInputMapper() {
		return inputMapper;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="404">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="408:5:5" line-data="	public void setInputMapper(Mapper inputMapper) {">`setInputMapper`</SwmToken> sets the mapper to map flow input attributes.

```java
	/**
	 * Sets the mapper to map flow input attributes.
	 * @param inputMapper the input mapper
	 */
	public void setInputMapper(Mapper inputMapper) {
		this.inputMapper = inputMapper;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="412">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="417:5:5" line-data="	public ActionList getStartActionList() {">`getStartActionList`</SwmToken> returns the list of actions executed by the flow when an execution of the flow starts.

```java
	/**
	 * Returns the list of actions executed by this flow when an execution of the flow <i>starts</i>. The returned list
	 * is mutable.
	 * @return the start action list
	 */
	public ActionList getStartActionList() {
		return startActionList;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="421">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="426:5:5" line-data="	public ActionList getEndActionList() {">`getEndActionList`</SwmToken> returns the list of actions executed by the flow when an execution of the flow ends.

```java
	/**
	 * Returns the list of actions executed by this flow when an execution of the flow <i>ends</i>. The returned list is
	 * mutable.
	 * @return the end action list
	 */
	public ActionList getEndActionList() {
		return endActionList;
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" line="161">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="120:4:4" line-data="public class FlowModelFlowBuilder extends AbstractFlowBuilder {">`FlowModelFlowBuilder`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="161:3:3" line-data="	protected Flow createFlow() {">`Flow`</SwmToken> class is used to create a new flow instance. The method <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="161:5:5" line-data="	protected Flow createFlow() {">`createFlow`</SwmToken> initializes the flow with an ID and attributes, and sets the application context.

```java
	protected Flow createFlow() {
		String flowId = getContext().getFlowId();
		AttributeMap<Object> flowAttributes = parseFlowMetaAttributes(flowModel);
		flowAttributes = getContext().getFlowAttributes().union(flowAttributes);
		if (IS_SPRING_FACES_PRESENT) {
			flowAttributes.asMap().put(VALIDATOR_FLOW_ATTR, getLocalContext().getValidator());
			flowAttributes.asMap().put(VALIDATION_HINT_RESOLVER_FLOW_ATTR, getLocalContext().getValidationHintResolver());
		}
		Flow flow = getLocalContext().getFlowArtifactFactory().createFlow(flowId, flowAttributes);
		flow.setApplicationContext(getLocalContext().getApplicationContext());
		return flow;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/ActionState.java" line="58">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ActionState.java" pos="58:3:3" line-data="	public ActionState(Flow flow, String id) throws IllegalArgumentException {">`ActionState`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ActionState.java" pos="58:5:5" line-data="	public ActionState(Flow flow, String id) throws IllegalArgumentException {">`Flow`</SwmToken> class is used in the constructor to associate the state with a specific flow. This ensures that the state is part of the correct flow.

```java
	public ActionState(Flow flow, String id) throws IllegalArgumentException {
		super(flow, id);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" line="75">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" pos="75:3:3" line-data="	public ViewState(Flow flow, String id, ViewFactory viewFactory) throws IllegalArgumentException {">`ViewState`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ViewState.java" pos="75:5:5" line-data="	public ViewState(Flow flow, String id, ViewFactory viewFactory) throws IllegalArgumentException {">`Flow`</SwmToken> class is used in the constructor to link the view state to a particular flow. This linkage is crucial for maintaining the flow's structure and behavior.

```java
	public ViewState(Flow flow, String id, ViewFactory viewFactory) throws IllegalArgumentException {
		super(flow, id);
		Assert.notNull(viewFactory, "The view factory is required");
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/AbstractFlowBuilder.java" line="62">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="72:14:14" line-data="import org.springframework.webflow.engine.builder.support.AbstractFlowBuilder;">`AbstractFlowBuilder`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/AbstractFlowBuilder.java" pos="62:3:3" line-data="	protected Flow createFlow() {">`Flow`</SwmToken> class is used to represent the flow being built by the builder. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/support/AbstractFlowBuilder.java" pos="62:5:5" line-data="	protected Flow createFlow() {">`createFlow`</SwmToken> method initializes a new flow instance with an ID and attributes.

```java
	protected Flow createFlow() {
		String id = getContext().getFlowId();
		AttributeMap<Object> attributes = getContext().getFlowAttributes();
		return getContext().getFlowArtifactFactory().createFlow(id, attributes);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="54">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="54:3:3" line-data="	protected TransitionableState(Flow flow, String id) throws IllegalArgumentException {">`TransitionableState`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="54:5:5" line-data="	protected TransitionableState(Flow flow, String id) throws IllegalArgumentException {">`Flow`</SwmToken> class is used in the constructor to ensure that the state is part of the correct flow. This association is necessary for the state's transitions to function properly.

```java
	protected TransitionableState(Flow flow, String id) throws IllegalArgumentException {
		super(flow, id);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/EndState.java" line="67">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/EndState.java" pos="67:3:3" line-data="	public EndState(Flow flow, String id) throws IllegalArgumentException {">`EndState`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/EndState.java" pos="67:5:5" line-data="	public EndState(Flow flow, String id) throws IllegalArgumentException {">`Flow`</SwmToken> class is used in the constructor to associate the end state with a specific flow. This ensures that the end state correctly terminates the flow.

```java
	public EndState(Flow flow, String id) throws IllegalArgumentException {
		super(flow, id);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="134">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="89:10:10" line-data=" * {@link #start(RequestControlContext, MutableAttributeMap) start}, {@link #resume(RequestControlContext)},">`RequestControlContext`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="134:5:5" line-data="	void start(Flow flow, MutableAttributeMap&lt;?&gt; input) throws FlowExecutionException;">`Flow`</SwmToken> class is used in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="134:3:3" line-data="	void start(Flow flow, MutableAttributeMap&lt;?&gt; input) throws FlowExecutionException;">`start`</SwmToken> method to initiate a new flow session. This method handles the initial setup and execution of the flow.

```java
	void start(Flow flow, MutableAttributeMap<?> input) throws FlowExecutionException;

```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" line="119">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="219:4:4" line-data="		for (State state : states) {">`State`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="119:7:7" line-data="	private void setFlow(Flow flow) throws IllegalArgumentException {">`Flow`</SwmToken> class is used to represent the owning flow of the state. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/State.java" pos="119:5:5" line-data="	private void setFlow(Flow flow) throws IllegalArgumentException {">`setFlow`</SwmToken> method ensures that the state is correctly added to the flow.

```java
	private void setFlow(Flow flow) throws IllegalArgumentException {
		Assert.hasText(getId(), "The id of the state should be set before adding the state to a flow");
		Assert.notNull(flow, "The owning flow is required");
		this.flow = flow;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" line="75">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" pos="41:4:4" line-data="public class FlowExecutionImplFactory implements FlowExecutionFactory {">`FlowExecutionImplFactory`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" pos="76:5:5" line-data="		Assert.isInstanceOf(Flow.class, flowDefinition, &quot;FlowDefinition is of the wrong type: &quot;);">`Flow`</SwmToken> class is used to create and manage flow executions. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" pos="75:5:5" line-data="	public FlowExecution createFlowExecution(FlowDefinition flowDefinition) {">`createFlowExecution`</SwmToken> method initializes a new execution with the provided flow definition.

```java
	public FlowExecution createFlowExecution(FlowDefinition flowDefinition) {
		Assert.isInstanceOf(Flow.class, flowDefinition, "FlowDefinition is of the wrong type: ");
		if (logger.isDebugEnabled()) {
			logger.debug("Creating new execution of '" + flowDefinition.getId() + "'");
		}
		FlowExecutionImpl execution = new FlowExecutionImpl((Flow) flowDefinition);
		execution.setAttributes(executionAttributes);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/DecisionState.java" line="37">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/DecisionState.java" pos="37:3:3" line-data="	public DecisionState(Flow flow, String stateId) throws IllegalArgumentException {">`DecisionState`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/DecisionState.java" pos="37:5:5" line-data="	public DecisionState(Flow flow, String stateId) throws IllegalArgumentException {">`Flow`</SwmToken> class is used in the constructor to link the decision state to a specific flow. This association is necessary for the decision logic to be part of the flow.

```java
	public DecisionState(Flow flow, String stateId) throws IllegalArgumentException {
		super(flow, stateId);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" line="233">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="47:2:2" line-data="class RequestControlContextImpl implements RequestControlContext {">`RequestControlContextImpl`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="233:7:7" line-data="	public void start(Flow flow, MutableAttributeMap&lt;?&gt; input) throws FlowExecutionException {">`Flow`</SwmToken> class is used in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="233:5:5" line-data="	public void start(Flow flow, MutableAttributeMap&lt;?&gt; input) throws FlowExecutionException {">`start`</SwmToken> method to begin the execution of a flow. This method handles the initial setup and execution of the flow.

```java
	public void start(Flow flow, MutableAttributeMap<?> input) throws FlowExecutionException {
		flowExecution.start(flow, input, this);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="144">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="144:3:3" line-data="	public FlowExecutionImpl(Flow flow) {">`FlowExecutionImpl`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="144:5:5" line-data="	public FlowExecutionImpl(Flow flow) {">`Flow`</SwmToken> class is used to represent the flow being executed. The constructor initializes the flow execution with the provided flow.

```java
	public FlowExecutionImpl(Flow flow) {
		Assert.notNull(flow, "The flow definition is required");
		this.flow = flow;
		status = FlowExecutionStatus.NOT_STARTED;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
