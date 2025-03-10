---
title: Introduction to Conversations in Web Flow
---
# What is a Conversation

A Conversation refers to a single logical user interaction within the scope of a single request. It provides a context for a task that begins and eventually ends, allowing attributes to be placed in and read from the conversation's context during its lifecycle.

## Thread Safety

Conversations are not thread-safe and should not be shared among multiple threads. They need to be locked to obtain exclusive access before manipulation and unlocked after the manipulation is finished.

## Attributes

Attributes associated with a conversation can be any attributes, possibly technical in nature, and are not necessarily 'conversation scope' as defined for a flow execution.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/repository/support/AbstractFlowExecutionRepository.java" line="98">

---

An example of using a Conversation can be seen in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/support/AbstractFlowExecutionRepository.java" pos="52:6:6" line-data="public abstract class AbstractFlowExecutionRepository implements FlowExecutionRepository, FlowExecutionKeyFactory {">`AbstractFlowExecutionRepository`</SwmToken> class, where a conversation is begun and its ID is retrieved.

```java
		if (key == null) {
			Conversation conversation = beginConversation(execution);
			ConversationId executionId = conversation.getId();
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
