---
title: Overview of Action in Web Flow
---
# Overview of Action in Web Flow

Action refers to a core concept in Spring Web Flow that encapsulates a piece of business logic to be executed as part of a flow.

## Purpose of Action

Actions are typically used to perform tasks such as form submission handling, data validation, and invoking business services.

## Configuring Actions

In Spring Web Flow, actions can be configured declaratively within a flow definition, allowing for a clean separation of concerns between the flow logic and the business logic.

## Driving Flow Execution

Actions can return events that drive the flow execution forward, determining the next state or view to transition to based on the outcome of the action.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/action/FormAction.java" line="422">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/FormAction.java" pos="725:21:21" line-data="	 * The returned form object will become the {@link FormObjectAccessor#setCurrentFormObject(Object, ScopeType)">`FormObjectAccessor`</SwmToken> class, for example, is used within actions to manage form objects and their associated errors in the flow execution request context.

```java
	protected void initAction() {
		if (getValidator() != null) {
			if (getFormObjectClass() != null && !getValidator().supports(getFormObjectClass())) {
				throw new IllegalArgumentException("Validator [" + getValidator()
						+ "] does not support form object class [" + getFormObjectClass() + "]");
			}
			// signature: public void ${validateMethodName}(${formObjectClass}, Errors)
			validateMethodInvoker = new DispatchMethodInvoker(getValidator(), getFormObjectClass(), Errors.class);
		}
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
