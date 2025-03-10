---
title: The FlowModel class
---
This document will cover the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken> class in detail. We will explain:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken> class in <SwmPath>[spring-webflow/…/model/FlowModel.java](spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java)</SwmPath> is a model support class for flows. It defines exactly one flow definition, which is composed of one or more states that define the steps of a conversation. One of these steps is the start state, which defines the conversation's starting point. Additionally, a flow may exhibit characteristics such as being annotated with attributes, being secured, managing persistent objects, instantiating instance variables, mapping input and output, executing actions at start and end times, defining transitions shared by all states, handling exceptions, and importing local bean definition files.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="78">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken> is the constructor for the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken> class. It initializes a new instance of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * Create a flow model
	 */
	public FlowModel() {
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="84">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="84:5:5" line-data="	public boolean isMergeableWith(Model model) {">`isMergeableWith`</SwmToken> checks if the given model can be merged with the current <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="85:9:9" line-data="		if ((model instanceof FlowModel)) {">`FlowModel`</SwmToken> instance. It returns true if the model is an instance of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="85:9:9" line-data="		if ((model instanceof FlowModel)) {">`FlowModel`</SwmToken>, otherwise false.

```java
	public boolean isMergeableWith(Model model) {
		if ((model instanceof FlowModel)) {
			return true;
		} else {
			return false;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="92">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="92:5:5" line-data="	public void merge(Model model) {">`merge`</SwmToken> merges the given model into the current <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="93:1:1" line-data="		FlowModel flow = (FlowModel) model;">`FlowModel`</SwmToken> instance. It sets various properties of the current instance by merging them with the corresponding properties of the given model.

```java
	public void merge(Model model) {
		FlowModel flow = (FlowModel) model;
		setParent(null);
		setStartStateId(merge(getStartStateId(), flow.getStartStateId()));
		setAttributes(merge(getAttributes(), flow.getAttributes()));
		setSecured((SecuredModel) merge(getSecured(), flow.getSecured()));
		setPersistenceContext((PersistenceContextModel) merge(getPersistenceContext(), flow.getPersistenceContext()));
		setVars(merge(getVars(), flow.getVars(), false));
		setInputs(merge(getInputs(), flow.getInputs()));
		setOutputs(merge(getOutputs(), flow.getOutputs()));
		setOnStartActions(merge(getOnStartActions(), flow.getOnStartActions(), false));
		setStates(merge(getStates(), flow.getStates()));
		setGlobalTransitions(merge(getGlobalTransitions(), flow.getGlobalTransitions()));
		setOnEndActions(merge(getOnEndActions(), flow.getOnEndActions(), false));
		setExceptionHandlers(merge(getExceptionHandlers(), flow.getExceptionHandlers()));
		setBeanImports(merge(getBeanImports(), flow.getBeanImports()));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="110">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="110:5:5" line-data="	public Model createCopy() {">`createCopy`</SwmToken> creates and returns a copy of the current <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="111:1:1" line-data="		FlowModel copy = new FlowModel();">`FlowModel`</SwmToken> instance. It copies all properties of the current instance to the new instance.

```java
	public Model createCopy() {
		FlowModel copy = new FlowModel();
		copy.setAbstract(abztract);
		copy.setParent(parent);
		copy.setStartStateId(startStateId);
		copy.setAttributes(copyList(attributes));
		copy.setSecured((SecuredModel) copy(secured));
		copy.setPersistenceContext((PersistenceContextModel) copy(persistenceContext));
		copy.setVars(copyList(vars));
		copy.setInputs(copyList(inputs));
		copy.setOutputs(copyList(outputs));
		copy.setOnStartActions(copyList(onStartActions));
		copy.setStates(copyList(states));
		copy.setGlobalTransitions(copyList(globalTransitions));
		copy.setOnEndActions(copyList(onEndActions));
		copy.setExceptionHandlers(copyList(exceptionHandlers));
		copy.setBeanImports(copyList(beanImports));
		return copy;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="130">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="133:5:5" line-data="	public String getAbstract() {">`getAbstract`</SwmToken> returns the abstract property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @return the abstract
	 */
	public String getAbstract() {
		return abztract;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="137">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="140:5:5" line-data="	public void setAbstract(String abztract) {">`setAbstract`</SwmToken> sets the abstract property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @param abztract the abstract to set
	 */
	public void setAbstract(String abztract) {
		if (StringUtils.hasText(abztract)) {
			this.abztract = abztract;
		} else {
			this.abztract = null;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="148">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="151:5:5" line-data="	public String getParent() {">`getParent`</SwmToken> returns the parent property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @return the parent
	 */
	public String getParent() {
		return parent;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="155">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="158:5:5" line-data="	public void setParent(String parent) {">`setParent`</SwmToken> sets the parent property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @param parent the parent to set
	 */
	public void setParent(String parent) {
		if (StringUtils.hasText(parent)) {
			this.parent = parent;
		} else {
			this.parent = null;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="166">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="169:5:5" line-data="	public String getStartStateId() {">`getStartStateId`</SwmToken> returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="170:3:3" line-data="		return startStateId;">`startStateId`</SwmToken> property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @return the id of the flow's start state
	 */
	public String getStartStateId() {
		return startStateId;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="173">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="176:5:5" line-data="	public void setStartStateId(String startStateId) {">`setStartStateId`</SwmToken> sets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="174:6:6" line-data="	 * @param startStateId the id of the flow&#39;s start state to set">`startStateId`</SwmToken> property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @param startStateId the id of the flow's start state to set
	 */
	public void setStartStateId(String startStateId) {
		if (StringUtils.hasText(startStateId)) {
			this.startStateId = startStateId;
		} else {
			this.startStateId = null;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="184">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="187:8:8" line-data="	public LinkedList&lt;AttributeModel&gt; getAttributes() {">`getAttributes`</SwmToken> returns the attributes property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @return the attributes
	 */
	public LinkedList<AttributeModel> getAttributes() {
		return attributes;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="191">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="194:5:5" line-data="	public void setAttributes(LinkedList&lt;AttributeModel&gt; attributes) {">`setAttributes`</SwmToken> sets the attributes property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @param attributes the attributes to set
	 */
	public void setAttributes(LinkedList<AttributeModel> attributes) {
		this.attributes = attributes;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="198">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="201:5:5" line-data="	public SecuredModel getSecured() {">`getSecured`</SwmToken> returns the secured property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @return the secured
	 */
	public SecuredModel getSecured() {
		return secured;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="205">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="208:5:5" line-data="	public void setSecured(SecuredModel secured) {">`setSecured`</SwmToken> sets the secured property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @param secured the secured to set
	 */
	public void setSecured(SecuredModel secured) {
		this.secured = secured;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="212">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="215:5:5" line-data="	public PersistenceContextModel getPersistenceContext() {">`getPersistenceContext`</SwmToken> returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="216:3:3" line-data="		return persistenceContext;">`persistenceContext`</SwmToken> property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @return the persistence context
	 */
	public PersistenceContextModel getPersistenceContext() {
		return persistenceContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="219">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="222:5:5" line-data="	public void setPersistenceContext(PersistenceContextModel persistenceContext) {">`setPersistenceContext`</SwmToken> sets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="220:6:6" line-data="	 * @param persistenceContext the persistence context to set">`persistenceContext`</SwmToken> property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @param persistenceContext the persistence context to set
	 */
	public void setPersistenceContext(PersistenceContextModel persistenceContext) {
		this.persistenceContext = persistenceContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="226">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="229:8:8" line-data="	public LinkedList&lt;VarModel&gt; getVars() {">`getVars`</SwmToken> returns the vars property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @return the vars
	 */
	public LinkedList<VarModel> getVars() {
		return vars;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="233">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="236:5:5" line-data="	public void setVars(LinkedList&lt;VarModel&gt; vars) {">`setVars`</SwmToken> sets the vars property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @param vars the vars to set
	 */
	public void setVars(LinkedList<VarModel> vars) {
		this.vars = vars;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="240">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="243:8:8" line-data="	public LinkedList&lt;InputModel&gt; getInputs() {">`getInputs`</SwmToken> returns the inputs property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @return the input mappings
	 */
	public LinkedList<InputModel> getInputs() {
		return inputs;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="247">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="250:5:5" line-data="	public void setInputs(LinkedList&lt;InputModel&gt; inputs) {">`setInputs`</SwmToken> sets the inputs property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @param inputs the input mappings to set
	 */
	public void setInputs(LinkedList<InputModel> inputs) {
		this.inputs = inputs;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="254">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="257:8:8" line-data="	public LinkedList&lt;OutputModel&gt; getOutputs() {">`getOutputs`</SwmToken> returns the outputs property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @return the output mappings
	 */
	public LinkedList<OutputModel> getOutputs() {
		return outputs;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="261">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="264:5:5" line-data="	public void setOutputs(LinkedList&lt;OutputModel&gt; outputs) {">`setOutputs`</SwmToken> sets the outputs property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @param outputs the output mappings to set
	 */
	public void setOutputs(LinkedList<OutputModel> outputs) {
		this.outputs = outputs;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" line="268">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="271:8:8" line-data="	public LinkedList&lt;AbstractActionModel&gt; getOnStartActions() {">`getOnStartActions`</SwmToken> returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="272:3:3" line-data="		return onStartActions;">`onStartActions`</SwmToken> property of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/FlowModel.java" pos="81:3:3" line-data="	public FlowModel() {">`FlowModel`</SwmToken>.

```java
	/**
	 * @return the on start actions
	 */
	public LinkedList<AbstractActionModel> getOnStartActions() {
		return onStartActions;
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" line="283">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="120:4:4" line-data="public class FlowModelFlowBuilder extends AbstractFlowBuilder {">`FlowModelFlowBuilder`</SwmToken> class, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="283:3:3" line-data="	protected FlowModel getFlowModel() {">`FlowModel`</SwmToken> is accessed through the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="283:5:5" line-data="	protected FlowModel getFlowModel() {">`getFlowModel`</SwmToken> method, which returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="284:3:3" line-data="		return flowModel;">`flowModel`</SwmToken> instance.

```java
	protected FlowModel getFlowModel() {
		return flowModel;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/xml/XmlFlowModelBuilder.java" line="206">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/xml/XmlFlowModelBuilder.java" pos="71:4:4" line-data="public class XmlFlowModelBuilder implements FlowModelBuilder {">`XmlFlowModelBuilder`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/xml/XmlFlowModelBuilder.java" pos="206:3:3" line-data="	private FlowModel parseFlow(Element element) {">`FlowModel`</SwmToken> is used to parse flow elements from XML. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/xml/XmlFlowModelBuilder.java" pos="206:5:5" line-data="	private FlowModel parseFlow(Element element) {">`parseFlow`</SwmToken> method creates a new <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/xml/XmlFlowModelBuilder.java" pos="206:3:3" line-data="	private FlowModel parseFlow(Element element) {">`FlowModel`</SwmToken> instance and sets its properties based on the XML element attributes.

```java
	private FlowModel parseFlow(Element element) {
		FlowModel flow = new FlowModel();
		flow.setAbstract(element.getAttribute("abstract"));
		flow.setParent(element.getAttribute("parent"));
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/FlowModelBuilder.java" line="62">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/xml/XmlFlowModelBuilder.java" pos="54:14:14" line-data="import org.springframework.webflow.engine.model.builder.FlowModelBuilder;">`FlowModelBuilder`</SwmToken> interface includes a method <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/FlowModelBuilder.java" pos="62:3:3" line-data="	FlowModel getFlowModel() throws FlowModelBuilderException;">`getFlowModel`</SwmToken> which is responsible for building and returning a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/FlowModelBuilder.java" pos="62:1:1" line-data="	FlowModel getFlowModel() throws FlowModelBuilderException;">`FlowModel`</SwmToken> instance.

```java
	FlowModel getFlowModel() throws FlowModelBuilderException;

```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/DefaultFlowModelHolder.java" line="55">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/DefaultFlowModelHolder.java" pos="37:4:4" line-data="public class DefaultFlowModelHolder implements FlowModelHolder {">`DefaultFlowModelHolder`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/DefaultFlowModelHolder.java" pos="55:5:5" line-data="	public synchronized FlowModel getFlowModel() {">`FlowModel`</SwmToken> is held and managed. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/DefaultFlowModelHolder.java" pos="55:7:7" line-data="	public synchronized FlowModel getFlowModel() {">`getFlowModel`</SwmToken> method returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/DefaultFlowModelHolder.java" pos="55:5:5" line-data="	public synchronized FlowModel getFlowModel() {">`FlowModel`</SwmToken> instance, potentially triggering its assembly if it is not already built.

```java
	public synchronized FlowModel getFlowModel() {
		if (assembling) {
			// must return early assembly result for when a flow calls itself recursively
			return flowModelBuilder.getFlowModel();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/registry/FlowModelRegistryImpl.java" line="50">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/registry/FlowModelRegistryImpl.java" pos="32:4:4" line-data="public class FlowModelRegistryImpl implements FlowModelRegistry, FlowModelHolderLocator {">`FlowModelRegistryImpl`</SwmToken> class implements the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/xml/XmlFlowModelBuilder.java" pos="58:14:14" line-data="import org.springframework.webflow.engine.model.registry.FlowModelLocator;">`FlowModelLocator`</SwmToken> interface, providing the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/registry/FlowModelRegistryImpl.java" pos="50:5:5" line-data="	public FlowModel getFlowModel(String id) throws NoSuchFlowModelException {">`getFlowModel`</SwmToken> method to retrieve a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/registry/FlowModelRegistryImpl.java" pos="50:3:3" line-data="	public FlowModel getFlowModel(String id) throws NoSuchFlowModelException {">`FlowModel`</SwmToken> by its ID. This method may throw a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/registry/FlowModelRegistryImpl.java" pos="50:14:14" line-data="	public FlowModel getFlowModel(String id) throws NoSuchFlowModelException {">`NoSuchFlowModelException`</SwmToken> if the specified flow model does not exist.

```java
	public FlowModel getFlowModel(String id) throws NoSuchFlowModelException {
		try {
			return getLocalFlowModelHolder(id).getFlowModel();
		} catch (NoSuchFlowModelException e) {
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
