---
title: Exploring Web Flow Configuration
---
# Exploring Web Flow Configuration

Web Flow configuration refers to the settings and classes that manage the setup and behavior of web flows within the Spring Web Flow framework.

## Configuration Components

The configuration includes various classes and methods that handle the registration and parsing of bean definitions related to web flows.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/WebFlowConfigNamespaceHandler.java" line="31">

---

For instance, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/WebFlowConfigNamespaceHandler.java" pos="27:4:4" line-data="public class WebFlowConfigNamespaceHandler extends NamespaceHandlerSupport {">`WebFlowConfigNamespaceHandler`</SwmToken> class is responsible for registering bean definition parsers for different components like flow executors, flow execution listeners, flow registries, and flow builder services.

```java
		registerBeanDefinitionParser("flow-registry", new FlowRegistryBeanDefinitionParser());
		registerBeanDefinitionParser("flow-builder-services", new FlowBuilderServicesBeanDefinitionParser());
	}
```

---

</SwmSnippet>

## Initialization and Management

These configurations ensure that the web flow components are correctly initialized and managed within the Spring application context.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" line="119">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" pos="124:5:5" line-data="	public FlowDefinitionRegistryBuilder addFlowLocation(String path) {">`addFlowLocation`</SwmToken> method registers a flow defined at a specified location as an XML file. This method can accept a path to a single resource or an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" pos="120:25:27" line-data="	 * This may be a path to a single resource or a ANT-style path expression that">`ANT-style`</SwmToken> path expression that matches multiple resources.

```java
	 * Register a flow defined at the following location as an .xml file.
	 * This may be a path to a single resource or a ANT-style path expression that
	 * matches multiple resources.
	 * @param path the resource path to the externalized flow definition resource.
	 */
	public FlowDefinitionRegistryBuilder addFlowLocation(String path) {
		this.addFlowLocation(path, null, null);
		return this;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" line="97">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/config/FlowDefinitionRegistryBuilder.java" pos="111:5:5" line-data="	public FlowDefinitionRegistryBuilder setBasePath(String basePath) {">`setBasePath`</SwmToken> method configures the base path where flow definitions are found. When specified, all flow locations are relative to this path. This helps in assigning flow IDs based on the path segment between their base path and file name.

```java
	/**
	 * Configure the base path where flow definitions are found. When specified, all
	 * flow locations are relative to this path. Also when specified, by default flows
	 * are assigned an id equal to the the path segment between their base path and
	 * file name.
	 * <p>
	 * For example, if a flow definition is located at
	 * '/WEB-INF/hotels/booking/booking-flow.xml' and the base path is '/WEB-INF', the
	 * remaining path to this flow is 'hotels/booking' which then becomes the flow id.
	 * <p>
	 * If a flow definition is found directly on the base path, the file name minus
	 * its extension is used as the flow id.
	 * @param basePath the base path to use
	 */
	public FlowDefinitionRegistryBuilder setBasePath(String basePath) {
		if (basePath != null) {
			this.flowResourceFactory.setBasePath(basePath);
		}
		return this;
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
