---
title: The AbstractMvcView class
---
This document will provide an overview of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="114:3:3" line-data="	public AbstractMvcView(org.springframework.web.servlet.View view, RequestContext requestContext) {">`AbstractMvcView`</SwmToken> class. We will cover:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="114:3:3" line-data="	public AbstractMvcView(org.springframework.web.servlet.View view, RequestContext requestContext) {">`AbstractMvcView`</SwmToken> is.
2. Variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="114:3:3" line-data="	public AbstractMvcView(org.springframework.web.servlet.View view, RequestContext requestContext) {">`AbstractMvcView`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="114:3:3" line-data="	public AbstractMvcView(org.springframework.web.servlet.View view, RequestContext requestContext) {">`AbstractMvcView`</SwmToken>

<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="114:3:3" line-data="	public AbstractMvcView(org.springframework.web.servlet.View view, RequestContext requestContext) {">`AbstractMvcView`</SwmToken> is a base view implementation for the Spring Web MVC Servlet frameworks. It is used to render views in a web flow context, manage user events, and handle model binding and validation.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="114">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="114:3:3" line-data="	public AbstractMvcView(org.springframework.web.servlet.View view, RequestContext requestContext) {">`AbstractMvcView`</SwmToken> is a constructor that creates a new MVC view. It takes a Spring MVC view to render and the current flow request context as parameters.

```java
	public AbstractMvcView(org.springframework.web.servlet.View view, RequestContext requestContext) {
		this.view = view;
		this.requestContext = requestContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="123">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="123:5:5" line-data="	public void setExpressionParser(ExpressionParser expressionParser) {">`setExpressionParser`</SwmToken> sets the expression parser to use to parse model expressions.

```java
	public void setExpressionParser(ExpressionParser expressionParser) {
		this.expressionParser = expressionParser;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="131">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="131:5:5" line-data="	public void setConversionService(ConversionService conversionService) {">`setConversionService`</SwmToken> sets the service to use to expose formatters for field values.

```java
	public void setConversionService(ConversionService conversionService) {
		this.conversionService = conversionService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="135">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="135:5:5" line-data="	public void setValidator(Validator validator) {">`setValidator`</SwmToken> sets the validator to use for model validation.

```java
	public void setValidator(Validator validator) {
		this.validator = validator;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="139">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="139:5:5" line-data="	public void setValidationHintResolver(ValidationHintResolver validationHintResolver) {">`setValidationHintResolver`</SwmToken> sets the validation hint resolver to use.

```java
	public void setValidationHintResolver(ValidationHintResolver validationHintResolver) {
		if (validationHintResolver != null) {
			this.validationHintResolver = validationHintResolver;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="149">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="149:5:5" line-data="	public void setBinderConfiguration(BinderConfiguration binderConfiguration) {">`setBinderConfiguration`</SwmToken> sets the configuration describing how this view should bind to its model to access data for rendering.

```java
	public void setBinderConfiguration(BinderConfiguration binderConfiguration) {
		this.binderConfiguration = binderConfiguration;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="157">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="157:5:5" line-data="	public void setMessageCodesResolver(MessageCodesResolver messageCodesResolver) {">`setMessageCodesResolver`</SwmToken> sets the message codes resolver to use to resolve bind and validation failure message codes.

```java
	public void setMessageCodesResolver(MessageCodesResolver messageCodesResolver) {
		this.messageCodesResolver = messageCodesResolver;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="176">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="176:5:5" line-data="	public void setFieldMarkerPrefix(String fieldMarkerPrefix) {">`setFieldMarkerPrefix`</SwmToken> specifies a prefix that can be used for parameters that mark potentially empty fields.

```java
	public void setFieldMarkerPrefix(String fieldMarkerPrefix) {
		this.fieldMarkerPrefix = fieldMarkerPrefix;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="185">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="185:5:5" line-data="	public void setEventIdParameterName(String eventIdParameterName) {">`setEventIdParameterName`</SwmToken> sets the name of the request parameter to use to lookup user events signaled by this view.

```java
	public void setEventIdParameterName(String eventIdParameterName) {
		this.eventIdParameterName = eventIdParameterName;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="189">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="189:5:5" line-data="	public void render() throws IOException {">`render`</SwmToken> renders the view with the provided model data.

```java
	public void render() throws IOException {
		Map<String, Object> model = new HashMap<>();
		model.putAll(flowScopes());
		exposeBindingModel(model);
		model.put("flowRequestContext", requestContext);
		FlowExecutionKey key = requestContext.getFlowExecutionContext().getKey();
		if (key != null) {
			model.put("flowExecutionKey", requestContext.getFlowExecutionContext().getKey().toString());
			model.put("flowExecutionUrl", requestContext.getFlowExecutionUrl());
		}
		model.put("currentUser", requestContext.getExternalContext().getCurrentUser());
		try {
			if (logger.isDebugEnabled()) {
				logger.debug("Rendering MVC [" + view + "] with model map [" + model + "]");
			}
			doRender(model);
		} catch (IOException e) {
			throw e;
		} catch (Exception e) {
			IllegalStateException ise = new IllegalStateException("Exception occurred rendering view " + view);
			ise.initCause(e);
			throw ise;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="214">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="214:5:5" line-data="	public boolean userEventQueued() {">`userEventQueued`</SwmToken> checks if a user event is queued for processing.

```java
	public boolean userEventQueued() {
		return !userEventProcessed && getEventId() != null;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="218">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="218:5:5" line-data="	public void processUserEvent() {">`processUserEvent`</SwmToken> processes the user event signaled by this view.

```java
	public void processUserEvent() {
		String eventId = getEventId();
		if (eventId == null) {
			return;
		}
		if (logger.isDebugEnabled()) {
			logger.debug("Processing user event '" + eventId + "'");
		}
		Object model = getModelObject();
		if (model != null) {
			if (logger.isDebugEnabled()) {
				logger.debug("Resolved model " + model);
			}
			TransitionDefinition transition = requestContext.getMatchingTransition(eventId);
			if (shouldBind(model, transition)) {
				mappingResults = bind(model);
				if (hasErrors(mappingResults)) {
					if (logger.isDebugEnabled()) {
						logger.debug("Model binding resulted in errors; adding error messages to context");
					}
					addErrorMessages(mappingResults);
				}
				if (shouldValidate(model, transition)) {
					validate(model, transition);
				}
			}
		} else {
			if (logger.isDebugEnabled()) {
				logger.debug("No model to bind to; done processing user event");
			}
		}
		userEventProcessed = true;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="252">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="252:5:5" line-data="	public Serializable getUserEventState() {">`getUserEventState`</SwmToken> returns the state of the user event being processed.

```java
	public Serializable getUserEventState() {
		return new ViewActionStateHolder(eventId, userEventProcessed, mappingResults);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="256">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="256:5:5" line-data="	public boolean hasFlowEvent() {">`hasFlowEvent`</SwmToken> checks if there is a flow event to process.

```java
	public boolean hasFlowEvent() {
		return userEventProcessed && !requestContext.getMessageContext().hasErrorMessages();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="260">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="260:5:5" line-data="	public Event getFlowEvent() {">`getFlowEvent`</SwmToken> returns the flow event to process.

```java
	public Event getFlowEvent() {
		if (!hasFlowEvent()) {
			return null;
		}
		return new Event(this, getEventId(), requestContext.getRequestParameters().asAttributeMap());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="267">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="267:5:5" line-data="	public void saveState() {">`saveState`</SwmToken> saves the state of the view.

```java
	public void saveState() {

	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="271">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="271:5:5" line-data="	public String toString() {">`toString`</SwmToken> returns a string representation of the view.

```java
	public String toString() {
		return new ToStringCreator(this).append("view", view).toString();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="281">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="281:5:5" line-data="	protected RequestContext getRequestContext() {">`getRequestContext`</SwmToken> returns the current flow request context.

```java
	protected RequestContext getRequestContext() {
		return requestContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="289">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="289:13:13" line-data="	protected org.springframework.web.servlet.View getView() {">`getView`</SwmToken> returns the Spring MVC view to render.

```java
	protected org.springframework.web.servlet.View getView() {
		return view;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="296">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="296:5:5" line-data="	protected ConversionService getConversionService() {">`getConversionService`</SwmToken> returns the configured <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="296:3:3" line-data="	protected ConversionService getConversionService() {">`ConversionService`</SwmToken>.

```java
	protected ConversionService getConversionService() {
		return conversionService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="305">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="305:7:7" line-data="	protected abstract void doRender(Map&lt;String, ?&gt; model) throws Exception;">`doRender`</SwmToken> is a template method that subclasses should override to execute the view rendering logic.

```java
	protected abstract void doRender(Map<String, ?> model) throws Exception;

```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="311">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="311:5:5" line-data="	protected String getEventId() {">`getEventId`</SwmToken> returns the id of the user event being processed.

```java
	protected String getEventId() {
		if (eventId == null) {
			eventId = determineEventId(requestContext);
		}
		return this.eventId;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="326">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="326:5:5" line-data="	protected boolean shouldBind(Object model, TransitionDefinition transition) {">`shouldBind`</SwmToken> determines if model data binding should be invoked given the Transition that matched the current user event being processed.

```java
	protected boolean shouldBind(Object model, TransitionDefinition transition) {
		if (transition == null) {
			return true;
		}
		return transition.getAttributes().getBoolean("bind", true);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="337">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="337:5:5" line-data="	protected MappingResults getMappingResults() {">`getMappingResults`</SwmToken> returns the results of binding to the view's model, if model binding has occurred.

```java
	protected MappingResults getMappingResults() {
		return mappingResults;
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcViewFactory.java" line="93">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="562:6:6" line-data="	 * @see AbstractMvcViewFactory#getView(RequestContext)">`AbstractMvcViewFactory`</SwmToken> class, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcViewFactory.java" pos="96:1:1" line-data="		AbstractMvcView mvcView = createMvcView(view, context);">`AbstractMvcView`</SwmToken> is used to create and configure MVC views. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcViewFactory.java" pos="93:5:5" line-data="	public View getView(RequestContext context) {">`getView`</SwmToken> method retrieves the view ID, resolves the view, and then creates an instance of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcViewFactory.java" pos="96:1:1" line-data="		AbstractMvcView mvcView = createMvcView(view, context);">`AbstractMvcView`</SwmToken>. This instance is further configured with an expression parser, conversion service, and binder configuration.

```java
	public View getView(RequestContext context) {
		String viewId = (String) this.viewId.getValue(context);
		org.springframework.web.servlet.View view = viewResolver.resolveView(viewId, context);
		AbstractMvcView mvcView = createMvcView(view, context);
		mvcView.setExpressionParser(expressionParser);
		mvcView.setConversionService(conversionService);
		mvcView.setBinderConfiguration(binderConfiguration);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcViewFactory.java" line="123">

---

Additionally, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="562:6:6" line-data="	 * @see AbstractMvcViewFactory#getView(RequestContext)">`AbstractMvcViewFactory`</SwmToken> class contains an abstract method <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcViewFactory.java" pos="123:7:7" line-data="	protected abstract AbstractMvcView createMvcView(org.springframework.web.servlet.View view, RequestContext context);">`createMvcView`</SwmToken> which is responsible for creating instances of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcViewFactory.java" pos="123:5:5" line-data="	protected abstract AbstractMvcView createMvcView(org.springframework.web.servlet.View view, RequestContext context);">`AbstractMvcView`</SwmToken>. This method is intended to be implemented by subclasses to provide specific MVC view implementations.

```java
	protected abstract AbstractMvcView createMvcView(org.springframework.web.servlet.View view, RequestContext context);

```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcViewFactory.java" line="50">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcViewFactory.java" pos="34:4:4" line-data="public class ServletMvcViewFactory extends AbstractMvcViewFactory {">`ServletMvcViewFactory`</SwmToken> class, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcViewFactory.java" pos="50:5:5" line-data="	protected AbstractMvcView createMvcView(View view, RequestContext context) {">`createMvcView`</SwmToken> method is implemented to return an instance of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcViewFactory.java" pos="51:5:5" line-data="		return new ServletMvcView(view, context);">`ServletMvcView`</SwmToken>, which is a concrete subclass of <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcViewFactory.java" pos="50:3:3" line-data="	protected AbstractMvcView createMvcView(View view, RequestContext context) {">`AbstractMvcView`</SwmToken>. This demonstrates how the abstract method from <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="562:6:6" line-data="	 * @see AbstractMvcViewFactory#getView(RequestContext)">`AbstractMvcViewFactory`</SwmToken> is used to create specific types of MVC views.

```java
	protected AbstractMvcView createMvcView(View view, RequestContext context) {
		return new ServletMvcView(view, context);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" line="33">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="33:4:4" line-data="public class ServletMvcView extends AbstractMvcView {">`ServletMvcView`</SwmToken> class extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcView.java" pos="33:8:8" line-data="public class ServletMvcView extends AbstractMvcView {">`AbstractMvcView`</SwmToken> and represents a specific implementation of an MVC view for Spring Web Servlet. This class is used to create and manage <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/servlet/ServletMvcViewFactory.java" pos="37:9:11" line-data="	 * Creates a new servlet-based MVC view factory.">`servlet-based`</SwmToken> MVC views within the web flow framework.

```java
public class ServletMvcView extends AbstractMvcView {

	/**
	 * Creates a new Servlet MVC view.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
