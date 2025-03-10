---
title: Search Overview
---
# Search Overview

Search refers to the functionality that allows users to query and retrieve specific data from a dataset. This functionality is essential for users to efficiently find and retrieve specific information from a large dataset.

<SwmSnippet path="/spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" line="10">

---

The search functionality is implemented using a flow definition in the <SwmPath>[spring-webflow/…/test/search-flow.xml](spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml)</SwmPath> file. This file defines the states and transitions involved in the search process.

```xml
		<transition on="search" to="displayResults">
			<evaluate expression="formAction.bindAndValidate" />
		</transition>
```

---

</SwmSnippet>

# Search Event

When a search event is triggered, the flow transitions to the <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="10:13:13" line-data="		&lt;transition on=&quot;search&quot; to=&quot;displayResults&quot;&gt;">`displayResults`</SwmToken> state. This state is responsible for displaying the search results to the user.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/action/FormAction.java" line="476">

---

During the transition to the <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="10:13:13" line-data="		&lt;transition on=&quot;search&quot; to=&quot;displayResults&quot;&gt;">`displayResults`</SwmToken> state, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/FormAction.java" pos="476:5:5" line-data="	public Event bindAndValidate(RequestContext context) throws Exception {">`bindAndValidate`</SwmToken> method of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/FormAction.java" pos="118:13:13" line-data=" * custom action method in your FormAction subclass that does just that. Simply invoke it as either a chained action as">`FormAction`</SwmToken> class is called. This method binds incoming request parameters to the form object and validates them to ensure they meet the required criteria.

```java
	public Event bindAndValidate(RequestContext context) throws Exception {
		if (logger.isDebugEnabled()) {
			logger.debug("Executing bind");
		}
		Object formObject = getFormObject(context);
		DataBinder binder = createBinder(context, formObject);
		doBind(context, binder);
		if (getValidator() != null && validationEnabled(context)) {
			if (logger.isDebugEnabled()) {
				logger.debug("Executing validation");
			}
			doValidate(context, formObject, binder.getBindingResult());
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
