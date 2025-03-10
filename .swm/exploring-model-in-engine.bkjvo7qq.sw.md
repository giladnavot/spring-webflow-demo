---
title: Exploring Model in Engine
---
# Model Interface

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" pos="32:5:5" line-data="	boolean isMergeableWith(Model model);">`Model`</SwmToken> interface defines the structure and behavior of models within the engine. It ensures that all models can handle merging their content with another eligible model.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" line="25">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" pos="32:3:3" line-data="	boolean isMergeableWith(Model model);">`isMergeableWith`</SwmToken> method determines if a given model can be merged into the current model. This is essential for ensuring compatibility between models before attempting a merge.

```java
	/**
	 * Determine if the model is able to be merged into the current model
	 * 
	 * @param model the model to compare
	 * 
	 * @return true if able to merge
	 */
	boolean isMergeableWith(Model model);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" line="34">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" pos="37:14:14" line-data="	 * @param model the model to merge with">`merge`</SwmToken> method is responsible for merging the content of the provided model into the current model. This allows for the combination of model data in a controlled manner.

```java
	/**
	 * Merge the model into the current model
	 * 
	 * @param model the model to merge with
	 */
	void merge(Model model);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" line="41">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" pos="46:3:3" line-data="	Model createCopy();">`createCopy`</SwmToken> method creates a deep copy of the model. This is particularly useful when merging models and collections, as it ensures that the original model remains unchanged.

```java
	/**
	 * Create a deep copy of this model. Needed when merging models and collections.
	 * 
	 * @return a deep copy of this model
	 */
	Model createCopy();
```

---

</SwmSnippet>

## Implementations

Various classes such as `TransitionModel`, `ExceptionHandlerModel`, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/FlowModelBuilder.java" pos="62:1:1" line-data="	FlowModel getFlowModel() throws FlowModelBuilderException;">`FlowModel`</SwmToken>, and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/ViewStateModel.java" pos="63:1:1" line-data="		ViewStateModel state = (ViewStateModel) model;">`ViewStateModel`</SwmToken> implement the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" pos="32:5:5" line-data="	boolean isMergeableWith(Model model);">`Model`</SwmToken> interface, each providing specific implementations of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" pos="32:3:3" line-data="	boolean isMergeableWith(Model model);">`isMergeableWith`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" pos="30:14:14" line-data="	 * @return true if able to merge">`merge`</SwmToken>, and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/Model.java" pos="46:3:3" line-data="	Model createCopy();">`createCopy`</SwmToken> methods.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" line="23">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/AbstractModel.java" pos="28:6:6" line-data="public abstract class AbstractModel implements Model {">`AbstractModel`</SwmToken> class provides basic merge functions that can be utilized by other models. It includes methods for merging objects, strings, model elements, and lists.

```java
/**
 * Contains basic merge functions that can be utilized by other models.
 *
 * @author Scott Andrews
 */
public abstract class AbstractModel implements Model {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/ViewStateModel.java" line="62">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/ViewStateModel.java" pos="62:5:5" line-data="	public void merge(Model model) {">`merge`</SwmToken> method in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/ViewStateModel.java" pos="63:1:1" line-data="		ViewStateModel state = (ViewStateModel) model;">`ViewStateModel`</SwmToken> merges the content of another <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/ViewStateModel.java" pos="63:1:1" line-data="		ViewStateModel state = (ViewStateModel) model;">`ViewStateModel`</SwmToken> into the current one.

```java
	public void merge(Model model) {
		ViewStateModel state = (ViewStateModel) model;
		setParent(null);
		setAttributes(merge(getAttributes(), state.getAttributes()));
		setSecured((SecuredModel) merge(getSecured(), state.getSecured()));
		setOnEntryActions(merge(getOnEntryActions(), state.getOnEntryActions(), false));
		setExceptionHandlers(merge(getExceptionHandlers(), state.getExceptionHandlers()));
		setTransitions(merge(getTransitions(), state.getTransitions()));
		setOnExitActions(merge(getOnExitActions(), state.getOnExitActions(), false));
		setView(merge(getView(), state.getView()));
		setRedirect(merge(getRedirect(), state.getRedirect()));
		setPopup(merge(getPopup(), state.getPopup()));
		setModel(merge(getModel(), state.getModel()));
		setValidationHints(mergeValidationHints(getValidationHints(), state.getValidationHints()));
		setVars(merge(getVars(), state.getVars(), false));
		setBinder((BinderModel) merge(getBinder(), state.getBinder()));
		setOnRenderActions(merge(getOnRenderActions(), state.getOnRenderActions(), false));
	}
```

---

</SwmSnippet>

# Model Endpoints

Model endpoints are methods that provide access to the fully constructed flow model and its underlying resources.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/FlowModelBuilder.java" line="57">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/FlowModelBuilder.java" pos="62:3:3" line-data="	FlowModel getFlowModel() throws FlowModelBuilderException;">`getFlowModel`</SwmToken> method is an endpoint that returns the fully constructed flow model. This method is called by the builder's assembler after the assembly process is complete. It ensures that the flow model is ready for use.

```java
	 * Get the fully constructed flow model. Called by the builder's assembler (director) after assembly. When this
	 * method is called by the assembler, it is expected flow construction has completed and the returned flow model is
	 * ready for use.
	 * @throws FlowModelBuilderException an exception occurred building this flow
	 */
	FlowModel getFlowModel() throws FlowModelBuilderException;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/FlowModelBuilder.java" line="72">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/model/builder/FlowModelBuilder.java" pos="76:3:3" line-data="	Resource getFlowModelResource();">`getFlowModelResource`</SwmToken> method is an endpoint that retrieves the underlying flow model resource used to build the flow model. This method returns null if the builder does not construct the flow model from a resource.

```java
	 * Get the underlying flow model resource accessed to build this flow model. Returns null if this builder does not
	 * construct the flow model from a resource.
	 * @return the flow model resource
	 */
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
