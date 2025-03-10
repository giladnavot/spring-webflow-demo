---
title: The LocalAttributeMap class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="50:3:3" line-data="	public LocalAttributeMap() {">`LocalAttributeMap`</SwmToken> in the Spring Web Flow project. We will cover:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="50:3:3" line-data="	public LocalAttributeMap() {">`LocalAttributeMap`</SwmToken> is.
2. Variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="50:3:3" line-data="	public LocalAttributeMap() {">`LocalAttributeMap`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="50:3:3" line-data="	public LocalAttributeMap() {">`LocalAttributeMap`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="50:3:3" line-data="	public LocalAttributeMap() {">`LocalAttributeMap`</SwmToken> class in <SwmPath>[spring-webflow/…/collection/LocalAttributeMap.java](spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java)</SwmPath> is a generic, mutable attribute map with string keys. It is used to store and manage attributes in a map-like structure, providing various utility methods to access and manipulate these attributes.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="38">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="38:13:13" line-data="	 * The backing map storing the attributes.">`attributes`</SwmToken> is used to store the attributes in the map.

```java
	 * The backing map storing the attributes.
	 */
	private Map<String, V> attributes;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="43">

---

The variable <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="45:13:13" line-data="	private transient MapAccessor&lt;String, V&gt; attributeAccessor;">`attributeAccessor`</SwmToken> is a helper for accessing attributes. It is marked transient and restored on deserialization.

```java
	 * A helper for accessing attributes. Marked transient and restored on deserialization.
	 */
	private transient MapAccessor<String, V> attributeAccessor;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="47">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="50:3:3" line-data="	public LocalAttributeMap() {">`LocalAttributeMap`</SwmToken> creates a new attribute map, initially empty.

```java
	/**
	 * Creates a new attribute map, initially empty.
	 */
	public LocalAttributeMap() {
		initAttributes(createTargetMap());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="54">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="59:3:3" line-data="	public LocalAttributeMap(int size, int loadFactor) {">`LocalAttributeMap`</SwmToken> creates a new attribute map, initially empty with specified size and load factor.

```java
	/**
	 * Creates a new attribute map, initially empty.
	 * @param size the initial size
	 * @param loadFactor the load factor
	 */
	public LocalAttributeMap(int size, int loadFactor) {
		initAttributes(createTargetMap(size, loadFactor));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="63">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="66:3:3" line-data="	public LocalAttributeMap(String attributeName, V attributeValue) {">`LocalAttributeMap`</SwmToken> creates a new attribute map with a single entry.

```java
	/**
	 * Creates a new attribute map with a single entry.
	 */
	public LocalAttributeMap(String attributeName, V attributeValue) {
		initAttributes(createTargetMap(1, 1));
		put(attributeName, attributeValue);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="71">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="74:3:3" line-data="	public LocalAttributeMap(Map&lt;String, V&gt; map) {">`LocalAttributeMap`</SwmToken> creates a new attribute map wrapping the specified map.

```java
	/**
	 * Creates a new attribute map wrapping the specified map.
	 */
	public LocalAttributeMap(Map<String, V> map) {
		Assert.notNull(map, "The target map is required");
		initAttributes(map);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="81">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="81:11:11" line-data="	public Map&lt;String, V&gt; asMap() {">`asMap`</SwmToken> returns the attributes as a map.

```java
	public Map<String, V> asMap() {
		return attributeAccessor.asMap();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="85">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="85:5:5" line-data="	public int size() {">`size`</SwmToken> returns the number of attributes in the map.

```java
	public int size() {
		return attributes.size();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="89">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="89:5:5" line-data="	public V get(String attributeName) {">`get`</SwmToken> returns the value of the specified attribute.

```java
	public V get(String attributeName) {
		return attributes.get(attributeName);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="93">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="93:5:5" line-data="	public boolean isEmpty() {">`isEmpty`</SwmToken> checks if the map is empty.

```java
	public boolean isEmpty() {
		return attributes.isEmpty();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="97">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="97:5:5" line-data="	public boolean contains(String attributeName) {">`contains`</SwmToken> checks if the map contains the specified attribute.

```java
	public boolean contains(String attributeName) {
		return attributes.containsKey(attributeName);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="101">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="101:5:5" line-data="	public boolean contains(String attributeName, Class&lt;? extends V&gt; requiredType) throws IllegalArgumentException {">`contains`</SwmToken> checks if the map contains the specified attribute with the required type.

```java
	public boolean contains(String attributeName, Class<? extends V> requiredType) throws IllegalArgumentException {
		return attributeAccessor.containsKey(attributeName, requiredType);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="105">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="105:5:5" line-data="	public V get(String attributeName, V defaultValue) {">`get`</SwmToken> returns the value of the specified attribute or a default value if the attribute is not found.

```java
	public V get(String attributeName, V defaultValue) {
		return attributeAccessor.get(attributeName, defaultValue);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="109">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="109:13:13" line-data="	public &lt;T extends V&gt; T get(String attributeName, Class&lt;T&gt; requiredType) throws IllegalArgumentException {">`get`</SwmToken> returns the value of the specified attribute with the required type.

```java
	public <T extends V> T get(String attributeName, Class<T> requiredType) throws IllegalArgumentException {
		return attributeAccessor.get(attributeName, requiredType);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="113">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="113:13:13" line-data="	public &lt;T extends V&gt; T get(String attributeName, Class&lt;T&gt; requiredType, T defaultValue)">`get`</SwmToken> returns the value of the specified attribute with the required type or a default value if the attribute is not found.

```java
	public <T extends V> T get(String attributeName, Class<T> requiredType, T defaultValue)
			throws IllegalStateException {
		return attributeAccessor.get(attributeName, requiredType, defaultValue);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="118">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="118:5:5" line-data="	public V getRequired(String attributeName) throws IllegalArgumentException {">`getRequired`</SwmToken> returns the value of the specified attribute or throws an exception if the attribute is not found.

```java
	public V getRequired(String attributeName) throws IllegalArgumentException {
		return attributeAccessor.getRequired(attributeName);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="122">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="122:13:13" line-data="	public &lt;T extends V&gt; T getRequired(String attributeName, Class&lt;T&gt; requiredType) throws IllegalArgumentException {">`getRequired`</SwmToken> returns the value of the specified attribute with the required type or throws an exception if the attribute is not found.

```java
	public <T extends V> T getRequired(String attributeName, Class<T> requiredType) throws IllegalArgumentException {
		return attributeAccessor.getRequired(attributeName, requiredType);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="126">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="126:5:5" line-data="	public String getString(String attributeName) throws IllegalArgumentException {">`getString`</SwmToken> returns the value of the specified attribute as a string.

```java
	public String getString(String attributeName) throws IllegalArgumentException {
		return attributeAccessor.getString(attributeName);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="130">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="130:5:5" line-data="	public String getString(String attributeName, String defaultValue) throws IllegalArgumentException {">`getString`</SwmToken> returns the value of the specified attribute as a string or a default value if the attribute is not found.

```java
	public String getString(String attributeName, String defaultValue) throws IllegalArgumentException {
		return attributeAccessor.getString(attributeName, defaultValue);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="134">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="134:5:5" line-data="	public String getRequiredString(String attributeName) throws IllegalArgumentException {">`getRequiredString`</SwmToken> returns the value of the specified attribute as a string or throws an exception if the attribute is not found.

```java
	public String getRequiredString(String attributeName) throws IllegalArgumentException {
		return attributeAccessor.getRequiredString(attributeName);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="138">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="138:8:8" line-data="	public Collection&lt;V&gt; getCollection(String attributeName) throws IllegalArgumentException {">`getCollection`</SwmToken> returns the value of the specified attribute as a collection.

```java
	public Collection<V> getCollection(String attributeName) throws IllegalArgumentException {
		return attributeAccessor.getCollection(attributeName);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="142">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="142:15:15" line-data="	public &lt;T extends Collection&lt;V&gt;&gt; T getCollection(String attributeName, Class&lt;T&gt; requiredType)">`getCollection`</SwmToken> returns the value of the specified attribute as a collection with the required type.

```java
	public <T extends Collection<V>> T getCollection(String attributeName, Class<T> requiredType)
			throws IllegalArgumentException {
		return attributeAccessor.getCollection(attributeName, requiredType);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" line="147">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalAttributeMap.java" pos="147:8:8" line-data="	public Collection&lt;V&gt; getRequiredCollection(String attributeName) throws IllegalArgumentException {">`getRequiredCollection`</SwmToken> returns the value of the specified attribute as a collection or throws an exception if the attribute is not found.

```java
	public Collection<V> getRequiredCollection(String attributeName) throws IllegalArgumentException {
		return attributeAccessor.getRequiredCollection(attributeName);
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" line="213">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="57:2:2" line-data="class FlowRegistryFactoryBean implements FactoryBean&lt;FlowDefinitionRegistry&gt;, BeanClassLoaderAware, InitializingBean,">`FlowRegistryFactoryBean`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowRegistryFactoryBean.java" pos="216:7:7" line-data="			flowAttributes = new LocalAttributeMap&lt;&gt;(1 + attributes.size(), 1);">`LocalAttributeMap`</SwmToken> is used to create and populate a map of flow attributes. This is particularly useful when the flow is in development mode, as it allows for the addition of specific attributes like 'development'.

```java
	private AttributeMap<Object> getFlowAttributes(Set<FlowElementAttribute> attributes) {
		MutableAttributeMap<Object> flowAttributes = null;
		if (flowBuilderServices.getDevelopment()) {
			flowAttributes = new LocalAttributeMap<>(1 + attributes.size(), 1);
			flowAttributes.put("development", true);
		}
		if (!attributes.isEmpty()) {
			if (flowAttributes == null) {
				flowAttributes = new LocalAttributeMap<>(attributes.size(), 1);
			}
			for (FlowElementAttribute attribute : attributes) {
				flowAttributes.put(attribute.getName(), getConvertedValue(attribute));
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/EndState.java" line="103">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/EndState.java" pos="46:4:4" line-data="public class EndState extends State {">`EndState`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/EndState.java" pos="106:1:1" line-data="			LocalAttributeMap&lt;Object&gt; sessionOutput = createSessionOutput(context);">`LocalAttributeMap`</SwmToken> is utilized to create a session output map. This map is then used to end the active flow session, either for the current flow or a parent flow that will resume.

```java
			context.endActiveFlowSession(getId(), createSessionOutput(context));
		} else {
			// there is a parent flow that will resume (this flow is a subflow)
			LocalAttributeMap<Object> sessionOutput = createSessionOutput(context);
			context.endActiveFlowSession(getId(), sessionOutput);
		}
	}

	/**
	 * Returns the subflow output map. This will invoke the output mapper (if any) to map data available in the flow
	 * execution request context into a newly created empty map.
	 */
	protected LocalAttributeMap<Object> createSessionOutput(RequestContext context) {
		LocalAttributeMap<Object> output = new LocalAttributeMap<>();
		if (outputMapper != null) {
			MappingResults results = outputMapper.map(context, output);
			if (results != null && results.hasErrorResults()) {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorFactoryBean.java" line="163">

---

Within the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorFactoryBean.java" pos="56:2:2" line-data="class FlowExecutorFactoryBean implements FactoryBean&lt;FlowExecutor&gt;, BeanClassLoaderAware, InitializingBean {">`FlowExecutorFactoryBean`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorFactoryBean.java" pos="164:1:1" line-data="		LocalAttributeMap&lt;Object&gt; executionAttributes = new LocalAttributeMap&lt;&gt;();">`LocalAttributeMap`</SwmToken> is employed to create and manage flow execution attributes. This includes adding default attributes if they are not already present.

```java
	private MutableAttributeMap<Object> createFlowExecutionAttributes() {
		LocalAttributeMap<Object> executionAttributes = new LocalAttributeMap<>();
		if (flowExecutionAttributes != null) {
			for (FlowElementAttribute attribute : flowExecutionAttributes) {
				executionAttributes.put(attribute.getName(), getConvertedValue(attribute));
			}
		}
		putDefaultFlowExecutionAttributes(executionAttributes);
		return executionAttributes;
	}

	private void putDefaultFlowExecutionAttributes(LocalAttributeMap<Object> executionAttributes) {
		if (!executionAttributes.contains(ALWAYS_REDIRECT_ON_PAUSE)) {
			executionAttributes.put(ALWAYS_REDIRECT_ON_PAUSE, true);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" line="934">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" pos="275:9:9" line-data="		FlowBuilder flowBuilder = new FlowModelFlowBuilder(flowModelHolder);">`FlowModelFlowBuilder`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/FlowModelFlowBuilder.java" pos="936:1:1" line-data="			LocalAttributeMap&lt;Object&gt; attributes = new LocalAttributeMap&lt;&gt;();">`LocalAttributeMap`</SwmToken> is used to parse and store meta attributes from a list of attribute models. This ensures that all relevant attributes are captured and available for use.

```java
	private MutableAttributeMap<Object> parseMetaAttributes(List<AttributeModel> attributeModels) {
		if (attributeModels != null && !attributeModels.isEmpty()) {
			LocalAttributeMap<Object> attributes = new LocalAttributeMap<>();
			for (AttributeModel attributeModel : attributeModels) {
				parseAndPutMetaAttribute(attributeModel, attributes);
			}
			return attributes;
		} else {
			return new LocalAttributeMap<>();
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorBuilder.java" line="50">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorBuilder.java" pos="61:3:3" line-data="	public FlowExecutorBuilder(FlowDefinitionLocator flowRegistry) {">`FlowExecutorBuilder`</SwmToken> class uses <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorBuilder.java" pos="52:3:3" line-data="	private LocalAttributeMap&lt;Object&gt; executionAttributes = new LocalAttributeMap&lt;&gt;();">`LocalAttributeMap`</SwmToken> to manage execution attributes. This includes initializing the map with existing attributes and adding new ones as needed.

```java
	private Integer maxFlowExecutionSnapshots;

	private LocalAttributeMap<Object> executionAttributes = new LocalAttributeMap<>();

	private ConditionalFlowExecutionListenerLoader listenerLoader;

	private FlowExecutionListenerCriteriaFactory listenerCriteriaFactory = new FlowExecutionListenerCriteriaFactory();

	private ConversationManager conversationManager;


	public FlowExecutorBuilder(FlowDefinitionLocator flowRegistry) {
		Assert.notNull(flowRegistry, "FlowDefinitionLocator is required");
		this.flowRegistry = flowRegistry;
	}

	/**
	 * Create a new instance with the given flow registry and ApplicationContext.
	 *
	 * @param flowRegistry the flow registry that will locate flow definitions
	 * @param applicationContext the Spring ApplicationContext
	 * @deprecated as of 2.5 an ApplicationContext is no longer required
	 */
	public FlowExecutorBuilder(FlowDefinitionLocator flowRegistry, ApplicationContext applicationContext) {
		Assert.notNull(flowRegistry, "FlowDefinitionLocator is required");
		this.flowRegistry = flowRegistry;
	}


	/**
	 * Set the maximum number of allowed flow executions per user.
	 * @param maxFlowExecutions the max flow executions
	 */
	public FlowExecutorBuilder setMaxFlowExecutions(int maxFlowExecutions) {
		this.maxFlowExecutions = maxFlowExecutions;
		return this;
	}

	/**
	 * Set the maximum number of history snapshots allowed per flow execution.
	 * @param maxFlowExecutionSnapshots the max flow execution snapshots
	 */
	public FlowExecutorBuilder setMaxFlowExecutionSnapshots(int maxFlowExecutionSnapshots) {
		this.maxFlowExecutionSnapshots = maxFlowExecutionSnapshots;
		return this;
	}

	/**
	 * Whether flow executions should redirect after they pause before rendering.
	 * @param redirectOnPause whether to redirect or not
	 */
	public FlowExecutorBuilder setAlwaysRedirectOnPause(boolean redirectOnPause) {
		this.executionAttributes.put("alwaysRedirectOnPause", redirectOnPause);
		return this;
	}

	/**
	 * Whether flow executions redirect after they pause for transitions that remain
	 * in the same view state. This attribute effectively overrides the value of the
	 * "always-redirect-on-pause" attribute in same state transitions.
	 * @param redirectInSameState whether to redirect or not
	 */
	public FlowExecutorBuilder setRedirectInSameState(boolean redirectInSameState) {
		this.executionAttributes.put("redirectInSameState", redirectInSameState);
		return this;
	}

	/**
	 * Add a single flow execution meta attribute.
	 * @param name the attribute name
	 * @param value the attribute value
	 */
	public FlowExecutorBuilder addFlowExecutionAttribute(String name, Object value) {
		this.executionAttributes.put(name, value);
		return this;
	}

	/**
	 * Register a {@link FlowExecutionListener} that observes the lifecycle of all flow
	 * executions launched by this executor.
	 * @param listener the listener to be registered
	 */
	public FlowExecutorBuilder addFlowExecutionListener(FlowExecutionListener listener) {
		return addFlowExecutionListener(listener, "*");
	}

	/**
	 * Register a {@link FlowExecutionListener} that observes the lifecycle of flow
	 * executions launched by this executor.
	 * @param listener the listener to be registered
	 * @param criteria the criteria that determines the flow definitions a listener
	 * 	should observe, delimited by commas or '*' for "all".
	 * 	Example: 'flow1,flow2,flow3'.
	 */
	public FlowExecutorBuilder addFlowExecutionListener(FlowExecutionListener listener, String criteria) {
		if (this.listenerLoader == null) {
			this.listenerLoader = new ConditionalFlowExecutionListenerLoader();
		}
		this.listenerLoader.addListener(listener, this.listenerCriteriaFactory.getListenerCriteria(criteria));
		return this;
	}

	/**
	 * Set the ConversationManager implementation to use for storing conversations
	 * in the session effectively controlling how state is stored physically when
	 * a flow execution is paused.. Note that when this attribute is provided, the
	 * "max-execution-snapshots" attribute is meaningless.
	 * @param conversationManager the ConversationManager instance to use
	 */
	public FlowExecutorBuilder setConversationManager(ConversationManager conversationManager) {
		this.conversationManager = conversationManager;
		return this;
	}

	/**
	 * Create and return a {@link FlowExecutor} instance.
	 */
	public FlowExecutor build() {
		FlowExecutionImplFactory executionFactory = getExecutionFactory();
		DefaultFlowExecutionRepository executionRepository = getFlowExecutionRepository(executionFactory);
		executionFactory.setExecutionKeyFactory(executionRepository);
		return new FlowExecutorImpl(this.flowRegistry, executionFactory, executionRepository);
	}


	private FlowExecutionImplFactory getExecutionFactory() {
		FlowExecutionImplFactory executionFactory = new FlowExecutionImplFactory();
		executionFactory.setExecutionAttributes(getExecutionAttributes());
		if (this.listenerLoader != null) {
			executionFactory.setExecutionListenerLoader(this.listenerLoader);
		}
		return executionFactory;
	}

	private DefaultFlowExecutionRepository getFlowExecutionRepository(FlowExecutionFactory executionFactory) {
		ConversationManager manager = getConversationManager();
		FlowExecutionSnapshotFactory snapshotFactory = getSnapshotFactory(executionFactory);
		DefaultFlowExecutionRepository repository = new DefaultFlowExecutionRepository(manager, snapshotFactory);
		if (this.maxFlowExecutionSnapshots != null) {
			repository.setMaxSnapshots((this.maxFlowExecutionSnapshots == 0) ? 1 : this.maxFlowExecutionSnapshots);
		}
		return repository;
	}

	private ConversationManager getConversationManager() {
		ConversationManager manager = this.conversationManager;
		if (manager == null) {
			manager = new SessionBindingConversationManager();
		}
		if (this.maxFlowExecutions != null && manager instanceof SessionBindingConversationManager) {
			((SessionBindingConversationManager) manager).setMaxConversations(this.maxFlowExecutions);
		}
		return manager;
	}

	private FlowExecutionSnapshotFactory getSnapshotFactory(FlowExecutionFactory executionFactory) {
		FlowExecutionSnapshotFactory factory = null;
		if (this.maxFlowExecutionSnapshots != null && this.maxFlowExecutionSnapshots == 0) {
			factory = new SimpleFlowExecutionSnapshotFactory(executionFactory, this.flowRegistry);
		}
		else {
			factory = new SerializedFlowExecutionSnapshotFactory(executionFactory, this.flowRegistry);
		}
		return factory;
	}

	private LocalAttributeMap<Object> getExecutionAttributes() {
		LocalAttributeMap<Object> attributes = new LocalAttributeMap<>(this.executionAttributes.asMap());
		if (!attributes.contains("alwaysRedirectOnPause")) {
			attributes.put("alwaysRedirectOnPause", true);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" line="247">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" pos="51:4:4" line-data="public class FlowDefinitionRegistryBuilder {">`FlowDefinitionRegistryBuilder`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" pos="249:12:12" line-data="			AttributeMap&lt;Object&gt; attributes = new LocalAttributeMap&lt;&gt;();">`LocalAttributeMap`</SwmToken> is used to register flow location patterns and update flow attributes. This helps in organizing and managing the flow definitions effectively.

```java
	private void registerFlowLocationPatterns(DefaultFlowRegistry flowRegistry) {
		for (String pattern : this.flowLocationPatterns) {
			AttributeMap<Object> attributes = new LocalAttributeMap<>();
			updateFlowAttributes(attributes);
			FlowDefinitionResource[] resources;
			try {
				resources = this.flowResourceFactory.createResources(pattern, attributes);
			} catch (IOException e) {
				IllegalStateException ise = new IllegalStateException(
						"An I/O Exception occurred resolving the flow location pattern '" + pattern + "'");
				ise.initCause(e);
				throw ise;
			}
			for (FlowDefinitionResource resource : resources) {
				registerFlow(resource, flowRegistry);
			}
		}
	}

	private void registerFlow(FlowDefinitionResource resource, DefaultFlowRegistry flowRegistry) {
		FlowModelBuilder flowModelBuilder;
		if (resource.getPath().getFilename().endsWith(".xml")) {
			flowModelBuilder = new XmlFlowModelBuilder(resource.getPath(), flowRegistry.getFlowModelRegistry());
		} else {
			throw new IllegalArgumentException(resource
					+ " is not a supported resource type; supported types are [.xml]");
		}
		FlowModelHolder flowModelHolder = new DefaultFlowModelHolder(flowModelBuilder);
		FlowBuilder flowBuilder = new FlowModelFlowBuilder(flowModelHolder);
		FlowBuilderContext builderContext = new FlowBuilderContextImpl(
				resource.getId(), resource.getAttributes(), flowRegistry, this.flowBuilderServices);
		FlowAssembler assembler = new FlowAssembler(flowBuilder, builderContext);
		DefaultFlowHolder flowHolder = new DefaultFlowHolder(assembler);

		flowRegistry.getFlowModelRegistry().registerFlowModel(resource.getId(), flowModelHolder);
		flowRegistry.registerFlowDefinition(flowHolder);
	}

	private void registerFlowBuilders(DefaultFlowRegistry flowRegistry) {
		for (FlowBuilderInfo info : this.flowBuilderInfos) {
			AttributeMap<Object> attributes = info.getAttributes();
			updateFlowAttributes(attributes);
			FlowBuilderContext builderContext = new FlowBuilderContextImpl(
					info.getId(), attributes, flowRegistry, this.flowBuilderServices);
			FlowAssembler assembler = new FlowAssembler(info.getBuilder(), builderContext);
			flowRegistry.registerFlowDefinition(assembler.assembleFlow());
		}
	}

	private void updateFlowAttributes(AttributeMap<Object> attributes) {
		if (this.flowBuilderServices.getDevelopment()) {
			attributes.asMap().put("development", true);
		}
	}


	private static class FlowLocation {

		private final String path;

		private final String id;

		private final AttributeMap<Object> attributes;


		public FlowLocation(String path, String id, Map<String, Object> attributes) {
			this.path = path;
			this.id = id;
			this.attributes = (attributes != null) ?
					new LocalAttributeMap<>(attributes) :
					new LocalAttributeMap<>(new HashMap<>());
		}

		public String getPath() {
			return this.path;
		}

		public String getId() {
			return this.id;
		}

		public AttributeMap<Object> getAttributes() {
			return this.attributes;
		}
	}

	private static class FlowBuilderInfo {

		private final FlowBuilder builder;

		private final String id;

		private final AttributeMap<Object> attributes;

		public FlowBuilderInfo(FlowBuilder builder, String id, Map<String, Object> attributes) {
			this.builder = builder;
			this.id = id;
			this.attributes = (attributes != null) ?
					new LocalAttributeMap<>(attributes) :
					new LocalAttributeMap<>(new HashMap<>());
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" line="107">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowExecutorBuilder.java" pos="168:1:1" line-data="		FlowExecutionImplFactory executionFactory = getExecutionFactory();">`FlowExecutionImplFactory`</SwmToken> class uses <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowExecutionImplFactory.java" pos="110:7:7" line-data="			conversationScope = new LocalAttributeMap&lt;&gt;();">`LocalAttributeMap`</SwmToken> to set the conversation scope and execution attributes for a flow execution. This ensures that all necessary attributes are available during the flow execution.

```java
		}
		execution.setKey(flowExecutionKey);
		if (conversationScope == null) {
			conversationScope = new LocalAttributeMap<>();
		}
		execution.setConversationScope(conversationScope);
		execution.setAttributes(executionAttributes);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowSessionImpl.java" line="61">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowSessionImpl.java" pos="69:3:3" line-data="	private FlowSessionImpl parent;">`FlowSessionImpl`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowSessionImpl.java" pos="64:14:14" line-data="	private MutableAttributeMap&lt;Object&gt; scope = new LocalAttributeMap&lt;&gt;();">`LocalAttributeMap`</SwmToken> is used to initialize the session data model and view scope. This helps in managing the session attributes and ensuring they are properly scoped.

```java
	/**
	 * The session data model ("flow scope").
	 */
	private MutableAttributeMap<Object> scope = new LocalAttributeMap<>();

	/**
	 * The parent session of this session (may be <code>null</code> if this is a root session.)
	 */
	private FlowSessionImpl parent;

	/**
	 * Set so the transient {@link #flow} field can be restored by the {@link FlowExecutionImplFactory}.
	 */
	private String flowId;

	/**
	 * Set so the transient {@link #state} field can be restored by the {@link FlowExecutionImplFactory}.
	 */
	private String stateId;

	/**
	 * Default constructor required for externalizable serialization. Should NOT be called programmatically.
	 */
	public FlowSessionImpl() {
	}

	/**
	 * Create a new flow session.
	 * @param flow the flow definition associated with this flow session
	 * @param parent this session's parent (may be null)
	 */
	public FlowSessionImpl(Flow flow, FlowSessionImpl parent) {
		Assert.notNull(flow, "The flow is required");
		this.flow = flow;
		this.parent = parent;
	}

	// implementing FlowSession

	public FlowDefinition getDefinition() {
		return flow;
	}

	public StateDefinition getState() {
		return state;
	}

	public MutableAttributeMap<Object> getScope() {
		return scope;
	}

	@SuppressWarnings("unchecked")
	public MutableAttributeMap<Object> getViewScope() throws IllegalStateException {
		if (state == null) {
			throw new IllegalStateException("The current state of this flow '" + flow.getId()
					+ "' is [null] - cannot access view scope");
		}
		if (!state.isViewState()) {
			throw new IllegalStateException("The current state '" + state.getId() + "' of this flow '" + flow.getId()
					+ "' is not a view state - view scope not accessible");
		}
		return (MutableAttributeMap<Object>) scope.get(VIEW_SCOPE_ATTRIBUTE);
	}

	public boolean isEmbeddedMode() {
		return (Boolean) scope.get(EMBEDDED_MODE_ATTRIBUTE, false);
	}

	public FlowSession getParent() {
		return parent;
	}

	public boolean isRoot() {
		return parent == null;
	}

	// public impl

	public void setCurrentState(State state) {
		if (this.state != null && this.state.isViewState()) {
			destroyViewScope();
		}
		this.state = state;
		if (this.state.isViewState()) {
			initViewScope();
		}
	}

	// custom serialization

	@SuppressWarnings("unchecked")
	public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
		flowId = (String) in.readObject();
		stateId = (String) in.readObject();
		scope = (MutableAttributeMap<Object>) in.readObject();
		parent = (FlowSessionImpl) in.readObject();
	}

	public void writeExternal(ObjectOutput out) throws IOException {
		out.writeObject(flow.getId());
		out.writeObject(state != null ? state.getId() : null);
		out.writeObject(scope);
		out.writeObject(parent);
	}

	// package-private

	Flow getFlow() {
		return flow;
	}

	// package private setters used by FlowExecutionImplFactory for setting/updating internal state

	/**
	 * Restores the definition of this flow session.
	 * @param flow the flow sessions definition
	 * @see FlowExecutionImplStateRestorer
	 */
	void setFlow(Flow flow) {
		Assert.notNull(flow, "The flow is required");
		this.flow = flow;
	}

	/**
	 * Set the current state of this flow session.
	 * @param state the state that is currently active in this flow session
	 * @see FlowExecutionImpl#setCurrentState(State)
	 * @see FlowExecutionImplStateRestorer
	 */
	void setState(State state) {
		Assert.notNull(state, "The state is required");
		Assert.isTrue(flow == state.getOwner(),
				"The state does not belong to the flow associated with this flow session");
		this.state = state;
	}

	/**
	 * Returns the de-serialized id indicating the flow id of this session.
	 */
	String getFlowId() {
		if (flow == null) {
			return flowId;
		} else {
			return flow.getId();
		}
	}

	/**
	 * Sets the de-serialized id indicating the flow id of this session. Used for testing only.
	 * @param flowId the flow id
	 */
	void setFlowId(String flowId) {
		this.flowId = flowId;
	}

	/**
	 * Returns the de-serialized id indicating the current state of this session.
	 */
	String getStateId() {
		if (state == null) {
			return stateId;
		} else {
			return state.getId();
		}
	}

	/**
	 * Sets the de-serialized id indicating the state of this session. Used for testing only.
	 * @param stateId the state id
	 */
	void setStateId(String stateId) {
		this.stateId = stateId;
	}

	/**
	 * Set a flow session attribute to indicate the current session should execute in embedded mode.
	 * @see FlowSession#isEmbeddedMode()
	 */
	void setEmbeddedMode() {
		this.scope.put(EMBEDDED_MODE_ATTRIBUTE, true);
	}

	// internal helpers

	/**
	 * Initialize the view scope data structure.
	 */
	private void initViewScope() {
		scope.put(VIEW_SCOPE_ATTRIBUTE, new LocalAttributeMap<>());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" line="64">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/FlowSessionImpl.java" pos="35:22:22" line-data=" * closely coupled with &lt;code&gt;FlowExecutionImpl&lt;/code&gt; and &lt;code&gt;RequestControlContextImpl&lt;/code&gt;. The three classes">`RequestControlContextImpl`</SwmToken> class uses <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="67:3:3" line-data="	private LocalAttributeMap&lt;Object&gt; requestScope = new LocalAttributeMap&lt;&gt;();">`LocalAttributeMap`</SwmToken> to manage request scope data and contextual properties. This ensures that all relevant data is available during the request processing.

```java
	/**
	 * The request scope data map. Never null, initially empty.
	 */
	private LocalAttributeMap<Object> requestScope = new LocalAttributeMap<>();

	/**
	 * Holder for contextual properties describing the currently executing request; never null, initially empty.
	 */
	private LocalAttributeMap<Object> attributes = new LocalAttributeMap<>();

	/**
	 * The current event being processed by this flow; initially null.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
