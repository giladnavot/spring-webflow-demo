---
title: The SecuredModel class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken> in the Spring Web Flow project. We will discuss:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken> class in <SwmPath>[spring-webflow/…/model/SecuredModel.java](spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java)</SwmPath> is used to support secured elements within a flow, state, or transition. It ensures that the user invoking the element meets the required security attributes; otherwise, access is denied. This model only configures a security attribute in the definition, and the flow execution must also be secured with a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="20:10:10" line-data="import org.springframework.webflow.security.SecurityFlowExecutionListener;">`SecurityFlowExecutionListener`</SwmToken>.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" line="40">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken> is a constructor that initializes the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken> with the provided security attributes.

```java
	/**
	 * Create a security settings model
	 * @param attributes the security attributes
	 */
	public SecuredModel(String attributes) {
		setAttributes(attributes);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" line="48">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="48:5:5" line-data="	public boolean isMergeableWith(Model model) {">`isMergeableWith`</SwmToken> checks if the current <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="49:10:10" line-data="		if (!(model instanceof SecuredModel)) {">`SecuredModel`</SwmToken> can be merged with another model. It returns true if the other model is also a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="49:10:10" line-data="		if (!(model instanceof SecuredModel)) {">`SecuredModel`</SwmToken> and has the same attributes.

```java
	public boolean isMergeableWith(Model model) {
		if (!(model instanceof SecuredModel)) {
			return false;
		}
		SecuredModel secured = (SecuredModel) model;
		return ObjectUtils.nullSafeEquals(getAttributes(), secured.getAttributes());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" line="56">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="56:5:5" line-data="	public void merge(Model model) {">`merge`</SwmToken> merges the current <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="57:1:1" line-data="		SecuredModel secured = (SecuredModel) model;">`SecuredModel`</SwmToken> with another <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="57:1:1" line-data="		SecuredModel secured = (SecuredModel) model;">`SecuredModel`</SwmToken>. It sets the match attribute by merging the current match with the match of the other model.

```java
	public void merge(Model model) {
		SecuredModel secured = (SecuredModel) model;
		setMatch(merge(getMatch(), secured.getMatch()));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" line="61">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="61:5:5" line-data="	public Model createCopy() {">`createCopy`</SwmToken> creates and returns a copy of the current <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="62:1:1" line-data="		SecuredModel copy = new SecuredModel(attributes);">`SecuredModel`</SwmToken>, including its attributes and match.

```java
	public Model createCopy() {
		SecuredModel copy = new SecuredModel(attributes);
		copy.setMatch(match);
		return copy;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" line="67">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="70:5:5" line-data="	public String getAttributes() {">`getAttributes`</SwmToken> returns the security attributes of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken>.

```java
	/**
	 * @return the attributes
	 */
	public String getAttributes() {
		return attributes;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" line="74">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="77:5:5" line-data="	public void setAttributes(String attributes) {">`setAttributes`</SwmToken> sets the security attributes of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken>. If the provided attributes are not empty, they are set; otherwise, they are set to null.

```java
	/**
	 * @param attributes the attributes to set
	 */
	public void setAttributes(String attributes) {
		if (StringUtils.hasText(attributes)) {
			this.attributes = attributes;
		} else {
			this.attributes = null;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" line="85">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="88:5:5" line-data="	public String getMatch() {">`getMatch`</SwmToken> returns the match attribute of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken>.

```java
	/**
	 * @return the match
	 */
	public String getMatch() {
		return match;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" line="92">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="95:5:5" line-data="	public void setMatch(String match) {">`setMatch`</SwmToken> sets the match attribute of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/SecuredModel.java" pos="44:3:3" line-data="	public SecuredModel(String attributes) {">`SecuredModel`</SwmToken>. If the provided match is not empty, it is set; otherwise, it is set to null.

```java
	/**
	 * @param match the match to set
	 */
	public void setMatch(String match) {
		if (StringUtils.hasText(match)) {
			this.match = match;
		} else {
			this.match = null;
		}
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" line="968">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="120:4:4" line-data="public class FlowModelFlowBuilder extends AbstractFlowBuilder {">`FlowModelFlowBuilder`</SwmToken>, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="968:7:7" line-data="	private void parseAndPutSecured(SecuredModel secured, MutableAttributeMap&lt;Object&gt; attributes) {">`SecuredModel`</SwmToken> is parsed and added to the attributes using the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="968:5:5" line-data="	private void parseAndPutSecured(SecuredModel secured, MutableAttributeMap&lt;Object&gt; attributes) {">`parseAndPutSecured`</SwmToken> method.

```java
	private void parseAndPutSecured(SecuredModel secured, MutableAttributeMap<Object> attributes) {
		if (secured != null) {
			SecurityRule rule = new SecurityRule();
			rule.setAttributes(SecurityRule.commaDelimitedListToSecurityAttributes(secured.getAttributes()));
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
