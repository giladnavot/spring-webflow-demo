---
title: The BindingModel class
---
This document will cover the class <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="84:3:3" line-data="	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,">`BindingModel`</SwmToken> in the Spring Web Flow project. We will explain:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="84:3:3" line-data="	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,">`BindingModel`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="84:3:3" line-data="	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,">`BindingModel`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="84:3:3" line-data="	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,">`BindingModel`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="84:3:3" line-data="	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,">`BindingModel`</SwmToken> class in <SwmPath>[spring-webflow/…/view/BindingModel.java](spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java)</SwmPath> makes the properties of the model object available to Spring views during rendering. It also makes data binding (mapping) results available after a form postback attempt and makes error messages available to the view. This class acts as a Spring Errors adapter for use with Spring form and bind tags.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="76">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="84:3:3" line-data="	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,">`BindingModel`</SwmToken> is the constructor for the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="84:3:3" line-data="	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,">`BindingModel`</SwmToken> class. It initializes the object with the provided parameters: <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="78:6:6" line-data="	 * @param objectName the name of the bound model object">`objectName`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="79:6:6" line-data="	 * @param boundObject the bound model object">`boundObject`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="80:6:6" line-data="	 * @param expressionParser the expression parser used to access model object properties">`expressionParser`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="81:6:6" line-data="	 * @param conversionService the registry used to access converters for formatting properties">`conversionService`</SwmToken>, and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="82:6:6" line-data="	 * @param messageContext the message context containing flow messages to display">`messageContext`</SwmToken>.

```java
	/**
	 * Creates a new Spring Binding model.
	 * @param objectName the name of the bound model object
	 * @param boundObject the bound model object
	 * @param expressionParser the expression parser used to access model object properties
	 * @param conversionService the registry used to access converters for formatting properties
	 * @param messageContext the message context containing flow messages to display
	 */
	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,
			ConversionService conversionService, MessageContext messageContext) {
		Assert.hasText(objectName, "The object name is required");
		Assert.notNull(boundObject, "The bound object instance is required");
		this.objectName = objectName;
		this.boundObject = boundObject;
		this.expressionParser = expressionParser;
		this.conversionService = conversionService;
		this.messageContext = messageContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="95">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="100:5:5" line-data="	public void setMappingResults(MappingResults results) {">`setMappingResults`</SwmToken> sets the results of a data mapping attempt onto the bound model object from the view.

```java
	/**
	 * Sets the results of a data mapping attempt onto the bound model object from the view.
	 * @see AbstractMvcView#processUserEvent()
	 * @param results
	 */
	public void setMappingResults(MappingResults results) {
		this.mappingResults = results;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="104">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="104:5:5" line-data="	public void setBinderConfiguration(BinderConfiguration binderConfiguration) {">`setBinderConfiguration`</SwmToken> sets the binder configuration for the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="84:3:3" line-data="	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,">`BindingModel`</SwmToken>.

```java
	public void setBinderConfiguration(BinderConfiguration binderConfiguration) {
		this.binderConfiguration = binderConfiguration;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="108">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="110:8:8" line-data="	public List&lt;ObjectError&gt; getAllErrors() {">`getAllErrors`</SwmToken> retrieves all errors from the message context that match the criteria for any source of errors.

```java
	// implementing Errors

	public List<ObjectError> getAllErrors() {
		return toErrors(messageContext.getMessagesByCriteria(ERRORS_ANY_SOURCE), ALL_ERRORS);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="114">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="114:8:8" line-data="	public List&lt;ObjectError&gt; getGlobalErrors() {">`getGlobalErrors`</SwmToken> retrieves global errors from the message context that do not have a field source.

```java
	public List<ObjectError> getGlobalErrors() {
		return toErrors(messageContext.getMessagesByCriteria(ERRORS_WITHOUT_FIELD_SOURCE), ALL_ERRORS);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="118">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="118:8:8" line-data="	public List&lt;FieldError&gt; getFieldErrors(String field) {">`getFieldErrors`</SwmToken> retrieves field-specific errors from the message context based on the provided field name.

```java
	public List<FieldError> getFieldErrors(String field) {
		field = fixedField(field);
		MessageCriteria messageCriteria;
		if (field.endsWith("*")) {
			String prefix = field.substring(0, field.length() - 1);
			messageCriteria = new FieldPrefixErrorMessage(prefix);
		} else {
			messageCriteria = new FieldErrorMessage(field);
		}
		return toErrors(messageContext.getMessagesByCriteria(messageCriteria), FIELD_ERRORS);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="130">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="130:6:6" line-data="	public Class&lt;?&gt; getFieldType(String field) {">`getFieldType`</SwmToken> returns the type of the specified field in the bound object.

```java
	public Class<?> getFieldType(String field) {
		return parseFieldExpression(fixedField(field), false).getValueType(boundObject);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="134">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken> returns the value of the specified field in the bound object, considering any mapping results.

```java
	public Object getFieldValue(String field) {
		field = fixedField(field);
		if (mappingResults != null) {
			List<MappingResult> results = mappingResults.getResults(new FieldErrorResult(field));
			if (!results.isEmpty()) {
				MappingResult fieldError = results.get(0);
				return fieldError.getOriginalValue();
			}
		}
		return getFormattedValue(field);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="146">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="148:8:8" line-data="	public List&lt;FieldError&gt; getFieldErrors() {">`getFieldErrors`</SwmToken> retrieves all field-specific errors from the message context.

```java
	// not typically used by mvc views, but implemented to be on the safe side

	public List<FieldError> getFieldErrors() {
		return toErrors(messageContext.getMessagesByCriteria(ERRORS_FIELD_SOURCE), FIELD_ERRORS);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="152">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="152:5:5" line-data="	public String getObjectName() {">`getObjectName`</SwmToken> returns the name of the bound model object.

```java
	public String getObjectName() {
		return objectName;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="156">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="158:5:5" line-data="	public void addAllErrors(Errors errors) {">`addAllErrors`</SwmToken> is not expected to be called during view rendering and throws an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="159:5:5" line-data="		throw new UnsupportedOperationException(&quot;Should not be called during view rendering&quot;);">`UnsupportedOperationException`</SwmToken>.

```java
	// never expected to be called by mvc views

	public void addAllErrors(Errors errors) {
		throw new UnsupportedOperationException("Should not be called during view rendering");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="162">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="162:5:5" line-data="	public void reject(String errorCode, Object[] errorArgs, String defaultMessage) {">`reject`</SwmToken> is not expected to be called during view rendering and throws an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="163:5:5" line-data="		throw new UnsupportedOperationException(&quot;Should not be called during view rendering&quot;);">`UnsupportedOperationException`</SwmToken>.

```java
	public void reject(String errorCode, Object[] errorArgs, String defaultMessage) {
		throw new UnsupportedOperationException("Should not be called during view rendering");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="166">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="166:5:5" line-data="	public void rejectValue(String field, String errorCode, Object[] errorArgs, String defaultMessage) {">`rejectValue`</SwmToken> is not expected to be called during view rendering and throws an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="167:5:5" line-data="		throw new UnsupportedOperationException(&quot;Should not be called during view rendering&quot;);">`UnsupportedOperationException`</SwmToken>.

```java
	public void rejectValue(String field, String errorCode, Object[] errorArgs, String defaultMessage) {
		throw new UnsupportedOperationException("Should not be called during view rendering");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="170">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="172:5:5" line-data="	public Object getTarget() {">`getTarget`</SwmToken> returns the bound model object.

```java
	// implementing BindingResult

	public Object getTarget() {
		return boundObject;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="176">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="176:5:5" line-data="	public Object getRawFieldValue(String field) {">`getRawFieldValue`</SwmToken> returns the raw value of the specified field in the bound object.

```java
	public Object getRawFieldValue(String field) {
		return parseFieldExpression(fixedField(field), false).getValue(boundObject);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="180">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="180:5:5" line-data="	public PropertyEditor findEditor(String field, Class&lt;?&gt; valueType) {">`findEditor`</SwmToken> finds a property editor for the specified field and value type.

```java
	public PropertyEditor findEditor(String field, Class<?> valueType) {
		if (field != null) {
			field = fixedField(field);
		}
		return findSpringConvertingPropertyEditor(field, valueType);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="187">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="189:5:5" line-data="	public void addError(ObjectError error) {">`addError`</SwmToken> is not expected to be called during view rendering and throws an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="190:5:5" line-data="		throw new UnsupportedOperationException(&quot;Should not be called during view rendering&quot;);">`UnsupportedOperationException`</SwmToken>.

```java
	// never expected to be called by mvc views

	public void addError(ObjectError error) {
		throw new UnsupportedOperationException("Should not be called during view rendering");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="193">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="193:11:11" line-data="	public Map&lt;String, Object&gt; getModel() {">`getModel`</SwmToken> is not expected to be called during view rendering and throws an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="194:5:5" line-data="		throw new UnsupportedOperationException(&quot;Should not be called during view rendering&quot;);">`UnsupportedOperationException`</SwmToken>.

```java
	public Map<String, Object> getModel() {
		throw new UnsupportedOperationException("Should not be called during view rendering");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="197">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="197:5:5" line-data="	public PropertyEditorRegistry getPropertyEditorRegistry() {">`getPropertyEditorRegistry`</SwmToken> is not expected to be called during view rendering and throws an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="198:5:5" line-data="		throw new UnsupportedOperationException(&quot;Should not be called during view rendering&quot;);">`UnsupportedOperationException`</SwmToken>.

```java
	public PropertyEditorRegistry getPropertyEditorRegistry() {
		throw new UnsupportedOperationException("Should not be called during view rendering");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="201">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="201:7:7" line-data="	public String[] getSuppressedFields() {">`getSuppressedFields`</SwmToken> is not expected to be called during view rendering and throws an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="202:5:5" line-data="		throw new UnsupportedOperationException(&quot;Should not be called during view rendering&quot;);">`UnsupportedOperationException`</SwmToken>.

```java
	public String[] getSuppressedFields() {
		throw new UnsupportedOperationException("Should not be called during view rendering");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="205">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="205:5:5" line-data="	public void recordSuppressedField(String field) {">`recordSuppressedField`</SwmToken> is not expected to be called during view rendering and throws an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="206:5:5" line-data="		throw new UnsupportedOperationException(&quot;Should not be called during view rendering&quot;);">`UnsupportedOperationException`</SwmToken>.

```java
	public void recordSuppressedField(String field) {
		throw new UnsupportedOperationException("Should not be called during view rendering");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="209">

---

The function <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="209:7:7" line-data="	public String[] resolveMessageCodes(String errorCode, String field) {">`resolveMessageCodes`</SwmToken> with parameters <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="209:11:11" line-data="	public String[] resolveMessageCodes(String errorCode, String field) {">`errorCode`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="209:16:16" line-data="	public String[] resolveMessageCodes(String errorCode, String field) {">`field`</SwmToken> is not expected to be called during view rendering and throws an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="210:5:5" line-data="		throw new UnsupportedOperationException(&quot;Should not be called during view rendering&quot;);">`UnsupportedOperationException`</SwmToken>.

```java
	public String[] resolveMessageCodes(String errorCode, String field) {
		throw new UnsupportedOperationException("Should not be called during view rendering");
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="608">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="97:6:6" line-data="	 * @see AbstractMvcView#processUserEvent()">`AbstractMvcView`</SwmToken> class, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="611:1:1" line-data="			BindingModel bindingModel = new BindingModel(getModelExpression().getExpressionString(), modelObject,">`BindingModel`</SwmToken> is instantiated within the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="608:5:5" line-data="	private void exposeBindingModel(Map&lt;String, Object&gt; model) {">`exposeBindingModel`</SwmToken> method. This method retrieves the model object and, if it is not null, creates a new <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="611:1:1" line-data="			BindingModel bindingModel = new BindingModel(getModelExpression().getExpressionString(), modelObject,">`BindingModel`</SwmToken> instance using various parameters such as the model expression string, the model object itself, the expression parser, the conversion service, and the message context from the request context.

```java
	private void exposeBindingModel(Map<String, Object> model) {
		Object modelObject = getModelObject();
		if (modelObject != null) {
			BindingModel bindingModel = new BindingModel(getModelExpression().getExpressionString(), modelObject,
					expressionParser, conversionService, requestContext.getMessageContext());
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="613">

---

After the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="84:3:3" line-data="	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,">`BindingModel`</SwmToken> instance is created, the method sets the binder configuration and mapping results on the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="84:3:3" line-data="	public BindingModel(String objectName, Object boundObject, ExpressionParser expressionParser,">`BindingModel`</SwmToken> instance. This setup is crucial for the binding process in the MVC view, ensuring that the model data is correctly bound to the view components.

```java
			bindingModel.setBinderConfiguration(binderConfiguration);
			bindingModel.setMappingResults(mappingResults);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
