---
title: Search Functionality in Spring Binding
---
# Overview of Search in Spring Binding

Search in Spring Binding involves filtering and retrieving specific mapping results based on defined criteria. This functionality is essential for efficiently accessing and manipulating data within the Spring framework.

## <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingResults.java" pos="30:4:4" line-data="public class DefaultMappingResults implements MappingResults {">`DefaultMappingResults`</SwmToken> Class

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingResults.java" pos="30:4:4" line-data="public class DefaultMappingResults implements MappingResults {">`DefaultMappingResults`</SwmToken> class provides methods to access and manipulate the results of a mapping operation. It is a core component in implementing search functionality within Spring Binding.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingResults.java" line="81">

---

One of the key methods in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingResults.java" pos="30:4:4" line-data="public class DefaultMappingResults implements MappingResults {">`DefaultMappingResults`</SwmToken> class is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingResults.java" pos="81:8:8" line-data="	public List&lt;MappingResult&gt; getResults(MappingResultsCriteria criteria) {">`getResults`</SwmToken>. This method takes a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingResults.java" pos="81:10:10" line-data="	public List&lt;MappingResult&gt; getResults(MappingResultsCriteria criteria) {">`MappingResultsCriteria`</SwmToken> object as a parameter to filter the mapping results. The criteria define the conditions that the results must meet to be included in the final output.

```java
	public List<MappingResult> getResults(MappingResultsCriteria criteria) {
		List<MappingResult> results = new ArrayList<>();
		for (MappingResult result : mappingResults) {
			if (criteria.test(result)) {
				results.add(result);
			}
		}
		return Collections.unmodifiableList(results);
	}
```

---

</SwmSnippet>

## How <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingResults.java" pos="81:8:8" line-data="	public List&lt;MappingResult&gt; getResults(MappingResultsCriteria criteria) {">`getResults`</SwmToken> Works

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingResults.java" pos="81:8:8" line-data="	public List&lt;MappingResult&gt; getResults(MappingResultsCriteria criteria) {">`getResults`</SwmToken> method iterates through the list of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/mapping/impl/DefaultMappingResults.java" pos="81:5:5" line-data="	public List&lt;MappingResult&gt; getResults(MappingResultsCriteria criteria) {">`MappingResult`</SwmToken> objects and applies the criteria to each result. Only the results that meet the criteria are added to the final list. This filtered list is then returned as an unmodifiable list, ensuring that the results cannot be altered after retrieval.

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
