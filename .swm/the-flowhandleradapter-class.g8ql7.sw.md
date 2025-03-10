---
title: The FlowHandlerAdapter class
---
This document will cover the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="103:3:3" line-data="	public FlowHandlerAdapter() {">`FlowHandlerAdapter`</SwmToken> class. We will explain:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="103:3:3" line-data="	public FlowHandlerAdapter() {">`FlowHandlerAdapter`</SwmToken> is.
2. The variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="103:3:3" line-data="	public FlowHandlerAdapter() {">`FlowHandlerAdapter`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="103:3:3" line-data="	public FlowHandlerAdapter() {">`FlowHandlerAdapter`</SwmToken>

<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="103:3:3" line-data="	public FlowHandlerAdapter() {">`FlowHandlerAdapter`</SwmToken> is a custom MVC <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="35:10:10" line-data="import org.springframework.web.servlet.HandlerAdapter;">`HandlerAdapter`</SwmToken> that encapsulates the generic workflow associated with executing flows in a Servlet environment. It delegates to mapped <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="242:7:7" line-data="		return handler instanceof FlowHandler;">`FlowHandler`</SwmToken> flow handlers to manage the interaction with executions of specific flow definitions.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="96">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="103:3:3" line-data="	public FlowHandlerAdapter() {">`FlowHandlerAdapter`</SwmToken> is the constructor for the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="103:3:3" line-data="	public FlowHandlerAdapter() {">`FlowHandlerAdapter`</SwmToken> class. It prevents caching of flow pages by default.

```java
	/**
	 * Creates a new flow handler adapter.
	 * @see #setFlowExecutor(FlowExecutor)
	 * @see #setFlowUrlHandler(FlowUrlHandler)
	 * @see #setAjaxHandler(AjaxHandler)
	 * @see #afterPropertiesSet()
	 */
	public FlowHandlerAdapter() {
		// prevent caching of flow pages by default
		setCacheSeconds(0);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="109">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="111:5:5" line-data="	public FlowExecutor getFlowExecutor() {">`getFlowExecutor`</SwmToken> returns the central service for executing flows. It is a required function.

```java
	 * Returns the central service for executing flows. Required.
	 */
	public FlowExecutor getFlowExecutor() {
		return flowExecutor;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="115">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="119:5:5" line-data="	public void setFlowExecutor(FlowExecutor flowExecutor) {">`setFlowExecutor`</SwmToken> sets the central service for executing flows. It is a required function.

```java
	/**
	 * Sets the central service for executing flows. Required.
	 * @param flowExecutor
	 */
	public void setFlowExecutor(FlowExecutor flowExecutor) {
		this.flowExecutor = flowExecutor;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="123">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="126:5:5" line-data="	public FlowUrlHandler getFlowUrlHandler() {">`getFlowUrlHandler`</SwmToken> returns the flow URL handler.

```java
	/**
	 * Returns the flow url handler.
	 */
	public FlowUrlHandler getFlowUrlHandler() {
		return flowUrlHandler;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="130">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="134:5:5" line-data="	public void setFlowUrlHandler(FlowUrlHandler flowUrlHandler) {">`setFlowUrlHandler`</SwmToken> sets the flow URL handler.

```java
	/**
	 * Sets the flow url handler
	 * @param flowUrlHandler the flow url handler
	 */
	public void setFlowUrlHandler(FlowUrlHandler flowUrlHandler) {
		this.flowUrlHandler = flowUrlHandler;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="138">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="141:5:5" line-data="	public AjaxHandler getAjaxHandler() {">`getAjaxHandler`</SwmToken> returns the configured Ajax handler.

```java
	/**
	 * Returns the configured Ajax handler.
	 */
	public AjaxHandler getAjaxHandler() {
		return ajaxHandler;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="145">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="149:5:5" line-data="	public void setAjaxHandler(AjaxHandler ajaxHandler) {">`setAjaxHandler`</SwmToken> sets the configured Ajax handler.

```java
	/**
	 * Sets the configured Ajax handler.
	 * @param ajaxHandler the ajax handler
	 */
	public void setAjaxHandler(AjaxHandler ajaxHandler) {
		this.ajaxHandler = ajaxHandler;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="153">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="157:5:5" line-data="	public boolean getRedirectHttp10Compatible() {">`getRedirectHttp10Compatible`</SwmToken> checks whether redirects sent by this handler adapter should be compatible with HTTP <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="154:27:29" line-data="	 * Whether redirect sent by this handler adapter should be compatible with HTTP 1.0 clients.">`1.0`</SwmToken> clients.

```java
	/**
	 * Whether redirect sent by this handler adapter should be compatible with HTTP 1.0 clients.
	 * @return true if so, false otherwise
	 */
	public boolean getRedirectHttp10Compatible() {
		return redirectHttp10Compatible;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="161">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="172:5:5" line-data="	public void setRedirectHttp10Compatible(boolean redirectHttp10Compatible) {">`setRedirectHttp10Compatible`</SwmToken> sets whether redirects sent by this handler adapter should be compatible with HTTP <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="162:29:31" line-data="	 * Set whether redirects sent by this handler adapter should be compatible with HTTP 1.0 clients.">`1.0`</SwmToken> clients.

```java
	/**
	 * Set whether redirects sent by this handler adapter should be compatible with HTTP 1.0 clients.
	 * <p>
	 * By default, this will enforce a redirect HTTP status code of 302 by delegating to
	 * <code>HttpServletResponse.sendRedirect</code>. Setting this to false will send HTTP status code 303, which is the
	 * correct code for HTTP 1.1 clients, but not understood by HTTP 1.0 clients.
	 * <p>
	 * Many HTTP 1.1 clients treat 302 just like 303, not making any difference. However, some clients depend on 303
	 * when redirecting after a POST request; turn this flag off in such a scenario.
	 * @see jakarta.servlet.http.HttpServletResponse#sendRedirect
	 */
	public void setRedirectHttp10Compatible(boolean redirectHttp10Compatible) {
		this.redirectHttp10Compatible = redirectHttp10Compatible;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="176">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="181:5:5" line-data="	public void setStatusCode(HttpStatus statusCode) {">`setStatusCode`</SwmToken> sets the status code for this view.

```java
	/**
	 * Set the status code for this view.
	 * <p>Default is to send 302/303, depending on the value of the
	 * {@link #setRedirectHttp10Compatible(boolean) http10Compatible} flag.
	 */
	public void setStatusCode(HttpStatus statusCode) {
		this.statusCode = statusCode;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="185">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="195:5:5" line-data="	public void setHosts(String[] hosts) {">`setHosts`</SwmToken> configures one or more hosts associated with the application.

```java
	/**
	 * Configure one or more hosts associated with the application. All other
	 * hosts will be considered external hosts. In effect this property
	 * provides a way turn off encoding via
	 * {@link HttpServletResponse#encodeRedirectURL} for URLs that have a host
	 * and that host is not listed as a known host.
	 * <p>If not set (the default) all URLs are encoded through the response.
	 * @param hosts one or more application hosts
	 * @since 2.4.3
	 */
	public void setHosts(String[] hosts) {
		this.hosts = hosts;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="199">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="202:7:7" line-data="	public String[] getHosts() {">`getHosts`</SwmToken> returns the configured hosts associated with the application.

```java
	/**
	 * Return the configured hosts associated with the application.
	 */
	public String[] getHosts() {
		return this.hosts;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="206">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="216:5:5" line-data="	public void setSaveOutputToFlashScopeOnRedirect(boolean saveOutputToFlashScopeOnRedirect) {">`setSaveOutputToFlashScopeOnRedirect`</SwmToken> sets whether servlet relative redirects sent by this handler adapter should pass flow output to the Spring MVC flash scope.

```java
	/**
	 * Set whether servlet relative redirects sent by this handler adapter
	 * should pass {@link FlowExecutionOutcome#getOutput() flow output} to the
	 * Spring MVC {@link FlashMap flash scope}.
	 *
	 * <p>By default, to remain compatible with previous releases, flow output is
	 * not mapped to flash scope.
	 *
	 * @param saveOutputToFlashScopeOnRedirect
	 */
	public void setSaveOutputToFlashScopeOnRedirect(boolean saveOutputToFlashScopeOnRedirect) {
		this.saveOutputToFlashScopeOnRedirect = saveOutputToFlashScopeOnRedirect;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="220">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="227:5:5" line-data="	public boolean getSaveOutputToFlashScopeOnRedirect() {">`getSaveOutputToFlashScopeOnRedirect`</SwmToken> checks whether servlet relative redirects should pass flow output to the Spring MVC flash scope.

```java
	/**
	 * Whether servlet relative redirects should pass
	 * {@link FlowExecutionOutcome#getOutput() flow output} to the Spring MVC
	 * {@link FlashMap flash scope}.
	 *
	 * @return {@code true} if so, {@code false} otherwise
	 */
	public boolean getSaveOutputToFlashScopeOnRedirect() {
		return this.saveOutputToFlashScopeOnRedirect;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="231">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="231:5:5" line-data="	public void afterPropertiesSet() throws Exception {">`afterPropertiesSet`</SwmToken> ensures that the required properties are set after the properties are set.

```java
	public void afterPropertiesSet() throws Exception {
		Assert.notNull(flowExecutor, "The FlowExecutor to execute flows is required");
		if (flowUrlHandler == null) {
			flowUrlHandler = new DefaultFlowUrlHandler();
		}
		if (ajaxHandler == null) {
			ajaxHandler = new DefaultAjaxHandler();
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="241">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="241:5:5" line-data="	public boolean supports(Object handler) {">`supports`</SwmToken> checks if the handler is an instance of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="242:7:7" line-data="		return handler instanceof FlowHandler;">`FlowHandler`</SwmToken>.

```java
	public boolean supports(Object handler) {
		return handler instanceof FlowHandler;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="245">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="245:5:5" line-data="	public ModelAndView handle(HttpServletRequest request, HttpServletResponse response, Object handler)">`handle`</SwmToken> handles the HTTP request and response for a given handler.

```java
	public ModelAndView handle(HttpServletRequest request, HttpServletResponse response, Object handler)
			throws Exception {
		FlowHandler flowHandler = (FlowHandler) handler;
		checkRequest(request);
		prepareResponse(response);
		String flowExecutionKey = flowUrlHandler.getFlowExecutionKey(request);
		if (flowExecutionKey != null) {
			try {
				ServletExternalContext context = createServletExternalContext(request, response);
				FlowExecutionResult result = flowExecutor.resumeExecution(flowExecutionKey, context);
				handleFlowExecutionResult(result, context, request, response, flowHandler);
			} catch (FlowException e) {
				handleFlowException(e, request, response, flowHandler);
			}
		} else {
			try {
				String flowId = getFlowId(flowHandler, request);
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
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="273">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="273:5:5" line-data="	public long getLastModified(HttpServletRequest request, Object handler) {">`getLastModified`</SwmToken> returns the last modified time for the given request and handler.

```java
	public long getLastModified(HttpServletRequest request, Object handler) {
		return -1;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="280">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="284:5:5" line-data="	protected ServletExternalContext createServletExternalContext(HttpServletRequest request,">`createServletExternalContext`</SwmToken> creates the servlet external context for the current HTTP servlet request.

```java
	 * Creates the servlet external context for the current HTTP servlet request.
	 * @param request the current request
	 * @param response the current response
	 */
	protected ServletExternalContext createServletExternalContext(HttpServletRequest request,
			HttpServletResponse response) {
		ServletExternalContext context = new MvcExternalContext(getServletContext(), request, response, flowUrlHandler);
		context.setAjaxRequest(ajaxHandler.isAjaxRequest(request, response));
		return context;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="292">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="297:5:5" line-data="	protected String defaultGetFlowId(HttpServletRequest request) {">`defaultGetFlowId`</SwmToken> determines the ID of the flow to launch from the current request.

```java
	 * The default algorithm to determine the id of the flow to launch from the current request. Only called if
	 * {@link FlowHandler#getFlowId()} returns null. This implementation delegates to the configured
	 * {@link FlowUrlHandler#getFlowId(HttpServletRequest)}. Subclasses may override.
	 * @param request the current request
	 */
	protected String defaultGetFlowId(HttpServletRequest request) {
		return flowUrlHandler.getFlowId(request);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="302">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="307:8:8" line-data="	protected MutableAttributeMap&lt;Object&gt; defaultCreateFlowExecutionInputMap(HttpServletRequest request) {">`defaultCreateFlowExecutionInputMap`</SwmToken> creates the flow execution input map from the current request parameters.

```java
	 * The default algorithm to create the flow execution input map. Only called if
	 * {@link FlowHandler#createExecutionInputMap(HttpServletRequest)} returns null. This implementation exposes all
	 * current request parameters as flow execution input attributes. Subclasses may override.
	 * @param request the current request
	 */
	protected MutableAttributeMap<Object> defaultCreateFlowExecutionInputMap(HttpServletRequest request) {
		Map<String, String[]> parameterMap = request.getParameterMap();
		if (parameterMap.size() == 0) {
			return null;
		}
		LocalAttributeMap<Object> inputMap = new LocalAttributeMap<>(parameterMap.size(), 1);
		for (Map.Entry<String, String[]> entry : parameterMap.entrySet()) {
			String[] values = entry.getValue();
			inputMap.put(entry.getKey(), values.length == 1 ? values[0] : values);
		}
		return inputMap;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="321">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="331:5:5" line-data="	protected void defaultHandleExecutionOutcome(String flowId, FlowExecutionOutcome outcome,">`defaultHandleExecutionOutcome`</SwmToken> handles the flow execution outcome by attempting to start a new execution of the ended flow.

```java
	 * The default algorithm for handling a flow execution outcome. Only called if
	 * {@link FlowHandler#handleExecutionOutcome(FlowExecutionOutcome, HttpServletRequest, HttpServletResponse)} returns
	 * null. This implementation attempts to start a new execution of the ended flow. Any flow execution output is
	 * passed as input to the new execution. Subclasses may override.
	 * @param flowId the id of the ended flow
	 * @param outcome the flow execution outcome
	 * @param context ServletExternalContext the completed ServletExternalContext
	 * @param request the current request
	 * @param response the current response
	 */
	protected void defaultHandleExecutionOutcome(String flowId, FlowExecutionOutcome outcome,
			ServletExternalContext context, HttpServletRequest request, HttpServletResponse response)
			throws IOException {
		if (!context.isResponseComplete()) {
			// by default, just start the flow over passing the output as input
			if (logger.isDebugEnabled()) {
				logger.debug("Ended flow '" + flowId + "' did not commit a response; "
						+ "attempting to start a new flow execution as a default outcome handler");
			}
			String flowUrl = flowUrlHandler.createFlowDefinitionUrl(flowId, outcome.getOutput(), request);
			sendRedirect(flowUrl, request, response);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="346">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="356:5:5" line-data="	protected void defaultHandleException(String flowId, FlowException e, HttpServletRequest request,">`defaultHandleException`</SwmToken> handles a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="346:19:19" line-data="	 * The default algorithm for handling a {@link FlowException} now handled by the Web Flow system. Only called if">`FlowException`</SwmToken> by attempting to start a new execution of the ended or expired flow.

```java
	 * The default algorithm for handling a {@link FlowException} now handled by the Web Flow system. Only called if
	 * {@link FlowHandler#handleException(FlowException, HttpServletRequest, HttpServletResponse)} returns null. This
	 * implementation rethrows the exception unless it is a {@link NoSuchFlowExecutionException}. If the exception is a
	 * NoSuchFlowExecutionException, this implementation attempts to start a new execution of the ended or expired flow.
	 * Subclasses may override.
	 * @param flowId the id of the ended flow
	 * @param e the flow exception
	 * @param request the current request
	 * @param response the current response
	 */
	protected void defaultHandleException(String flowId, FlowException e, HttpServletRequest request,
			HttpServletResponse response) throws IOException {
		if (e instanceof NoSuchFlowExecutionException && flowId != null) {
			if (!response.isCommitted()) {
				if (logger.isDebugEnabled()) {
					logger.debug("Restarting a new execution of previously ended flow '" + flowId + "'");
				}
				// by default, attempt to restart the flow
				String flowUrl = flowUrlHandler.createFlowDefinitionUrl(flowId, null, request);
				sendRedirect(flowUrl, request, response);
			}
		} else {
			throw e;
		}
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-faces/src/main/java/org/springframework/faces/webflow/JsfFlowHandlerAdapter.java" line="24">

---

The <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/JsfFlowHandlerAdapter.java" pos="24:12:12" line-data="import org.springframework.webflow.mvc.servlet.FlowHandlerAdapter;">`FlowHandlerAdapter`</SwmToken> is extended by the <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/JsfFlowHandlerAdapter.java" pos="33:4:4" line-data="public class JsfFlowHandlerAdapter extends FlowHandlerAdapter {">`JsfFlowHandlerAdapter`</SwmToken> class. This extension replaces the default <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/JsfFlowHandlerAdapter.java" pos="27:28:28" line-data=" * An extension of {@link FlowHandlerAdapter} that replaces the default {@link AjaxHandler} instance with a">`AjaxHandler`</SwmToken> instance with a <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/JsfFlowHandlerAdapter.java" pos="28:7:7" line-data=" * {@link JsfAjaxHandler}.">`JsfAjaxHandler`</SwmToken>, providing specialized handling for JSF-based web flows.

```java
import org.springframework.webflow.mvc.servlet.FlowHandlerAdapter;

/**
 * An extension of {@link FlowHandlerAdapter} that replaces the default {@link AjaxHandler} instance with a
 * {@link JsfAjaxHandler}.
 *
 * @author Rossen Stoyanchev
 * @since 2.2.0
 */
public class JsfFlowHandlerAdapter extends FlowHandlerAdapter {


	public void afterPropertiesSet() throws Exception {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" line="59">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="59:3:3" line-data="	public FlowController() {">`FlowController`</SwmToken> class, an instance of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="60:7:7" line-data="		flowHandlerAdapter = new FlowHandlerAdapter();">`FlowHandlerAdapter`</SwmToken> is created and initialized with a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="61:7:7" line-data="		flowHandlerAdapter.setFlowUrlHandler(new FilenameFlowUrlHandler());">`FilenameFlowUrlHandler`</SwmToken>. This setup is crucial for managing the flow URL handling within the controller.

```java
	public FlowController() {
		flowHandlerAdapter = new FlowHandlerAdapter();
		flowHandlerAdapter.setFlowUrlHandler(new FilenameFlowUrlHandler());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" line="144">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="59:3:3" line-data="	public FlowController() {">`FlowController`</SwmToken> class includes accessor methods for the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="144:3:3" line-data="	public FlowHandlerAdapter getFlowHandlerAdapter() {">`FlowHandlerAdapter`</SwmToken>. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="144:5:5" line-data="	public FlowHandlerAdapter getFlowHandlerAdapter() {">`getFlowHandlerAdapter`</SwmToken> method returns the current instance of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="144:3:3" line-data="	public FlowHandlerAdapter getFlowHandlerAdapter() {">`FlowHandlerAdapter`</SwmToken>, while the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="153:5:5" line-data="	public void setFlowHandlerAdapter(FlowHandlerAdapter flowHandlerAdapter) {">`setFlowHandlerAdapter`</SwmToken> method allows for setting a custom <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowController.java" pos="144:3:3" line-data="	public FlowHandlerAdapter getFlowHandlerAdapter() {">`FlowHandlerAdapter`</SwmToken>, enabling complete customization of the flow controller workflow.

```java
	public FlowHandlerAdapter getFlowHandlerAdapter() {
		return flowHandlerAdapter;
	}

	/**
	 * Sets the flow handler adapter which this Controller uses internally to carry out handler workflow. Call this
	 * instead of the convenience accesors to completely customize flow controller workflow.
	 * @param flowHandlerAdapter the flow handler adapter
	 */
	public void setFlowHandlerAdapter(FlowHandlerAdapter flowHandlerAdapter) {
		this.flowHandlerAdapter = flowHandlerAdapter;
		customFlowHandlerAdapterSet = true;
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
