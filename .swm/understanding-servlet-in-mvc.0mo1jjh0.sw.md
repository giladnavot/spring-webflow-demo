---
title: Understanding Servlet in MVC
---
# What is a Servlet

Servlets in the MVC architecture are used to handle HTTP requests and responses. They act as a controller in the MVC pattern, processing user requests, invoking business logic, and returning the appropriate view.

# Servlet in Spring Web Flow

In this project, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="33:4:4" line-data="public class ServletMvcView extends AbstractMvcView {">`ServletMvcView`</SwmToken> class extends the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="26:12:12" line-data="import org.springframework.webflow.mvc.view.AbstractMvcView;">`AbstractMvcView`</SwmToken> and is responsible for rendering the view in a Spring Web Flow application. It takes an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="40:5:13" line-data="	public ServletMvcView(org.springframework.web.servlet.View view, RequestContext context) {">`org.springframework.web.servlet.View`</SwmToken> and a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="45:1:1" line-data="		RequestContext context = getRequestContext();">`RequestContext`</SwmToken> as parameters to create a new Servlet MVC view.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" line="45">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="44:5:5" line-data="	protected void doRender(Map&lt;String, ?&gt; model) throws Exception {">`doRender`</SwmToken> method in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="33:4:4" line-data="public class ServletMvcView extends AbstractMvcView {">`ServletMvcView`</SwmToken> handles the rendering of the view by setting necessary attributes in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="47:1:1" line-data="		HttpServletRequest request = (HttpServletRequest) externalContext.getNativeRequest();">`HttpServletRequest`</SwmToken> and then calling the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="55:5:5" line-data="		getView().render(model, request, response);">`render`</SwmToken> method on the view with the model, request, and response.

```java
		RequestContext context = getRequestContext();
		ExternalContext externalContext = context.getExternalContext();
		HttpServletRequest request = (HttpServletRequest) externalContext.getNativeRequest();
		HttpServletResponse response = (HttpServletResponse) externalContext.getNativeResponse();
		request.setAttribute(org.springframework.web.servlet.support.RequestContext.WEB_APPLICATION_CONTEXT_ATTRIBUTE,
				context.getActiveFlow().getApplicationContext());
		// spring:eval tag
		if (getConversionService() != null) {
			request.setAttribute(ConversionService.class.getName(), getConversionService().getDelegateConversionService());
		}
		getView().render(model, request, response);
	}

}

```

---

</SwmSnippet>

# Creating <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="33:4:4" line-data="public class ServletMvcView extends AbstractMvcView {">`ServletMvcView`</SwmToken> Instances

The `ServletMvcViewFactory` class is responsible for creating instances of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="33:4:4" line-data="public class ServletMvcView extends AbstractMvcView {">`ServletMvcView`</SwmToken>. It extends `AbstractMvcViewFactory` and overrides the `createMvcView` method to return a new <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="33:4:4" line-data="public class ServletMvcView extends AbstractMvcView {">`ServletMvcView`</SwmToken> instance.

# How to Use Servlets

Servlets are used by extending classes like <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="33:4:4" line-data="public class ServletMvcView extends AbstractMvcView {">`ServletMvcView`</SwmToken> and implementing methods to handle rendering and request processing. For example, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="44:5:5" line-data="	protected void doRender(Map&lt;String, ?&gt; model) throws Exception {">`doRender`</SwmToken> method in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="33:4:4" line-data="public class ServletMvcView extends AbstractMvcView {">`ServletMvcView`</SwmToken> handles the rendering of the view by setting necessary attributes in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="47:1:1" line-data="		HttpServletRequest request = (HttpServletRequest) externalContext.getNativeRequest();">`HttpServletRequest`</SwmToken> and then calling the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="55:5:5" line-data="		getView().render(model, request, response);">`render`</SwmToken> method on the view with the model, request, and response.

# Where Servlets are Used

Servlets are used in various classes such as <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="33:4:4" line-data="public class ServletMvcView extends AbstractMvcView {">`ServletMvcView`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="61:4:4" line-data="public class FlowHandlerAdapter extends WebContentGenerator implements HandlerAdapter, InitializingBean {">`FlowHandlerAdapter`</SwmToken>, and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="286:9:9" line-data="		ServletExternalContext context = new MvcExternalContext(getServletContext(), request, response, flowUrlHandler);">`MvcExternalContext`</SwmToken>. These classes extend or utilize servlet functionality to manage HTTP requests and responses within the Spring Web Flow framework.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="53">

---

One example of servlet usage is in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="61:4:4" line-data="public class FlowHandlerAdapter extends WebContentGenerator implements HandlerAdapter, InitializingBean {">`FlowHandlerAdapter`</SwmToken> class, which encapsulates the generic workflow associated with executing flows in a Servlet environment. It delegates to mapped <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="55:16:16" line-data=" * environment. Delegates to mapped {@link FlowHandler flow handlers} to manage the interaction with executions of">`FlowHandler`</SwmToken> flow handlers to manage the interaction with executions of specific flow definitions.

```java
/**
 * A custom MVC HandlerAdapter that encapsulates the generic workflow associated with executing flows in a Servlet
 * environment. Delegates to mapped {@link FlowHandler flow handlers} to manage the interaction with executions of
 * specific flow definitions.
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" line="172">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="172:5:5" line-data="	public ModelAndView handleRequest(HttpServletRequest request, HttpServletResponse response) throws Exception {">`handleRequest`</SwmToken> method in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="43:4:4" line-data="public class FlowController implements Controller, ApplicationContextAware, InitializingBean {">`FlowController`</SwmToken> class is responsible for handling HTTP requests. It retrieves the appropriate <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="173:1:1" line-data="		FlowHandler handler = getFlowHandler(request);">`FlowHandler`</SwmToken> for the request and delegates the handling to the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="174:3:3" line-data="		return flowHandlerAdapter.handle(request, response, handler);">`flowHandlerAdapter`</SwmToken>.

```java
	public ModelAndView handleRequest(HttpServletRequest request, HttpServletResponse response) throws Exception {
		FlowHandler handler = getFlowHandler(request);
		return flowHandlerAdapter.handle(request, response, handler);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" line="178">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="179:5:5" line-data="	private FlowHandler getFlowHandler(HttpServletRequest request) {">`getFlowHandler`</SwmToken> method in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="43:4:4" line-data="public class FlowController implements Controller, ApplicationContextAware, InitializingBean {">`FlowController`</SwmToken> class retrieves the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="179:3:3" line-data="	private FlowHandler getFlowHandler(HttpServletRequest request) {">`FlowHandler`</SwmToken> for a given flow ID. If no specific handler is found, it defaults to a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="188:7:7" line-data="			handler = new DefaultFlowHandler(flowId);">`DefaultFlowHandler`</SwmToken>.

```java

	private FlowHandler getFlowHandler(HttpServletRequest request) {
		FlowUrlHandler urlHandler = flowHandlerAdapter.getFlowUrlHandler();
		String flowId = urlHandler.getFlowId(request);
		return getFlowHandler(flowId);
	}

	private FlowHandler getFlowHandler(String flowId) {
		FlowHandler handler = flowHandlers.get(flowId);
		if (handler == null) {
			handler = new DefaultFlowHandler(flowId);
		}
		return handler;
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
