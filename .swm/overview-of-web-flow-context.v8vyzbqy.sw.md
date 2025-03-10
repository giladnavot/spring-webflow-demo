---
title: Overview of Web Flow Context
---
# Overview of Web Flow Context

Context in Web Flow refers to the environment and state information that is passed around during the execution of a web flow. It encapsulates details about the current HTTP request, response, and the servlet context.

## <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="263:1:1" line-data="				ServletExternalContext context = createServletExternalContext(request, response);">`ServletExternalContext`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="263:1:1" line-data="				ServletExternalContext context = createServletExternalContext(request, response);">`ServletExternalContext`</SwmToken> class provides contextual information about an HTTP Servlet environment that has interacted with Spring Web Flow. It includes references to the servlet context, HTTP request, and HTTP response.

## Accessors and Maps

This class also provides accessors for various maps such as the HTTP request parameter map, request attribute map, session map, and application map. These maps allow the flow to interact with the underlying servlet environment.

## Managing Response State

Additionally, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="263:1:1" line-data="				ServletExternalContext context = createServletExternalContext(request, response);">`ServletExternalContext`</SwmToken> manages flags indicating the state of the response, such as whether the response is complete, if a flow execution redirect has been requested, or if the request originated from an Ajax request.

## Flow URL Handling

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="42:12:12" line-data="import org.springframework.webflow.context.servlet.FlowUrlHandler;">`FlowUrlHandler`</SwmToken> is another component that works with the context to generate flow execution <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="189:14:14" line-data="	 * {@link HttpServletResponse#encodeRedirectURL} for URLs that have a host">`URLs`</SwmToken>, ensuring that the correct <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="189:14:14" line-data="	 * {@link HttpServletResponse#encodeRedirectURL} for URLs that have a host">`URLs`</SwmToken> are used for flow navigation and redirection.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="262">

---

In <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="61:4:4" line-data="public class FlowHandlerAdapter extends WebContentGenerator implements HandlerAdapter, InitializingBean {">`FlowHandlerAdapter`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="263:1:1" line-data="				ServletExternalContext context = createServletExternalContext(request, response);">`ServletExternalContext`</SwmToken> is used to create a new external context wrapping the given servlet HTTP request and response.

```java
				MutableAttributeMap<Object> input = getInputMap(flowHandler, request);
				ServletExternalContext context = createServletExternalContext(request, response);
				FlowExecutionResult result = flowExecutor.launchExecution(flowId, input, context);
				handleFlowExecutionResult(result, context, request, response, flowHandler);
			} catch (FlowException e) {
				handleFlowException(e, request, response, flowHandler);
			}
		}
		return null;
	}

	public long getLastModified(HttpServletRequest request, Object handler) {
		return -1;
	}

	// subclassing hooks

	/**
	 * Creates the servlet external context for the current HTTP servlet request.
	 * @param request the current request
	 * @param response the current response
	 */
	protected ServletExternalContext createServletExternalContext(HttpServletRequest request,
			HttpServletResponse response) {
		ServletExternalContext context = new MvcExternalContext(getServletContext(), request, response, flowUrlHandler);
		context.setAjaxRequest(ajaxHandler.isAjaxRequest(request, response));
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
