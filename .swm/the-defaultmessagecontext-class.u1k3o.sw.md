---
title: The DefaultMessageContext class
---
This document will cover the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="59:3:3" line-data="	public DefaultMessageContext() {">`DefaultMessageContext`</SwmToken> class. We will cover:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="59:3:3" line-data="	public DefaultMessageContext() {">`DefaultMessageContext`</SwmToken> is.
2. Variables and functions defined in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="59:3:3" line-data="	public DefaultMessageContext() {">`DefaultMessageContext`</SwmToken>.

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="59:3:3" line-data="	public DefaultMessageContext() {">`DefaultMessageContext`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="59:3:3" line-data="	public DefaultMessageContext() {">`DefaultMessageContext`</SwmToken> class is a default implementation of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="534:1:1" line-data="		StateManageableMessageContext messageContext = new DefaultMessageContext(messageSource);">`StateManageableMessageContext`</SwmToken> interface. It uses a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="67:5:5" line-data="	public DefaultMessageContext(MessageSource messageSource) {">`MessageSource`</SwmToken> to resolve messages that are added by callers. This class is responsible for managing and resolving messages within a specific context, providing functionalities to add, retrieve, and clear messages.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="50">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="50:8:8" line-data="				protected List&lt;Message&gt; create(Object source) {">`create`</SwmToken> is used to create a new list of messages for a given source.

```java
				protected List<Message> create(Object source) {
					return new ArrayList<>();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="59">

---

The constructor <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="59:3:3" line-data="	public DefaultMessageContext() {">`DefaultMessageContext`</SwmToken> initializes the message context with a default message source that resolves default text and cannot resolve localized message codes.

```java
	public DefaultMessageContext() {
		init(null);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="67">

---

The constructor <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="67:3:3" line-data="	public DefaultMessageContext(MessageSource messageSource) {">`DefaultMessageContext`</SwmToken> initializes the message context with a provided message source to resolve messages added to this context.

```java
	public DefaultMessageContext(MessageSource messageSource) {
		init(messageSource);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="71">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="71:5:5" line-data="	public MessageSource getMessageSource() {">`getMessageSource`</SwmToken> returns the current message source used by this context.

```java
	public MessageSource getMessageSource() {
		return messageSource;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="77">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="77:7:7" line-data="	public Message[] getAllMessages() {">`getAllMessages`</SwmToken> retrieves all messages from the context.

```java
	public Message[] getAllMessages() {
		List<Message> messages = new ArrayList<>();
		for (List<Message> list : sourceMessages.values()) {
			messages.addAll(list);
		}
		return messages.toArray(new Message[messages.size()]);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="85">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="85:7:7" line-data="	public Message[] getMessagesBySource(Object source) {">`getMessagesBySource`</SwmToken> retrieves messages by a specific source.

```java
	public Message[] getMessagesBySource(Object source) {
		List<Message> messages = sourceMessages.get(source);
		return messages.toArray(new Message[messages.size()]);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="90">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="90:7:7" line-data="	public Message[] getMessagesByCriteria(MessageCriteria criteria) {">`getMessagesByCriteria`</SwmToken> retrieves messages that match specific criteria.

```java
	public Message[] getMessagesByCriteria(MessageCriteria criteria) {
		List<Message> messages = new ArrayList<>();
		for (List<Message> sourceMessages : this.sourceMessages.values()) {
			for (Message message : sourceMessages) {
				if (criteria.test(message)) {
					messages.add(message);
				}
			}
		}
		return messages.toArray(new Message[messages.size()]);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="102">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="102:5:5" line-data="	public boolean hasErrorMessages() {">`hasErrorMessages`</SwmToken> checks if there are any error messages in the context.

```java
	public boolean hasErrorMessages() {
		for (List<Message> sourceMessages : this.sourceMessages.values()) {
			for (Message message : sourceMessages) {
				if (message.getSeverity() == Severity.ERROR) {
					return true;
				}
			}
		}
		return false;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="113">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="113:5:5" line-data="	public void addMessage(MessageResolver messageResolver) {">`addMessage`</SwmToken> adds a resolved message to the context.

```java
	public void addMessage(MessageResolver messageResolver) {
		Locale currentLocale = LocaleContextHolder.getLocale();
		if (logger.isDebugEnabled()) {
			logger.debug("Resolving message using " + messageResolver);
		}
		Message message = messageResolver.resolveMessage(messageSource, currentLocale);
		List<Message> messages = sourceMessages.get(message.getSource());
		if (logger.isDebugEnabled()) {
			logger.debug("Adding resolved message " + message);
		}
		messages.add(message);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="126">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="126:5:5" line-data="	public void clearMessages() {">`clearMessages`</SwmToken> clears all messages from the context.

```java
	public void clearMessages() {
		sourceMessages.clear();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="132">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="132:5:5" line-data="	public Serializable createMessagesMemento() {">`createMessagesMemento`</SwmToken> creates a memento of the current messages for state management.

```java
	public Serializable createMessagesMemento() {
		return new LinkedHashMap<>(sourceMessages);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="136">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="137:5:5" line-data="	public void restoreMessages(Serializable messagesMemento) {">`restoreMessages`</SwmToken> restores messages from a given memento.

```java
	@SuppressWarnings("unchecked")
	public void restoreMessages(Serializable messagesMemento) {
		sourceMessages.putAll((Map<Object, List<Message>>) messagesMemento);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="141">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="141:5:5" line-data="	public void setMessageSource(MessageSource messageSource) {">`setMessageSource`</SwmToken> sets the message source for this context.

```java
	public void setMessageSource(MessageSource messageSource) {
		if (messageSource == null) {
			messageSource = new DefaultTextFallbackMessageSource();
		}
		this.messageSource = messageSource;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="150">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="150:5:5" line-data="	private void init(MessageSource messageSource) {">`init`</SwmToken> initializes the message context with a given message source.

```java
	private void init(MessageSource messageSource) {
		setMessageSource(messageSource);
		// create the 'null' source message list eagerly to ensure global messages are indexed first
		this.sourceMessages.get(null);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="156">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="156:5:5" line-data="	public String toString() {">`toString`</SwmToken> provides a string representation of the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="59:3:3" line-data="	public DefaultMessageContext() {">`DefaultMessageContext`</SwmToken> object.

```java
	public String toString() {
		return new ToStringCreator(this).append("sourceMessages", sourceMessages).toString();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="161">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="161:5:5" line-data="		protected MessageFormat resolveCode(String code, Locale locale) {">`resolveCode`</SwmToken> in the inner class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="143:7:7" line-data="			messageSource = new DefaultTextFallbackMessageSource();">`DefaultTextFallbackMessageSource`</SwmToken> is used to resolve a message code to a message format.

```java
		protected MessageFormat resolveCode(String code, Locale locale) {
			return null;
		}
```

---

</SwmSnippet>

# Usage

## <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="73:4:4" line-data="public class FlowExecutionImpl implements FlowExecution, Externalizable {">`FlowExecutionImpl`</SwmToken>

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="73:4:4" line-data="public class FlowExecutionImpl implements FlowExecution, Externalizable {">`FlowExecutionImpl`</SwmToken> class, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="59:3:3" line-data="	public DefaultMessageContext() {">`DefaultMessageContext`</SwmToken> is used to create a message context from a given message source. This is done within the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="533:5:5" line-data="	private MessageContext createMessageContext(MessageSource messageSource) {">`createMessageContext`</SwmToken> method, where a new instance of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="59:3:3" line-data="	public DefaultMessageContext() {">`DefaultMessageContext`</SwmToken> is instantiated with the provided <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="67:7:7" line-data="	public DefaultMessageContext(MessageSource messageSource) {">`messageSource`</SwmToken>.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" line="533">

---

Additionally, the method checks if there is a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="535:3:3" line-data="		Serializable messagesMemento = (Serializable) getFlashScope().extract(&quot;messagesMemento&quot;);">`messagesMemento`</SwmToken> in the flash scope. If such a memento exists, it restores the messages into the newly created <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImpl.java" pos="534:3:3" line-data="		StateManageableMessageContext messageContext = new DefaultMessageContext(messageSource);">`messageContext`</SwmToken>.

```java
	private MessageContext createMessageContext(MessageSource messageSource) {
		StateManageableMessageContext messageContext = new DefaultMessageContext(messageSource);
		Serializable messagesMemento = (Serializable) getFlashScope().extract("messagesMemento");
		if (messagesMemento != null) {
			messageContext.restoreMessages(messagesMemento);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
