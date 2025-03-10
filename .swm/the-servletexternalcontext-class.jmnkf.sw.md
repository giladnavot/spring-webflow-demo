---
title: The ServletExternalContext class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="129:3:3" line-data="	public ServletExternalContext(ServletContext context, HttpServletRequest request, HttpServletResponse response) {">`ServletExternalContext`</SwmToken> in the Spring Web Flow project. We will cover:

1. What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="129:3:3" line-data="	public ServletExternalContext(ServletContext context, HttpServletRequest request, HttpServletResponse response) {">`ServletExternalContext`</SwmToken>
2. Variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="129:3:3" line-data="	public ServletExternalContext(ServletContext context, HttpServletRequest request, HttpServletResponse response) {">`ServletExternalContext`</SwmToken>

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="129:3:3" line-data="	public ServletExternalContext(ServletContext context, HttpServletRequest request, HttpServletResponse response) {">`ServletExternalContext`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="129:3:3" line-data="	public ServletExternalContext(ServletContext context, HttpServletRequest request, HttpServletResponse response) {">`ServletExternalContext`</SwmToken> class provides contextual information about an HTTP Servlet environment that has interacted with Spring Web Flow. It is used to wrap the servlet context, HTTP request, and HTTP response, providing various methods to interact with these objects and manage the flow of web requests and responses.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="129">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="129:3:3" line-data="	public ServletExternalContext(ServletContext context, HttpServletRequest request, HttpServletResponse response) {">`ServletExternalContext`</SwmToken> constructor initializes the context, request, and response objects along with a default flow URL handler.

```java
	public ServletExternalContext(ServletContext context, HttpServletRequest request, HttpServletResponse response) {
		init(context, request, response, new DefaultFlowUrlHandler());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="140">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="140:3:3" line-data="	public ServletExternalContext(ServletContext context, HttpServletRequest request, HttpServletResponse response,">`ServletExternalContext`</SwmToken> constructor with a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="141:1:1" line-data="			FlowUrlHandler flowUrlHandler) {">`FlowUrlHandler`</SwmToken> parameter initializes the context, request, response, and the provided flow URL handler.

```java
	public ServletExternalContext(ServletContext context, HttpServletRequest request, HttpServletResponse response,
			FlowUrlHandler flowUrlHandler) {
		init(context, request, response, flowUrlHandler);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="150">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="150:5:5" line-data="	public void setAjaxRequest(boolean ajaxRequest) {">`setAjaxRequest`</SwmToken> function sets a flag indicating if the current request is an Ajax request.

```java
	public void setAjaxRequest(boolean ajaxRequest) {
		this.ajaxRequest = ajaxRequest;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="156">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="156:5:5" line-data="	public String getContextPath() {">`getContextPath`</SwmToken> function returns the context path of the request.

```java
	public String getContextPath() {
		return request.getContextPath();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="160">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="160:5:5" line-data="	public ParameterMap getRequestParameterMap() {">`getRequestParameterMap`</SwmToken> function returns an accessor for the HTTP request parameter map.

```java
	public ParameterMap getRequestParameterMap() {
		return requestParameterMap;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="164">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="164:8:8" line-data="	public MutableAttributeMap&lt;Object&gt; getRequestMap() {">`getRequestMap`</SwmToken> function returns an accessor for the HTTP request attribute map.

```java
	public MutableAttributeMap<Object> getRequestMap() {
		return requestMap;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="168">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="168:8:8" line-data="	public SharedAttributeMap&lt;Object&gt; getSessionMap() {">`getSessionMap`</SwmToken> function returns an accessor for the HTTP session map.

```java
	public SharedAttributeMap<Object> getSessionMap() {
		return sessionMap;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="172">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="172:8:8" line-data="	public SharedAttributeMap&lt;Object&gt; getGlobalSessionMap() {">`getGlobalSessionMap`</SwmToken> function returns an accessor for the global HTTP session map.

```java
	public SharedAttributeMap<Object> getGlobalSessionMap() {
		return getSessionMap();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="176">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="176:8:8" line-data="	public SharedAttributeMap&lt;Object&gt; getApplicationMap() {">`getApplicationMap`</SwmToken> function returns an accessor for the servlet context application map.

```java
	public SharedAttributeMap<Object> getApplicationMap() {
		return applicationMap;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="180">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="180:5:5" line-data="	public Principal getCurrentUser() {">`getCurrentUser`</SwmToken> function returns the current user principal.

```java
	public Principal getCurrentUser() {
		return request.getUserPrincipal();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="184">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="184:5:5" line-data="	public Locale getLocale() {">`getLocale`</SwmToken> function returns the locale of the request.

```java
	public Locale getLocale() {
		return request.getLocale();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="188">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="188:5:5" line-data="	public Object getNativeContext() {">`getNativeContext`</SwmToken> function returns the native servlet context.

```java
	public Object getNativeContext() {
		return context;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="192">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="192:5:5" line-data="	public Object getNativeRequest() {">`getNativeRequest`</SwmToken> function returns the native HTTP servlet request.

```java
	public Object getNativeRequest() {
		return request;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="196">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="196:5:5" line-data="	public Object getNativeResponse() {">`getNativeResponse`</SwmToken> function returns the native HTTP servlet response.

```java
	public Object getNativeResponse() {
		return response;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="200">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="200:5:5" line-data="	public boolean isAjaxRequest() {">`isAjaxRequest`</SwmToken> function returns a flag indicating if the current request is an Ajax request.

```java
	public boolean isAjaxRequest() {
		return ajaxRequest;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="204">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="204:5:5" line-data="	public String getFlowExecutionUrl(String flowId, String flowExecutionKey) {">`getFlowExecutionUrl`</SwmToken> function returns the URL for the flow execution.

```java
	public String getFlowExecutionUrl(String flowId, String flowExecutionKey) {
		return response.encodeURL(flowUrlHandler.createFlowExecutionUrl(flowId, flowExecutionKey, request));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="208">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="208:5:5" line-data="	public Writer getResponseWriter() throws IllegalStateException {">`getResponseWriter`</SwmToken> function returns a writer for the response.

```java
	public Writer getResponseWriter() throws IllegalStateException {
		assertResponseAllowed();
		try {
			return response.getWriter();
		} catch (IOException e) {
			IllegalStateException ise = new IllegalStateException("Unable to access the response Writer");
			ise.initCause(e);
			throw ise;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="219">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="219:5:5" line-data="	public boolean isResponseAllowed() {">`isResponseAllowed`</SwmToken> function returns a flag indicating if the response is allowed.

```java
	public boolean isResponseAllowed() {
		return !responseComplete;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="223">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="223:5:5" line-data="	public boolean isResponseComplete() {">`isResponseComplete`</SwmToken> function returns a flag indicating if the response is complete.

```java
	public boolean isResponseComplete() {
		return responseComplete;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="227">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="227:5:5" line-data="	public void recordResponseComplete() {">`recordResponseComplete`</SwmToken> function sets the response complete flag to true.

```java
	public void recordResponseComplete() {
		responseComplete = true;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="231">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="231:5:5" line-data="	public boolean isResponseCompleteFlowExecutionRedirect() {">`isResponseCompleteFlowExecutionRedirect`</SwmToken> function returns a flag indicating if a flow execution redirect has been requested.

```java
	public boolean isResponseCompleteFlowExecutionRedirect() {
		return flowExecutionRedirectRequested;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="235">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="235:5:5" line-data="	public void requestFlowExecutionRedirect() throws IllegalStateException {">`requestFlowExecutionRedirect`</SwmToken> function requests a flow execution redirect and marks the response as complete.

```java
	public void requestFlowExecutionRedirect() throws IllegalStateException {
		assertResponseAllowed();
		flowExecutionRedirectRequested = true;
		recordResponseComplete();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="241">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="241:5:5" line-data="	public void requestFlowDefinitionRedirect(String flowId, MutableAttributeMap&lt;?&gt; input) throws IllegalStateException {">`requestFlowDefinitionRedirect`</SwmToken> function requests a flow definition redirect and marks the response as complete.

```java
	public void requestFlowDefinitionRedirect(String flowId, MutableAttributeMap<?> input) throws IllegalStateException {
		assertResponseAllowed();
		flowDefinitionRedirectFlowId = flowId;
		flowDefinitionRedirectFlowInput = new LocalAttributeMap<>();
		if (input != null) {
			flowDefinitionRedirectFlowInput.putAll(input);
		}
		recordResponseComplete();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" line="251">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/context/servlet/ServletExternalContext.java" pos="251:5:5" line-data="	public void requestExternalRedirect(String location) throws IllegalStateException {">`requestExternalRedirect`</SwmToken> function requests an external redirect and marks the response as complete.

```java
	public void requestExternalRedirect(String location) throws IllegalStateException {
		assertResponseAllowed();
		externalRedirectUrl = location;
		recordResponseComplete();
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="250">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="61:4:4" line-data="public class FlowHandlerAdapter extends WebContentGenerator implements HandlerAdapter, InitializingBean {">`FlowHandlerAdapter`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="253:1:1" line-data="				ServletExternalContext context = createServletExternalContext(request, response);">`ServletExternalContext`</SwmToken> is used to resume a flow execution. The method <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="253:7:7" line-data="				ServletExternalContext context = createServletExternalContext(request, response);">`createServletExternalContext`</SwmToken> is called with the current request and response to create an instance of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="253:1:1" line-data="				ServletExternalContext context = createServletExternalContext(request, response);">`ServletExternalContext`</SwmToken>. This context is then passed to the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="254:7:9" line-data="				FlowExecutionResult result = flowExecutor.resumeExecution(flowExecutionKey, context);">`flowExecutor.resumeExecution`</SwmToken> method along with the flow execution key to resume the flow execution.

```java
		String flowExecutionKey = flowUrlHandler.getFlowExecutionKey(request);
		if (flowExecutionKey != null) {
			try {
				ServletExternalContext context = createServletExternalContext(request, response);
				FlowExecutionResult result = flowExecutor.resumeExecution(flowExecutionKey, context);
				handleFlowExecutionResult(result, context, request, response, flowHandler);
			} catch (FlowException e) {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="260">

---

In another part of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="61:4:4" line-data="public class FlowHandlerAdapter extends WebContentGenerator implements HandlerAdapter, InitializingBean {">`FlowHandlerAdapter`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="263:1:1" line-data="				ServletExternalContext context = createServletExternalContext(request, response);">`ServletExternalContext`</SwmToken> is used to launch a new flow execution. The method <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="263:7:7" line-data="				ServletExternalContext context = createServletExternalContext(request, response);">`createServletExternalContext`</SwmToken> is again called with the current request and response to create an instance of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="263:1:1" line-data="				ServletExternalContext context = createServletExternalContext(request, response);">`ServletExternalContext`</SwmToken>. This context is then passed to the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="264:7:9" line-data="				FlowExecutionResult result = flowExecutor.launchExecution(flowId, input, context);">`flowExecutor.launchExecution`</SwmToken> method along with the flow ID and input map to start a new flow execution.

```java
			try {
				String flowId = getFlowId(flowHandler, request);
				MutableAttributeMap<Object> input = getInputMap(flowHandler, request);
				ServletExternalContext context = createServletExternalContext(request, response);
				FlowExecutionResult result = flowExecutor.launchExecution(flowId, input, context);
				handleFlowExecutionResult(result, context, request, response, flowHandler);
			} catch (FlowException e) {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" line="284">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="284:5:5" line-data="	protected ServletExternalContext createServletExternalContext(HttpServletRequest request,">`createServletExternalContext`</SwmToken> method in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="61:4:4" line-data="public class FlowHandlerAdapter extends WebContentGenerator implements HandlerAdapter, InitializingBean {">`FlowHandlerAdapter`</SwmToken> class is responsible for creating an instance of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/FlowHandlerAdapter.java" pos="284:3:3" line-data="	protected ServletExternalContext createServletExternalContext(HttpServletRequest request,">`ServletExternalContext`</SwmToken>. It wraps the given servlet HTTP request and response, and sets additional properties such as whether the request is an AJAX request.

```java
	protected ServletExternalContext createServletExternalContext(HttpServletRequest request,
			HttpServletResponse response) {
		ServletExternalContext context = new MvcExternalContext(getServletContext(), request, response, flowUrlHandler);
		context.setAjaxRequest(ajaxHandler.isAjaxRequest(request, response));
		return context;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/MvcExternalContext.java" line="9">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/MvcExternalContext.java" pos="19:4:4" line-data="public class MvcExternalContext extends ServletExternalContext {">`MvcExternalContext`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/MvcExternalContext.java" pos="11:12:12" line-data="import org.springframework.webflow.context.servlet.ServletExternalContext;">`ServletExternalContext`</SwmToken> to provide specific functionality available in a Spring MVC environment. It overrides certain operations to integrate with Spring MVC features.

```java
import org.springframework.web.servlet.support.RequestContextUtils;
import org.springframework.webflow.context.servlet.FlowUrlHandler;
import org.springframework.webflow.context.servlet.ServletExternalContext;

/**
 * Spring MVC external context implementation. Is a {@link ServletExternalContext}, but overrides operations to plug in
 * specific functionality available in a Spring MVC Environment.
 * 
 * @author Keith Donald
 */
public class MvcExternalContext extends ServletExternalContext {

	/**
	 * Create a new external context wrapping given servlet HTTP request and response and given servlet context.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
