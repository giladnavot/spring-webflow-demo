---
title: The AbstractModel class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractMappingModel.java" pos="25:10:10" line-data="public abstract class AbstractMappingModel extends AbstractModel {">`AbstractModel`</SwmToken> in the Spring Web Flow project. We will cover:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractMappingModel.java" pos="25:10:10" line-data="public abstract class AbstractMappingModel extends AbstractModel {">`AbstractModel`</SwmToken> is.
2. Variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractMappingModel.java" pos="25:10:10" line-data="public abstract class AbstractMappingModel extends AbstractModel {">`AbstractModel`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractMappingModel.java" pos="25:10:10" line-data="public abstract class AbstractMappingModel extends AbstractModel {">`AbstractModel`</SwmToken>

<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractMappingModel.java" pos="25:10:10" line-data="public abstract class AbstractMappingModel extends AbstractModel {">`AbstractModel`</SwmToken> is an abstract class in the Spring Web Flow project, located in <SwmPath>[spring-webflow/…/model/AbstractModel.java](spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java)</SwmPath>. It provides basic merge functions that can be utilized by other models. The primary purpose of this class is to offer a set of utility methods for merging different types of objects, strings, model elements, and lists.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" line="30">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" pos="32:16:16" line-data="	 * @param child the child object to merge">`merge`</SwmToken> merges two objects. If the child object is null, the parent object is returned; otherwise, the child object is returned.

```java
	/**
	 * Merge two objects. If the child is null, the parent will be returned. Else the child will be returned.
	 * @param child the child object to merge
	 * @param parent the parent object to merge
	 * @return the merged string
	 */
	protected Object merge(Object child, Object parent) {
		if (child == null) {
			return parent;
		} else {
			return child;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" line="44">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" pos="46:16:16" line-data="	 * @param child the child string to merge">`merge`</SwmToken> merges two strings. If the child string is null, the parent string is returned; otherwise, the child string is returned.

```java
	/**
	 * Merge two strings. If the child is null, the parent will be returned. Else the child will be returned.
	 * @param child the child string to merge
	 * @param parent the parent string to merge
	 * @return the merged string
	 */
	@SuppressWarnings("RedundantCast")
	protected String merge(String child, String parent) {
		return (String) merge((Object) child, (Object) parent);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" line="55">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" pos="58:18:18" line-data="	 * @param child the child model element to merge">`merge`</SwmToken> merges two model elements. If the child model is null, the parent model is returned; otherwise, the parent model is merged into the child model, and the result is returned.

```java
	/**
	 * Merge two model elements. If the child is null, the parent will be returned. Else the parent element will be
	 * merged into the child element with the result returned
	 * @param child the child model element to merge
	 * @param parent the parent model element to merge
	 * @return the merged element model
	 */
	protected Model merge(Model child, Model parent) {
		if (child == null) {
			if (parent == null) {
				return null;
			} else {
				return parent.createCopy();
			}
		} else if (parent == null) {
			return child;
		} else {
			child.merge(parent);
			return child;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" line="77">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" pos="79:30:30" line-data="	 * added. Mergeable elements in both lists will be merged according to that element merge rules. New items are added">`merge`</SwmToken> merges two lists. All child elements will be in the merged list, and all parent elements not in the child list will be added. Mergeable elements in both lists will be merged according to the element merge rules. New items are added to the end of the list.

```java
	/**
	 * Merge two lists. All child element will be in the merged list. All parent elements not in the child list will be
	 * added. Mergeable elements in both lists will be merged according to that element merge rules. New items are added
	 * to the end of the list
	 * @param child the child list to merge
	 * @param parent the parent list to merge
	 * @return the merged list
	 */
	protected <T extends Model> LinkedList<T> merge(LinkedList<T> child, LinkedList<T> parent) {
		return merge(child, parent, true);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" line="89">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" pos="91:30:30" line-data="	 * added. Mergeable elements in both lists will be merged according to that element merge rules.">`merge`</SwmToken> merges two lists with an option to add new items at the end or the beginning of the list. All child elements will be in the merged list, and all parent elements not in the child list will be added. Mergeable elements in both lists will be merged according to the element merge rules.

```java
	/**
	 * Merge two lists. All child element will be in the merged list. All parent elements not in the child list will be
	 * added. Mergeable elements in both lists will be merged according to that element merge rules.
	 * @param child the child list to merge
	 * @param parent the parent list to merge
	 * @param addAtEnd if true new items will be added at the end of the list, otherwise the beginning
	 * @return the merged list
	 */
	protected <T extends Model> LinkedList<T> merge(LinkedList<T> child, LinkedList<T> parent, boolean addAtEnd) {
		if (child == null) {
			return copyList(parent);
		}
		if (parent == null) {
			return child;
		}
		if (!addAtEnd) {
			parent = new LinkedList<>(parent);
			Collections.reverse(parent);
		}
		for (T parentModel : parent) {
			addOrMerge(child, parentModel, addAtEnd);
		}
		return child;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" line="114">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" pos="114:13:13" line-data="	private &lt;T extends Model&gt; void addOrMerge(LinkedList&lt;T&gt; list, T modelToMerge, boolean addAtEnd) {">`addOrMerge`</SwmToken> adds or merges a model element into a list. If the model element is mergeable with an existing element in the list, it merges them; otherwise, it adds a copy of the model element to the list.

```java
	private <T extends Model> void addOrMerge(LinkedList<T> list, T modelToMerge, boolean addAtEnd) {
		for (T model : list) {
			if (model.isMergeableWith(modelToMerge)) {
				model.merge(modelToMerge);
				return;
			}
		}
		@SuppressWarnings("unchecked")
		T copy = (T) modelToMerge.createCopy();
		if (addAtEnd) {
			list.addLast(copy);
		} else {
			list.addFirst(copy);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" line="130">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" pos="130:5:5" line-data="	protected Model copy(Model model) {">`copy`</SwmToken> creates a copy of a model element. If the model element is null, it returns null; otherwise, it returns a copy of the model element.

```java
	protected Model copy(Model model) {
		if (model == null) {
			return null;
		}
		return model.createCopy();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" line="137">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" pos="138:16:16" line-data="	protected &lt;T extends Model&gt; LinkedList&lt;T&gt; copyList(LinkedList&lt;T&gt; list) {">`copyList`</SwmToken> creates a copy of a list of model elements. If the list is null, it returns null; otherwise, it returns a new list with copies of the model elements.

```java
	@SuppressWarnings("unchecked")
	protected <T extends Model> LinkedList<T> copyList(LinkedList<T> list) {
		if (list == null) {
			return null;
		}
		LinkedList<T> copy = new LinkedList<>();
		for (T model : list) {
			copy.add((T) model.createCopy());
		}
		return copy;
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractMappingModel.java" line="25">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractMappingModel.java" pos="25:6:6" line-data="public abstract class AbstractMappingModel extends AbstractModel {">`AbstractMappingModel`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractMappingModel.java" pos="25:10:10" line-data="public abstract class AbstractMappingModel extends AbstractModel {">`AbstractModel`</SwmToken> and includes a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractMappingModel.java" pos="27:5:5" line-data="	private String name;">`name`</SwmToken> property.

```java
public abstract class AbstractMappingModel extends AbstractModel {

	private String name;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
