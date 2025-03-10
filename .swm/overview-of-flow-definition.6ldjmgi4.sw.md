---
title: Overview of Flow Definition
---
# Overview of Flow Definition

<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/definition/FlowDefinition.java" pos="44:4:4" line-data="public interface FlowDefinition extends Annotated {">`FlowDefinition`</SwmToken> refers to the definition of a flow, which is a program that, when executed, carries out a task on behalf of a single client.

A flow definition is a reusable, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/definition/FlowDefinition.java" pos="24:16:18" line-data=" * A flow definition is a reusable, self-contained controller module that defines a blue print for an executable user">`self-contained`</SwmToken> controller module that defines a blueprint for an executable user task.

Flows typically orchestrate controlled navigations or dialogs within web applications to guide users through the fulfillment of a business process or goal that takes place over a series of steps, modeled as states.

# Structure of a Flow Definition

Structurally, a flow definition is composed of a set of states. A state is a point in a flow where a behavior is executed, such as showing a view, executing an action, spawning a subflow, or terminating the flow.

Different types of states execute different behaviors in a polymorphic fashion. Most states are transitionable states, meaning they can respond to events by taking the flow from one state to another.

Each flow has exactly one start state, which defines the starting point of the program.

# Flow Definition Endpoints

The interface exposes the flow's identifier, states, and other definitional attributes, making it suitable for introspection by tools as well as <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/definition/FlowDefinition.java" pos="37:15:17" line-data=" * introspection by tools as well as user-code at flow execution time.">`user-code`</SwmToken> at flow execution time.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/definition/FlowDefinition.java" line="47">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/definition/FlowDefinition.java" pos="50:3:3" line-data="	String getId();">`getId`</SwmToken> method returns the unique identifier of a flow. This identifier is used to distinguish one flow from another within the application.

```java
	 * Returns the unique id of this flow.
	 * @return the flow id
	 */
	String getId();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/definition/FlowDefinition.java" line="52">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/definition/FlowDefinition.java" pos="34:18:18" line-data=" * Each flow has exactly one {@link #getStartState() start state} which defines the starting point of the program.">`getStartState`</SwmToken> method returns the starting point of the flow. This is the initial state where the flow begins its execution.

```java
	/**
	 * Return this flow's starting point.
	 * @return the start state
	 */
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
