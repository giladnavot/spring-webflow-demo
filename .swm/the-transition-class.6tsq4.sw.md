---
title: The Transition class
---
This document will provide a comprehensive overview of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="61:15:15" line-data="	protected final Log logger = LogFactory.getLog(Transition.class);">`Transition`</SwmToken> class in the Spring Web Flow project. We will cover:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="61:15:15" line-data="	protected final Log logger = LogFactory.getLog(Transition.class);">`Transition`</SwmToken> is and its purpose.
2. The variables and functions defined in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="61:15:15" line-data="	protected final Log logger = LogFactory.getLog(Transition.class);">`Transition`</SwmToken> class.

# What is Transition

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="61:15:15" line-data="	protected final Log logger = LogFactory.getLog(Transition.class);">`Transition`</SwmToken> class in <SwmPath>[spring-webflow/…/engine/Transition.java](spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java)</SwmPath> represents a path from one state to another within a flow execution. It is used to move the flow from its current state, called the source state, to another state, called the target state. A transition becomes eligible for execution when an event occurs in the source state, and its eligibility is determined by a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="67:3:3" line-data="	private TransitionCriteria matchingCriteria;">`TransitionCriteria`</SwmToken> object called the matching criteria. If the matching criteria return true, the transition is marked eligible for execution. The execution of an eligible transition is further determined by another <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="67:3:3" line-data="	private TransitionCriteria matchingCriteria;">`TransitionCriteria`</SwmToken> object called the execution criteria. If the execution criteria test fails, the transition will roll back and reenter its source state. If the execution criteria test succeeds, the transition will execute and take the flow to the target state.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="61">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="61:7:7" line-data="	protected final Log logger = LogFactory.getLog(Transition.class);">`logger`</SwmToken> is used for logging purposes within the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="61:15:15" line-data="	protected final Log logger = LogFactory.getLog(Transition.class);">`Transition`</SwmToken> class and its subclasses.

```java
	protected final Log logger = LogFactory.getLog(Transition.class);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="67">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="67:5:5" line-data="	private TransitionCriteria matchingCriteria;">`matchingCriteria`</SwmToken> determines whether or not this transition matches as eligible for execution when an event occurs in the source state.

```java
	private TransitionCriteria matchingCriteria;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="73">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="73:5:5" line-data="	private TransitionCriteria executionCriteria = WildcardTransitionCriteria.INSTANCE;">`executionCriteria`</SwmToken> determines whether or not this transition, once matched, should complete execution or should roll back.

```java
	private TransitionCriteria executionCriteria = WildcardTransitionCriteria.INSTANCE;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="78">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="78:5:5" line-data="	private TargetStateResolver targetStateResolver;">`targetStateResolver`</SwmToken> is responsible for calculating the target state of this transition.

```java
	private TargetStateResolver targetStateResolver;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="86">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="86:3:3" line-data="	public Transition() {">`Transition`</SwmToken> creates a new transition that always matches and always executes, but its execution does nothing by default.

```java
	public Transition() {
		this(WildcardTransitionCriteria.INSTANCE, null);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="97">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="97:3:3" line-data="	public Transition(TargetStateResolver targetStateResolver) {">`Transition`</SwmToken> creates a new transition that always matches and always executes, transitioning to the target state calculated by the provided <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="97:7:7" line-data="	public Transition(TargetStateResolver targetStateResolver) {">`targetStateResolver`</SwmToken>.

```java
	public Transition(TargetStateResolver targetStateResolver) {
		this(WildcardTransitionCriteria.INSTANCE, targetStateResolver);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="108">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="108:3:3" line-data="	public Transition(TransitionCriteria matchingCriteria, TargetStateResolver targetStateResolver) {">`Transition`</SwmToken> creates a new transition that matches on the specified criteria, transitioning to the target state calculated by the provided <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="108:12:12" line-data="	public Transition(TransitionCriteria matchingCriteria, TargetStateResolver targetStateResolver) {">`targetStateResolver`</SwmToken>.

```java
	public Transition(TransitionCriteria matchingCriteria, TargetStateResolver targetStateResolver) {
		setMatchingCriteria(matchingCriteria);
		setTargetStateResolver(targetStateResolver);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="115">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="115:5:5" line-data="	public String getId() {">`getId`</SwmToken> returns the ID of the transition, which is derived from the matching criteria.

```java
	public String getId() {
		return matchingCriteria.toString();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="119">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="119:5:5" line-data="	public String getTargetStateId() {">`getTargetStateId`</SwmToken> returns the ID of the target state, which is derived from the target state resolver.

```java
	public String getTargetStateId() {
		if (targetStateResolver != null) {
			return targetStateResolver.toString();
		} else {
			return null;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="131">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="131:5:5" line-data="	public TransitionCriteria getMatchingCriteria() {">`getMatchingCriteria`</SwmToken> returns the criteria that determine whether or not this transition matches as eligible for execution.

```java
	public TransitionCriteria getMatchingCriteria() {
		return matchingCriteria;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="139">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="139:5:5" line-data="	public void setMatchingCriteria(TransitionCriteria matchingCriteria) {">`setMatchingCriteria`</SwmToken> sets the criteria that determine whether or not this transition matches as eligible for execution.

```java
	public void setMatchingCriteria(TransitionCriteria matchingCriteria) {
		Assert.notNull(matchingCriteria, "The criteria for matching this transition is required");
		this.matchingCriteria = matchingCriteria;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="149">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="149:5:5" line-data="	public TransitionCriteria getExecutionCriteria() {">`getExecutionCriteria`</SwmToken> returns the criteria that determine whether or not this transition, once matched, should complete execution or should roll back.

```java
	public TransitionCriteria getExecutionCriteria() {
		return executionCriteria;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="158">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="158:5:5" line-data="	public void setExecutionCriteria(TransitionCriteria executionCriteria) {">`setExecutionCriteria`</SwmToken> sets the criteria that determine whether or not this transition, once matched, should complete execution or should roll back.

```java
	public void setExecutionCriteria(TransitionCriteria executionCriteria) {
		this.executionCriteria = executionCriteria;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="165">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="165:5:5" line-data="	public TargetStateResolver getTargetStateResolver() {">`getTargetStateResolver`</SwmToken> returns this transition's target state resolver.

```java
	public TargetStateResolver getTargetStateResolver() {
		return targetStateResolver;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="174">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="174:5:5" line-data="	public void setTargetStateResolver(TargetStateResolver targetStateResolver) {">`setTargetStateResolver`</SwmToken> sets this transition's target state resolver, to calculate what state to transition to when this transition is executed.

```java
	public void setTargetStateResolver(TargetStateResolver targetStateResolver) {
		this.targetStateResolver = targetStateResolver;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="184">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="184:5:5" line-data="	public boolean matches(RequestContext context) {">`matches`</SwmToken> checks if this transition is eligible for execution given the state of the provided flow execution request context.

```java
	public boolean matches(RequestContext context) {
		return matchingCriteria.test(context);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="194">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="194:5:5" line-data="	public boolean canExecute(RequestContext context) {">`canExecute`</SwmToken> checks if this transition can complete its execution or should be rolled back, given the state of the flow execution request context.

```java
	public boolean canExecute(RequestContext context) {
		if (executionCriteria != null) {
			return executionCriteria.test(context);
		} else {
			return false;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="211">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="211:5:5" line-data="	public boolean execute(State sourceState, RequestControlContext context) throws FlowExecutionException {">`execute`</SwmToken> executes this state transition. It should only be called if the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="184:5:5" line-data="	public boolean matches(RequestContext context) {">`matches`</SwmToken> method returns true for the given context.

```java
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
							logger.debug("Exiting state '" + sourceState.getId() + "'");
						}
						if (sourceState instanceof TransitionableState) {
							((TransitionableState) sourceState).exit(context);
						}
					}
					targetState.enter(context);
					if (logger.isDebugEnabled()) {
						if (context.getFlowExecutionContext().isActive()) {
							logger.debug("Completed transition execution.  As a result, the new state is '"
									+ context.getCurrentState().getId() + "' in flow '"
									+ context.getActiveFlow().getId() + "'");
						} else {
							logger.debug("Completed transition execution.  As a result, the flow execution has ended");
						}
					}
					return true;
				}
			}
		}
		return false;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="245">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="245:5:5" line-data="	public String toString() {">`toString`</SwmToken> returns a string representation of the transition, including the matching criteria and the target state resolver.

```java
	public String toString() {
		return new ToStringCreator(this).append("on", getMatchingCriteria()).append("to", getTargetStateResolver())
				.toString();
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="471">

---

In the <SwmPath>[spring-webflow/…/engine/Flow.java](spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="472:4:4" line-data="		for (Transition transition : globalTransitionSet) {">`Transition`</SwmToken> class is used to retrieve and execute transitions based on specific events. For instance, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="471:5:5" line-data="	public TransitionDefinition getGlobalTransition(String eventId) {">`getGlobalTransition`</SwmToken> method iterates through a set of global transitions to find a match for a given event ID.

```java
	public TransitionDefinition getGlobalTransition(String eventId) {
		for (Transition transition : globalTransitionSet) {
			if (transition.getId().equals(eventId)) {
				return transition;
			}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" line="710">

---

In the <SwmPath>[spring-webflow/…/model/FlowModelFlowBuilder.java](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="710:3:3" line-data="	private Transition[] parseIfs(List&lt;IfModel&gt; ifModels) {">`Transition`</SwmToken> class is used to parse and create transitions from a list of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="710:11:11" line-data="	private Transition[] parseIfs(List&lt;IfModel&gt; ifModels) {">`IfModel`</SwmToken> objects. This is done in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="710:7:7" line-data="	private Transition[] parseIfs(List&lt;IfModel&gt; ifModels) {">`parseIfs`</SwmToken> method, which converts the list of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="710:11:11" line-data="	private Transition[] parseIfs(List&lt;IfModel&gt; ifModels) {">`IfModel`</SwmToken> objects into an array of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="710:3:3" line-data="	private Transition[] parseIfs(List&lt;IfModel&gt; ifModels) {">`Transition`</SwmToken> objects.

```java
	private Transition[] parseIfs(List<IfModel> ifModels) {
		if (ifModels != null && !ifModels.isEmpty()) {
			List<Transition> transitions = new ArrayList<>(ifModels.size());
			for (IfModel ifModel : ifModels) {
				transitions.addAll(Arrays.asList(parseIf(ifModel)));
			}
			return transitions.toArray(new Transition[transitions.size()]);
		} else {
			return new Transition[0];
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" line="83">

---

In the <SwmPath>[spring-webflow/…/builder/FlowArtifactFactory.java](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" pos="84:23:23" line-data="			ViewFactory viewFactory, Boolean redirect, boolean popup, Action[] renderActions, Transition[] transitions,">`Transition`</SwmToken> class is used in several methods to create different state instances such as <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" pos="86:1:1" line-data="		ViewState viewState = new ViewState(flow, id, viewFactory);">`ViewState`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" pos="113:1:1" line-data="		ActionState actionState = new ActionState(flow, id);">`ActionState`</SwmToken>, and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" pos="135:1:1" line-data="		DecisionState decisionState = new DecisionState(flow, id);">`DecisionState`</SwmToken>. These methods initialize the state instances with various properties, including an array of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowArtifactFactory.java" pos="84:23:23" line-data="			ViewFactory viewFactory, Boolean redirect, boolean popup, Action[] renderActions, Transition[] transitions,">`Transition`</SwmToken> objects.

```java
	public State createViewState(String id, Flow flow, ViewVariable[] variables, Action[] entryActions,
			ViewFactory viewFactory, Boolean redirect, boolean popup, Action[] renderActions, Transition[] transitions,
			FlowExecutionExceptionHandler[] exceptionHandlers, Action[] exitActions, AttributeMap<?> attributes) {
		ViewState viewState = new ViewState(flow, id, viewFactory);
		viewState.addVariables(variables);
		viewState.setRedirect(redirect);
		viewState.setPopup(popup);
		viewState.getRenderActionList().addAll(renderActions);
		configureCommonProperties(viewState, entryActions, transitions, exceptionHandlers, exitActions, attributes);
		return viewState;
	}

	/**
	 * Factory method that creates a new action state, a state where a system action is executed. This method is an
	 * atomic operation that returns a fully initialized state. It encapsulates the selection of the action state
	 * implementation as well as the state assembly.
	 * @param id the identifier to assign to the state, must be unique to its owning flow (required)
	 * @param flow the flow that will own (contain) this state (required)
	 * @param entryActions any state entry actions; may be null
	 * @param actions the actions to execute when the state is entered (required)
	 * @param transitions any transitions (paths) out of this state; may be null
	 * @param exceptionHandlers any exception handlers; may be null
	 * @param exitActions any state exit actions; may be null
	 * @param attributes attributes to assign to the State, which may also be used to affect state construction; may be
	 * null
	 * @return the fully initialized action state instance
	 */
	public State createActionState(String id, Flow flow, Action[] entryActions, Action[] actions,
			Transition[] transitions, FlowExecutionExceptionHandler[] exceptionHandlers, Action[] exitActions,
			AttributeMap<?> attributes) {
		ActionState actionState = new ActionState(flow, id);
		actionState.getActionList().addAll(actions);
		configureCommonProperties(actionState, entryActions, transitions, exceptionHandlers, exitActions, attributes);
		return actionState;
	}

	/**
	 * Factory method that creates a new decision state, a state where a flow routing decision is made. This method is
	 * an atomic operation that returns a fully initialized state. It encapsulates the selection of the decision state
	 * implementation as well as the state assembly.
	 * @param id the identifier to assign to the state, must be unique to its owning flow (required)
	 * @param flow the flow that will own (contain) this state (required)
	 * @param entryActions any state entry actions; may be null
	 * @param transitions any transitions (paths) out of this state
	 * @param exceptionHandlers any exception handlers; may be null
	 * @param exitActions any state exit actions; may be null
	 * @param attributes attributes to assign to the State, which may also be used to affect state construction; may be
	 * null
	 * @return the fully initialized decision state instance
	 */
	public State createDecisionState(String id, Flow flow, Action[] entryActions, Transition[] transitions,
			FlowExecutionExceptionHandler[] exceptionHandlers, Action[] exitActions, AttributeMap<?> attributes) {
		DecisionState decisionState = new DecisionState(flow, id);
		configureCommonProperties(decisionState, entryActions, transitions, exceptionHandlers, exitActions, attributes);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" line="98">

---

In the <SwmPath>[spring-webflow/…/engine/RequestControlContext.java](spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="98:5:5" line-data="	boolean execute(Transition transition);">`Transition`</SwmToken> class is used to execute transitions out of the current source state. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/RequestControlContext.java" pos="98:3:3" line-data="	boolean execute(Transition transition);">`execute`</SwmToken> method allows for privileged execution of an arbitrary transition.

```java
	boolean execute(Transition transition);

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

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" line="213">

---

In the <SwmPath>[spring-webflow/…/impl/RequestControlContextImpl.java](spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="213:7:7" line-data="	public boolean execute(Transition transition) {">`Transition`</SwmToken> class is used to execute transitions and set the current transition in the request context. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="213:5:5" line-data="	public boolean execute(Transition transition) {">`execute`</SwmToken> method calls the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="214:3:5" line-data="		return flowExecution.execute(transition, this);">`flowExecution.execute`</SwmToken> method with the transition and context.

```java
	public boolean execute(Transition transition) {
		return flowExecution.execute(transition, this);
	}

	public void setCurrentTransition(Transition transition) {
		this.currentTransition = transition;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="393">

---

In the <SwmPath>[spring-webflow/…/impl/FlowExecutionImpl.java](spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="393:5:5" line-data="	boolean execute(Transition transition, RequestControlContext context) {">`Transition`</SwmToken> class is used to execute transitions within the flow execution. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="393:3:3" line-data="	boolean execute(Transition transition, RequestControlContext context) {">`execute`</SwmToken> method fires transition executing events and then executes the transition.

```java
	boolean execute(Transition transition, RequestControlContext context) {
		listeners.fireTransitionExecuting(context, transition);
		return transition.execute((State) getActiveSession().getState(), context);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" line="36">

---

In the <SwmPath>[spring-webflow/…/engine/TargetStateResolver.java](spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" pos="36:5:5" line-data="	State resolveTargetState(Transition transition, State sourceState, RequestContext context);">`Transition`</SwmToken> class is used to resolve the target state of a transition. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TargetStateResolver.java" pos="36:3:3" line-data="	State resolveTargetState(Transition transition, State sourceState, RequestContext context);">`resolveTargetState`</SwmToken> method returns the target state of the transition based on the current request context.

```java
	State resolveTargetState(Transition transition, State sourceState, RequestContext context);
}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" line="64">

---

In the <SwmPath>[spring-webflow/…/engine/TransitionableState.java](spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="65:4:4" line-data="		for (Transition transition : transitions) {">`Transition`</SwmToken> class is used to retrieve transitions based on event IDs and to get required transitions for a given request context. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="64:5:5" line-data="	public TransitionDefinition getTransition(String eventId) {">`getTransition`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionableState.java" pos="87:5:5" line-data="	public Transition getRequiredTransition(RequestContext context) throws NoMatchingTransitionException {">`getRequiredTransition`</SwmToken> methods handle these functionalities.

```java
	public TransitionDefinition getTransition(String eventId) {
		for (Transition transition : transitions) {
			if (transition.getId().equals(eventId)) {
				return transition;
			}
		}
		return null;
	}

	// impl

	/**
	 * Returns the set of transitions. The returned set is mutable.
	 */
	public TransitionSet getTransitionSet() {
		return transitions;
	}

	/**
	 * Get a transition in this state for given flow execution request context. Throws and exception when there is no
	 * corresponding transition.
	 * @throws NoMatchingTransitionException when a matching transition cannot be found
	 */
	public Transition getRequiredTransition(RequestContext context) throws NoMatchingTransitionException {
		Transition transition = getTransitionSet().getTransition(context);
		if (transition == null) {
			throw new NoMatchingTransitionException(getFlow().getId(), getId(), context.getCurrentEvent(),
					"No transition found on occurence of event '" + context.getCurrentEvent() + "' in state '"
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/ActionState.java" line="76">

---

In the <SwmPath>[spring-webflow/…/engine/ActionState.java](spring-webflow/src/main/java/org/springframework/webflow/engine/ActionState.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ActionState.java" pos="76:3:3" line-data="	public Transition getRequiredTransition(RequestContext context) throws NoMatchingTransitionException {">`Transition`</SwmToken> class is used to get required transitions for a given request context. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/ActionState.java" pos="76:5:5" line-data="	public Transition getRequiredTransition(RequestContext context) throws NoMatchingTransitionException {">`getRequiredTransition`</SwmToken> method retrieves the transition from the transition set based on the current event.

```java
	public Transition getRequiredTransition(RequestContext context) throws NoMatchingTransitionException {
		Transition transition = getTransitionSet().getTransition(context);
		if (transition == null) {
			throw new NoMatchingActionResultTransitionException(this, context.getCurrentEvent());
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/support/TransitionExecutingFlowExecutionExceptionHandler.java" line="111">

---

In the <SwmPath>[spring-webflow/…/support/TransitionExecutingFlowExecutionExceptionHandler.java](spring-webflow/src/main/java/org/springframework/webflow/engine/support/TransitionExecutingFlowExecutionExceptionHandler.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/support/TransitionExecutingFlowExecutionExceptionHandler.java" pos="111:7:7" line-data="		context.execute(new Transition(getTargetStateResolver(exception)));">`Transition`</SwmToken> class is used to execute a transition when handling flow execution exceptions. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/support/TransitionExecutingFlowExecutionExceptionHandler.java" pos="111:1:3" line-data="		context.execute(new Transition(getTargetStateResolver(exception)));">`context.execute`</SwmToken> method is called with a new <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/support/TransitionExecutingFlowExecutionExceptionHandler.java" pos="111:7:7" line-data="		context.execute(new Transition(getTargetStateResolver(exception)));">`Transition`</SwmToken> object.

```java
		context.execute(new Transition(getTargetStateResolver(exception)));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionSet.java" line="34">

---

In the <SwmPath>[spring-webflow/…/engine/TransitionSet.java](spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionSet.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionSet.java" pos="34:10:10" line-data="public class TransitionSet implements Iterable&lt;Transition&gt; {">`Transition`</SwmToken> class is used to manage a set of transitions. Methods such as <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionSet.java" pos="43:14:14" line-data="	 * @param transition the transition to add">`add`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionSet.java" pos="58:5:5" line-data="	public boolean addAll(Transition... transitions) {">`addAll`</SwmToken>, and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/TransitionSet.java" pos="47:4:4" line-data="		if (contains(transition)) {">`contains`</SwmToken> handle adding transitions to the set and checking for their existence.

```java
public class TransitionSet implements Iterable<Transition> {

	/**
	 * The set of transitions.
	 */
	private List<Transition> transitions = new LinkedList<>();

	/**
	 * Add a transition to this set.
	 * @param transition the transition to add
	 * @return true if this set's contents changed as a result of the add operation
	 */
	public boolean add(Transition transition) {
		if (contains(transition)) {
			return false;
		}
		return transitions.add(transition);
	}

	/**
	 * Add a collection of transition instances to this set.
	 * @param transitions the transitions to add
	 * @return true if this set's contents changed as a result of the add operation
	 */
	public boolean addAll(Transition... transitions) {
		return CollectionUtils.addAllNoDuplicates(this.transitions, transitions);
	}

	/**
	 * Tests if this transition is in this set.
	 * @param transition the transition
	 * @return true if the transition is contained in this set, false otherwise
	 */
	public boolean contains(Transition transition) {
		return transitions.contains(transition);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/support/DefaultTargetStateResolver.java" line="57">

---

In the <SwmPath>[spring-webflow/…/support/DefaultTargetStateResolver.java](spring-webflow/src/main/java/org/springframework/webflow/engine/support/DefaultTargetStateResolver.java)</SwmPath> file, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/support/DefaultTargetStateResolver.java" pos="57:7:7" line-data="	public State resolveTargetState(Transition transition, State sourceState, RequestContext context) {">`Transition`</SwmToken> class is used to resolve the target state of a transition. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/support/DefaultTargetStateResolver.java" pos="57:5:5" line-data="	public State resolveTargetState(Transition transition, State sourceState, RequestContext context) {">`resolveTargetState`</SwmToken> method retrieves the target state ID from the context and returns the corresponding state instance.

```java
	public State resolveTargetState(Transition transition, State sourceState, RequestContext context) {
		String targetStateId = (String) targetStateIdExpression.getValue(context);
		if (targetStateId != null) {
			return ((Flow) context.getActiveFlow()).getStateInstance(targetStateId);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
