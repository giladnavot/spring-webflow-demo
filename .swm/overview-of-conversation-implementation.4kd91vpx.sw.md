---
title: Overview of Conversation Implementation
---
# Overview of Conversation Implementation

The `impl` package in the `Conversation` module contains various implementation classes that support the conversation management functionality in Spring Web Flow. These classes provide concrete implementations for handling conversations, ensuring proper management and lifecycle of conversations within a session.

## Key Classes in the `impl` Package

Classes such as `ContainedConversation`, `ConversationContainer`, and `SimpleConversationId` are part of this package. Each of these classes plays a specific role in managing conversations.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/conversation/impl/ContainedConversation.java" line="5">

---

The `ContainedConversation` class is an internal helper class used by the `SessionBindingConversationManager` to manage individual conversations within a session.

```java
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      https://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
```

---

</SwmSnippet>

### ConversationContainer

The `ConversationContainer` class acts as a container for multiple conversations, managing their lifecycle and ensuring that they are properly stored and retrieved from the session.

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](https://app.swimm.io/)</sup></SwmMeta>
