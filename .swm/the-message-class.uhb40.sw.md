---
title: The Message class
---
This document will provide an overview of the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="45:3:3" line-data="	public Message(Object source, String text, Severity severity) {">`Message`</SwmToken> class in the Spring Web Flow project. We will cover:

1. What the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="45:3:3" line-data="	public Message(Object source, String text, Severity severity) {">`Message`</SwmToken> class is and its purpose.
2. The variables and functions defined in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="45:3:3" line-data="	public Message(Object source, String text, Severity severity) {">`Message`</SwmToken> class.

# What is Message

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="45:3:3" line-data="	public Message(Object source, String text, Severity severity) {">`Message`</SwmToken> class in <SwmPath>[spring-binding/…/message/Message.java](spring-binding/src/main/java/org/springframework/binding/message/Message.java)</SwmPath> is an object of communication that provides text information. For example, a validation message may inform a web application user that a business rule was violated. A message can be associated with a particular source element or component, has text providing the basis for communication, and has severity indicating the priority or intensity of the message for its receiver.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/Message.java" line="39">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="45:3:3" line-data="	public Message(Object source, String text, Severity severity) {">`Message`</SwmToken> is a constructor that creates a new message. It initializes the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="41:6:6" line-data="	 * @param source the source of the message">`source`</SwmToken>, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="42:6:6" line-data="	 * @param text the message text">`text`</SwmToken>, and <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="43:6:6" line-data="	 * @param severity the message severity">`severity`</SwmToken> variables.

```java
	/**
	 * Creates a new message.
	 * @param source the source of the message
	 * @param text the message text
	 * @param severity the message severity
	 */
	public Message(Object source, String text, Severity severity) {
		this.source = source;
		this.text = text;
		this.severity = severity;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/Message.java" line="51">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="57:5:5" line-data="	public Object getSource() {">`getSource`</SwmToken> returns a reference to the source element this message is associated with. This could be a field on a form in UI, or null (or empty "" in the case of global bean validation) if the message is not associated with any particular element.

```java
	/**
	 * A reference to the source element this message is associated with. This could be a field on a form in UI, or null
	 * (or empty "" in the case of global bean validation) if the message is not associated with a any particular
	 * element.
	 * @return the source
	 */
	public Object getSource() {
		return source;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/Message.java" line="61">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="65:5:5" line-data="	public String getText() {">`getText`</SwmToken> returns the message text. The text is the message's communication payload.

```java
	/**
	 * The message text. The text is the message's communication payload.
	 * @return the message text
	 */
	public String getText() {
		return text;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/Message.java" line="69">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="73:5:5" line-data="	public Severity getSeverity() {">`getSeverity`</SwmToken> returns the severity of this message. The severity indicates the intensity or priority of the communication.

```java
	/**
	 * The severity of this message. The severity indicates the intensity or priority of the communication.
	 * @return the message severity
	 */
	public Severity getSeverity() {
		return severity;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/Message.java" line="77">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="81:5:5" line-data="	public boolean hasField() {">`hasField`</SwmToken> checks whether the message is associated with a field. It returns `true` if the source is a String that has text; `false` otherwise.

```java
	/**
	 * Whether the message is associated with a field.
	 * @return {@code true} if the source is a String that has text; {@code false} otherwise.
	 */
	public boolean hasField() {
		if (this.source instanceof String) {
			return StringUtils.hasText((String) this.source);
		} else {
			return false;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/Message.java" line="89">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/Message.java" pos="89:5:5" line-data="	public String toString() {">`toString`</SwmToken> returns a string representation of the message, including the source, severity, and text.

```java
	public String toString() {
		return new ToStringCreator(this).append("source", source).append("severity", severity).append("text", text)
				.toString();
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-faces/src/main/java/org/springframework/faces/webflow/FlowFacesContext.java" line="169">

---

In the <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowFacesContext.java" pos="62:4:4" line-data="public class FlowFacesContext extends FacesContextWrapper {">`FlowFacesContext`</SwmToken> class, <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowFacesContext.java" pos="171:4:4" line-data="		for (Message message : this.context.getMessageContext().getAllMessages()) {">`Message`</SwmToken> is used to retrieve client IDs associated with messages, convert messages to <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowFacesContext.java" pos="214:5:5" line-data="	public List&lt;FacesMessage&gt; getMessageList() {">`FacesMessage`</SwmToken> objects, and filter messages based on specific criteria.

```java
	public Iterator<String> getClientIdsWithMessages() {
		Set<String> clientIds = new LinkedHashSet<>();
		for (Message message : this.context.getMessageContext().getAllMessages()) {
			Object source = message.getSource();
			if (source instanceof String) {
				clientIds.add((String) source);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-faces/src/main/java/org/springframework/faces/webflow/FlowFacesContext.java" line="214">

---

&nbsp;

```java
	public List<FacesMessage> getMessageList() {
		Message[] messages = this.context.getMessageContext().getAllMessages();
		return asFacesMessages(messages);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-faces/src/main/java/org/springframework/faces/webflow/FlowFacesContext.java" line="231">

---

&nbsp;

```java
	public List<FacesMessage> getMessageList(final String clientId) {
		final FacesMessageSource source = new FacesMessageSource(clientId);
		Message[] messages = this.context.getMessageContext().getMessagesByCriteria(message ->
				ObjectUtils.nullSafeEquals(message.getSource(), source)
						|| ObjectUtils.nullSafeEquals(message.getSource(), clientId));
		return asFacesMessages(messages);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="287">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="60:4:4" line-data="public class BindingModel extends AbstractErrors implements BindingResult {">`BindingModel`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="287:18:18" line-data="	private &lt;T extends ObjectError&gt; List&lt;T&gt; toErrors(Message[] messages, ObjectErrorFactory&lt;T&gt; errorFactory) {">`Message`</SwmToken> is used to convert messages to error objects and to filter messages based on severity and source.

```java
	private <T extends ObjectError> List<T> toErrors(Message[] messages, ObjectErrorFactory<T> errorFactory) {
		if (messages == null || messages.length == 0) {
			return Collections.emptyList();
		}
		ArrayList<T> errors = new ArrayList<>(messages.length);
		for (Message message : messages) {
			T error = errorFactory.get(objectName, message);
			if (error != null) {
				errors.add(error);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="335">

---

&nbsp;

```java
		public boolean test(Message message) {
			return message.getSeverity() == Severity.ERROR && field.equals(message.getSource());
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="348">

---

&nbsp;

```java
		public boolean test(Message message) {
			return message.getSeverity() == Severity.ERROR && message.getSource() instanceof String
					&& ((String) message.getSource()).startsWith(fieldPrefix);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageResolver.java" line="44">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageResolver.java" pos="24:4:4" line-data="public class DefaultMessageResolver implements MessageResolver, MessageSourceResolvable {">`DefaultMessageResolver`</SwmToken> class, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageResolver.java" pos="44:3:3" line-data="	public Message resolveMessage(MessageSource messageSource, Locale locale) {">`Message`</SwmToken> is used to resolve messages from a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageResolver.java" pos="44:7:7" line-data="	public Message resolveMessage(MessageSource messageSource, Locale locale) {">`MessageSource`</SwmToken> based on the current locale.

```java
	public Message resolveMessage(MessageSource messageSource, Locale locale) {
		return new Message(source, postProcessMessageText(messageSource.getMessage(this, locale)), severity);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/MessageContext.java" line="27">

---

In the <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowFacesContext.java" pos="158:33:33" line-data="	 * Translates a FacesMessage to a Spring Web Flow message and adds it to the current MessageContext">`MessageContext`</SwmToken> interface, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/MessageContext.java" pos="27:1:1" line-data="	Message[] getAllMessages();">`Message`</SwmToken> is used to retrieve all messages, messages by source, and messages that meet specific criteria.

```java
	Message[] getAllMessages();

	/**
	 * Get all messages in this context for the source provided.
	 * @param source the source associated with messages, or null for global messages
	 * @return the source's messages
	 */
	Message[] getMessagesBySource(Object source);

	/**
	 * Get all messages that meet the given result criteria.
	 * @param criteria the message criteria
	 */
	Message[] getMessagesByCriteria(MessageCriteria criteria);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="47">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="40:4:4" line-data="public class DefaultMessageContext implements StateManageableMessageContext {">`DefaultMessageContext`</SwmToken> class, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" pos="47:10:10" line-data="	private Map&lt;Object, List&lt;Message&gt;&gt; sourceMessages =">`Message`</SwmToken> is used to store and retrieve messages associated with different sources.

```java
	private Map<Object, List<Message>> sourceMessages =
			new AbstractCachingMapDecorator<Object, List<Message>>(new LinkedHashMap<>()) {

				protected List<Message> create(Object source) {
					return new ArrayList<>();
				}
			};
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/DefaultMessageContext.java" line="77">

---

&nbsp;

```java
	public Message[] getAllMessages() {
		List<Message> messages = new ArrayList<>();
		for (List<Message> list : sourceMessages.values()) {
			messages.addAll(list);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/MessageResolver.java" line="38">

---

In the <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowFacesContext.java" pos="42:10:10" line-data="import org.springframework.binding.message.MessageResolver;">`MessageResolver`</SwmToken> interface, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/MessageResolver.java" pos="38:1:1" line-data="	Message resolveMessage(MessageSource messageSource, Locale locale);">`Message`</SwmToken> is used to resolve messages from a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/MessageResolver.java" pos="38:5:5" line-data="	Message resolveMessage(MessageSource messageSource, Locale locale);">`MessageSource`</SwmToken> based on the current locale.

```java
	Message resolveMessage(MessageSource messageSource, Locale locale);
}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/MessageCriteria.java" line="30">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/MessageContext.java" pos="40:7:7" line-data="	Message[] getMessagesByCriteria(MessageCriteria criteria);">`MessageCriteria`</SwmToken> interface, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/MessageCriteria.java" pos="30:5:5" line-data="	boolean test(Message message);">`Message`</SwmToken> is used to test if a message meets specific criteria.

```java
	boolean test(Message message);
}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/message/MessageContextErrors.java" line="117">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/MessageContextErrors.java" pos="41:4:4" line-data="public class MessageContextErrors extends AbstractErrors {">`MessageContextErrors`</SwmToken> class, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/message/MessageContextErrors.java" pos="118:1:1" line-data="		Message[] messages = messageContext.getMessagesByCriteria(GLOBAL_ERROR);">`Message`</SwmToken> is used to retrieve global and field-specific errors.

```java
	public List<ObjectError> getGlobalErrors() {
		Message[] messages = messageContext.getMessagesByCriteria(GLOBAL_ERROR);
		if (messages.length == 0) {
			return Collections.emptyList();
		}
		List<ObjectError> errors = new ArrayList<>(messages.length);
		for (Message message : messages) {
			errors.add(new ObjectError(objectName, message.getText()));
		}
		return Collections.unmodifiableList(errors);
	}

	public List<FieldError> getFieldErrors() {
		Message[] messages = messageContext.getMessagesByCriteria(FIELD_ERROR);
		if (messages.length == 0) {
			return Collections.emptyList();
		}
		List<FieldError> errors = new ArrayList<>(messages.length);
		for (Message message : messages) {
			errors.add(new FieldError(objectName, (String) message.getSource(), message.getText()));
		}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
