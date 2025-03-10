---
title: Introduction to Transition Management in Engine
---
# Introduction to Transition Management in Engine

Transition Management refers to the process of managing the flow execution from one state to another within the Spring Web Flow framework.

A transition is a path from one state, called the source state, to another state, called the target state.

Transitions become eligible for execution when an event occurs within a transitionable source state.

The eligibility of a transition is determined by a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="36:22:22" line-data=" * eligibility of this transition is made by a &lt;code&gt;TransitionCriteria&lt;/code&gt; object called the &lt;i&gt;matching">`TransitionCriteria`</SwmToken> object called the matching criteria.

If the matching criteria returns true, the transition is marked eligible for execution for that event.

Whether an eligible transition should be allowed to execute is determined by another <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="36:22:22" line-data=" * eligibility of this transition is made by a &lt;code&gt;TransitionCriteria&lt;/code&gt; object called the &lt;i&gt;matching">`TransitionCriteria`</SwmToken> object called the execution criteria.

If the execution criteria test fails, the transition will roll back and reenter its source state.

If the execution criteria test succeeds, the transition will execute and take the flow to the transition's target state.

The target state of a transition is typically specified at configuration time in a static manner.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" line="28">

---

An example of Transition Management is the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="56:4:4" line-data="public class Transition extends AnnotatedObject implements TransitionDefinition {">`Transition`</SwmToken> class, which uses <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Transition.java" pos="36:22:22" line-data=" * eligibility of this transition is made by a &lt;code&gt;TransitionCriteria&lt;/code&gt; object called the &lt;i&gt;matching">`TransitionCriteria`</SwmToken> to determine if a transition should be executed based on the current state and event.

```java
/**
 * A path from one {@link TransitionableState state} to another {@link State state}.
 * <p>
 * When executed a transition takes a flow execution from its current state, called the <i>source state</i>, to another
 * state, called the <i>target state</i>. A transition may become eligible for execution on the occurrence of an
 * {@link Event} from within a transitionable source state.
 * <p>
 * When an event occurs within this transition's source <code>TransitionableState</code> the determination of the
 * eligibility of this transition is made by a <code>TransitionCriteria</code> object called the <i>matching
 * criteria</i>. If the matching criteria returns <code>true</code> this transition is marked eligible for execution for
 * that event.
 * <p>
 * Determination as to whether an eligible transition should be allowed to execute is made by a
 * <code>TransitionCriteria</code> object called the <i>execution criteria</i>. If the execution criteria test fails
 * this transition will <i>roll back</i> and reenter its source state. If the execution criteria test succeeds this
 * transition will execute and take the flow to the transition's target state.
 * <p>
 * The target state of this transition is typically specified at configuration time in a static manner. If the target
 * state of this transition needs to be calculated in a dynamic fashion at runtime configure a
 * {@link TargetStateResolver} that supports such calculations.
 * 
 * @see TransitionableState
 * @see TransitionCriteria
 * @see TargetStateResolver
 * 
 * @author Keith Donald
 * @author Erwin Vervaet
 */
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
