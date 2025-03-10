---
title: Search Functionality in Webflow
---
# Understanding Search in Webflow

Search in Webflow involves a flow definition that manages the process of searching and displaying results.

## Flow Definition

The flow starts with the <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="6:9:9" line-data="	&lt;view-state id=&quot;enterCriteria&quot; view=&quot;searchCriteria&quot;&gt;">`enterCriteria`</SwmToken> <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="6:2:4" line-data="	&lt;view-state id=&quot;enterCriteria&quot; view=&quot;searchCriteria&quot;&gt;">`view-state`</SwmToken>, where users input their search criteria. Upon rendering this state, the <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="8:7:9" line-data="			&lt;evaluate expression=&quot;formAction.setupForm&quot; /&gt;">`formAction.setupForm`</SwmToken> method is evaluated to set up the form.

<SwmSnippet path="/spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" line="10">

---

When the search action is triggered, the flow transitions to the <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="10:13:13" line-data="		&lt;transition on=&quot;search&quot; to=&quot;displayResults&quot;&gt;">`displayResults`</SwmToken> <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="6:2:4" line-data="	&lt;view-state id=&quot;enterCriteria&quot; view=&quot;searchCriteria&quot;&gt;">`view-state`</SwmToken>. During this transition, the <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="11:7:9" line-data="			&lt;evaluate expression=&quot;formAction.bindAndValidate&quot; /&gt;">`formAction.bindAndValidate`</SwmToken> method is called to bind the input data and validate it.

```xml
		<transition on="search" to="displayResults">
			<evaluate expression="formAction.bindAndValidate" />
		</transition>
```

---

</SwmSnippet>

## Displaying Search Results

In the <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="10:13:13" line-data="		&lt;transition on=&quot;search&quot; to=&quot;displayResults&quot;&gt;">`displayResults`</SwmToken> <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="6:2:4" line-data="	&lt;view-state id=&quot;enterCriteria&quot; view=&quot;searchCriteria&quot;&gt;">`view-state`</SwmToken>, the <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="17:7:12" line-data="			&lt;evaluate expression=&quot;phonebook.search(searchCriteria)&quot; result=&quot;flowScope.results&quot; /&gt;">`phonebook.search(searchCriteria)`</SwmToken> method is evaluated to perform the search based on the criteria provided. The results of the search are stored in the <SwmToken path="spring-webflow/src/test/java/org/springframework/webflow/test/search-flow.xml" pos="17:18:20" line-data="			&lt;evaluate expression=&quot;phonebook.search(searchCriteria)&quot; result=&quot;flowScope.results&quot; /&gt;">`flowScope.results`</SwmToken> for display.

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
