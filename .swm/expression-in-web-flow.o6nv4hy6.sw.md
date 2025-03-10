---
title: Expression in Web Flow
---
# Expression Overview

An Expression is an interface that encapsulates the details of a previously parsed expression string. It provides a common abstraction for expression evaluation independent of any language like Spring EL or the Unified EL.

## Purpose of Expression

The Expression interface defines methods for evaluating the expression against context objects, setting the expression in the provided context, getting the most general type that can be passed to the setValue method for the given context, and returning the original string used to create this expression.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/expression/el/WebFlowELExpressionParser.java" line="32">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/expression/el/WebFlowELExpressionParser.java" pos="37:4:4" line-data="public class WebFlowELExpressionParser extends ELExpressionParser {">`WebFlowELExpressionParser`</SwmToken> class allows for Unified EL expressions in a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/expression/el/WebFlowELExpressionParser.java" pos="33:17:17" line-data=" * Allows for Unified EL expressions in a FlowDefinition.">`FlowDefinition`</SwmToken>.

```java
/**
 * Allows for Unified EL expressions in a FlowDefinition.
 * 
 * @author Jeremy Grelle
 */
public class WebFlowELExpressionParser extends ELExpressionParser {

	/**
	 * Creates a new Web Flow EL expression parser.
	 * @param expressionFactory the underlying EL expression factory (EL provider specific)
	 */
	public WebFlowELExpressionParser(ExpressionFactory expressionFactory) {
		super(expressionFactory);
		putContextFactory(RequestContext.class, new RequestContextELContextFactory());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/expression/spel/WebFlowSpringELExpressionParser.java" line="32">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/expression/spel/WebFlowSpringELExpressionParser.java" pos="32:3:3" line-data="	public WebFlowSpringELExpressionParser(SpelExpressionParser expressionParser) {">`WebFlowSpringELExpressionParser`</SwmToken> class also utilizes expressions by adding default property accessors.

```java
	public WebFlowSpringELExpressionParser(SpelExpressionParser expressionParser) {
		super(expressionParser);
		addDefaultPropertyAccessors();
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
