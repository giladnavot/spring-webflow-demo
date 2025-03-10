---
title: The ValidationHelper class
---
This document will cover the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="93:3:3" line-data="	public ValidationHelper(Object model, RequestContext requestContext, String eventId,">`ValidationHelper`</SwmToken> class in the Spring Web Flow project. We will cover:

1. What <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="93:3:3" line-data="	public ValidationHelper(Object model, RequestContext requestContext, String eventId,">`ValidationHelper`</SwmToken> is.
2. The variables and functions defined in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="93:3:3" line-data="	public ValidationHelper(Object model, RequestContext requestContext, String eventId,">`ValidationHelper`</SwmToken>.

# What is <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="93:3:3" line-data="	public ValidationHelper(Object model, RequestContext requestContext, String eventId,">`ValidationHelper`</SwmToken>

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="93:3:3" line-data="	public ValidationHelper(Object model, RequestContext requestContext, String eventId,">`ValidationHelper`</SwmToken> class in <SwmPath>[spring-webflow/…/validation/ValidationHelper.java](spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java)</SwmPath> is a helper class that encapsulates conventions to invoke validation logic. It is used to validate model objects within the context of a web flow, ensuring that the data meets certain criteria before proceeding with the flow.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="76">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="93:3:3" line-data="	public ValidationHelper(Object model, RequestContext requestContext, String eventId,">`ValidationHelper`</SwmToken> constructor initializes the helper with the model object, request context, event ID, model name, expression parser, message codes resolver, mapping results, and validation hint resolver.

```java
	/**
	 * Create a throwaway validation helper object. Validation is invoked by the {@link #validate()} method.
	 * <p>
	 * Validation methods invoked include a validation method on the model object or a validator bean. The method name
	 * on either object is in the form of validate[viewStateId]. A ValidationContext is passed in the method signature
	 * along with the model object for validator beans. A MessageContext can be substituted for the ValidationContext.
	 * <p>
	 * For example: <code>model.validateEnterBookingDetails(VaticationContext)</code> or
	 * <code>context.getBean("modelValidator").validateEnterBookingDetails(model, VaticationContext)</code>
	 *
	 * @param model the object to validate
	 * @param requestContext the context for the request
	 * @param eventId the event triggering validation
	 * @param modelName the name of the model object
	 * @param expressionParser the expression parser
	 * @param mappingResults object mapping results
	 */
	public ValidationHelper(Object model, RequestContext requestContext, String eventId,
			String modelName, ExpressionParser expressionParser, MessageCodesResolver messageCodesResolver,
			MappingResults mappingResults, ValidationHintResolver hintResolver) {

		Assert.notNull(model, "The model to validate is required");
		Assert.notNull(requestContext, "The request context for the validator is required");
		this.model = model;
		this.requestContext = requestContext;
		this.eventId = eventId;
		this.modelName = modelName;
		this.expressionParser = expressionParser;
		this.messageCodesResolver = messageCodesResolver;
		this.mappingResults = mappingResults;
		this.validationHints = initValidationHints(model, requestContext, eventId, hintResolver);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="109">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="112:3:3" line-data="	public ValidationHelper(Object model, RequestContext requestContext, String eventId,">`ValidationHelper`</SwmToken> constructor initializes the helper with the model object, request context, event ID, model name, expression parser, message codes resolver, and mapping results, using a default <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="110:23:23" line-data="	 * An alternative constructor that creates an instance of {@link BeanValidationHintResolver}.">`BeanValidationHintResolver`</SwmToken>.

```java
	/**
	 * An alternative constructor that creates an instance of {@link BeanValidationHintResolver}.
	 */
	public ValidationHelper(Object model, RequestContext requestContext, String eventId,
			String modelName, ExpressionParser expressionParser, MessageCodesResolver messageCodesResolver,
			MappingResults mappingResults) {

		this(model, requestContext, eventId, modelName, expressionParser,
				messageCodesResolver, mappingResults, new BeanValidationHintResolver());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="121">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="121:9:9" line-data="	private static Object[] initValidationHints(Object model, RequestContext requestContext, String eventId,">`initValidationHints`</SwmToken> function initializes validation hints based on the model, request context, event ID, and validation hint resolver.

```java
	private static Object[] initValidationHints(Object model, RequestContext requestContext, String eventId,
			ValidationHintResolver hintResolver) {

		Expression expr = null;
		TransitionDefinition transition = requestContext.getMatchingTransition(eventId);
		if (transition != null) {
			expr = (Expression) transition.getAttributes().get("validationHints");
		}
		if (expr == null) {
			expr = (Expression) requestContext.getCurrentState().getAttributes().get("validationHints");
		}
		if (expr == null) {
			return null;
		}
		String flowId = requestContext.getActiveFlow().getId();
		String stateId = requestContext.getCurrentState().getId();
		try {
			Object hintsValue = expr.getValue(requestContext);
			if (hintsValue instanceof String) {
				String[] hints = StringUtils.commaDelimitedListToStringArray((String) hintsValue);
				return hintResolver.resolveValidationHints(model, flowId, stateId, hints);
			}
			else if (hintsValue instanceof Object[]) {
				return (Object[]) hintsValue;
			}
			else {
				throw new FlowExecutionException(flowId, stateId,
						"Failed to resolve validation hints [" + hintsValue + "]");
			}
		}
		catch (EvaluationException e) {
			throw new FlowExecutionException(flowId, stateId,
					"Failed to resolve validation hints expression [" + expr + "]", e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="157">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="160:5:5" line-data="	public void setValidator(Validator validator) {">`setValidator`</SwmToken> function configures a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="158:11:11" line-data="	 * Configure a {@link Validator} to apply to the model.">`Validator`</SwmToken> to apply to the model.

```java
	/**
	 * Configure a {@link Validator} to apply to the model.
	 */
	public void setValidator(Validator validator) {
		this.validator = validator;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="164">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="169:5:5" line-data="	public void setValidationHints(Object[] validationHints) {">`setValidationHints`</SwmToken> function provides validation hints (<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="165:10:12" line-data="	 * Provide validation hints (e.g. JSR-303 validation groups). Note that the constructor">`e.g`</SwmToken>., <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="165:15:17" line-data="	 * Provide validation hints (e.g. JSR-303 validation groups). Note that the constructor">`JSR-303`</SwmToken> validation groups).

```java
	/**
	 * Provide validation hints (e.g. JSR-303 validation groups). Note that the constructor
	 * automatically detects validation hints specified on a view state or a transition.
	 * Therefore use of this method should not be needed.
	 */
	public void setValidationHints(Object[] validationHints) {
		this.validationHints = validationHints;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="173">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="176:5:5" line-data="	public void validate() {">`validate`</SwmToken> function invokes the validators available by convention.

```java
	/**
	 * Invoke the validators available by convention.
	 */
	public void validate() {
		if (this.validator != null) {
			invokeValidatorDefaultValidateMethod(this.validator);
		}
		invokeModelValidationMethod(model);
		Object modelValidator = getModelValidator();
		if (modelValidator != null) {
			invokeModelValidator(modelValidator);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="187">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="187:5:5" line-data="	private void invokeModelValidationMethod(Object model) {">`invokeModelValidationMethod`</SwmToken> function invokes validation methods on the model object for the current state and default validation.

```java
	private void invokeModelValidationMethod(Object model) {
		invokeValidateMethodForCurrentState(model);
		invokeDefaultValidateMethod(model);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="192">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="192:5:5" line-data="	private boolean invokeValidateMethodForCurrentState(Object model) {">`invokeValidateMethodForCurrentState`</SwmToken> function invokes the validation method for the current state on the model object.

```java
	private boolean invokeValidateMethodForCurrentState(Object model) {
		String methodName = "validate" + StringUtils.capitalize(requestContext.getCurrentState().getId());
		// preferred
		Method validateMethod = ReflectionUtils.findMethod(model.getClass(), methodName, ValidationContext.class);
		if (validateMethod != null) {
			if (logger.isDebugEnabled()) {
				logger.debug("Invoking current state model validation method '" + methodName + "(ValidationContext)'");
			}
			ReflectionUtils.invokeMethod(validateMethod, model, new DefaultValidationContext(requestContext, eventId, mappingResults));
			return true;
		}
		// web flow 2.0.3 or < compatibility only
		validateMethod = ReflectionUtils.findMethod(model.getClass(), methodName, MessageContext.class);
		if (validateMethod != null) {
			ReflectionUtils.invokeMethod(validateMethod, model, requestContext.getMessageContext());
			return true;
		}
		// mvc 2 compatibility only
		validateMethod = ReflectionUtils.findMethod(model.getClass(), methodName, Errors.class);
		if (validateMethod != null) {
			MessageContextErrors errors = new MessageContextErrors(requestContext.getMessageContext(), modelName,
					model, expressionParser, messageCodesResolver, mappingResults);
			if (logger.isDebugEnabled()) {
				logger.debug("Invoking current state model validation method '" + methodName + "(Errors)'");
			}
			ReflectionUtils.invokeMethod(validateMethod, model, errors);
			return true;
		}
		return false;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="223">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="223:5:5" line-data="	private boolean invokeDefaultValidateMethod(Object model) {">`invokeDefaultValidateMethod`</SwmToken> function invokes the default validation method on the model object.

```java
	private boolean invokeDefaultValidateMethod(Object model) {
		// preferred
		Method validateMethod = ReflectionUtils.findMethod(model.getClass(), "validate", ValidationContext.class);
		if (validateMethod != null) {
			if (logger.isDebugEnabled()) {
				logger.debug("Invoking default model validation method 'validate(ValidationContext)'");
			}
			ReflectionUtils.invokeMethod(validateMethod, model, new DefaultValidationContext(requestContext, eventId, mappingResults));
			return true;
		}
		// mvc 2 compatibility only
		validateMethod = ReflectionUtils.findMethod(model.getClass(), "validate", Errors.class);
		if (validateMethod != null) {
			if (logger.isDebugEnabled()) {
				logger.debug("Invoking default model validation method 'validate(Errors)'");
			}
			MessageContextErrors errors = new MessageContextErrors(requestContext.getMessageContext(), modelName,
					model, expressionParser, messageCodesResolver, mappingResults);
			ReflectionUtils.invokeMethod(validateMethod, model, errors);
			return true;
		}
		return false;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="247">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="247:5:5" line-data="	private Object getModelValidator() {">`getModelValidator`</SwmToken> function retrieves the validator bean for the model object from the application context.

```java
	private Object getModelValidator() {
		BeanFactory beanFactory = requestContext.getActiveFlow().getApplicationContext();
		if (beanFactory != null && StringUtils.hasText(modelName)) {
			String validatorName = modelName + "Validator";
			if (beanFactory.containsBean(validatorName)) {
				return beanFactory.getBean(validatorName);
			}
		}
		return null;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="258">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="258:5:5" line-data="	private void invokeModelValidator(Object validator) {">`invokeModelValidator`</SwmToken> function invokes validation methods on the validator bean for the current state and default validation.

```java
	private void invokeModelValidator(Object validator) {
		invokeValidatorValidateMethodForCurrentState(validator);
		invokeValidatorDefaultValidateMethod(validator);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="263">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="263:5:5" line-data="	private boolean invokeValidatorValidateMethodForCurrentState(Object validator) {">`invokeValidatorValidateMethodForCurrentState`</SwmToken> function invokes the validation method for the current state on the validator bean.

```java
	private boolean invokeValidatorValidateMethodForCurrentState(Object validator) {
		String methodName = "validate" + StringUtils.capitalize(requestContext.getCurrentState().getId());
		// preferred
		Method validateMethod = findValidationMethod(model, validator, methodName, ValidationContext.class);
		if (validateMethod != null) {
			if (logger.isDebugEnabled()) {
				logger.debug("Invoking current state validator method '"
						+ ClassUtils.getShortName(validator.getClass()) + "." + methodName + "("
						+ ClassUtils.getShortName(model.getClass()) + ", ValidationContext)'");
			}
			ReflectionUtils.invokeMethod(validateMethod, validator, model,
					new DefaultValidationContext(requestContext, eventId, mappingResults));
			return true;
		}
		// mvc 2 compatibility only
		validateMethod = findValidationMethod(model, validator, methodName, Errors.class);
		if (validateMethod != null) {
			if (logger.isDebugEnabled()) {
				logger.debug("Invoking current state validator method '"
						+ ClassUtils.getShortName(validator.getClass()) + "." + methodName + "("
						+ ClassUtils.getShortName(model.getClass()) + ", Errors)'");
			}
			MessageContextErrors errors = new MessageContextErrors(requestContext.getMessageContext(), modelName,
					model, expressionParser, messageCodesResolver, mappingResults);
			ReflectionUtils.invokeMethod(validateMethod, validator, model, errors);
			return true;
		}
		// web flow 2.0.0 to 2.0.3 compatibility only [to remove in web flow 3]
		validateMethod = findValidationMethod(model, validator, methodName, MessageContext.class);
		if (validateMethod != null) {
			ReflectionUtils.invokeMethod(validateMethod, validator,
					model, requestContext.getMessageContext());
			return true;
		}
		return false;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="300">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="300:5:5" line-data="	private boolean invokeValidatorDefaultValidateMethod(Object validator) {">`invokeValidatorDefaultValidateMethod`</SwmToken> function invokes the default validation method on the validator bean.

```java
	private boolean invokeValidatorDefaultValidateMethod(Object validator) {
		if (validator instanceof Validator) {
			// Spring Framework Validator type
			Validator springValidator = (Validator) validator;
			if (logger.isDebugEnabled()) {
				logger.debug("Invoking Spring Validator '" + ClassUtils.getShortName(validator.getClass()) + "'");
			}
			if (springValidator.supports(model.getClass())) {
				MessageContextErrors errors = new MessageContextErrors(requestContext.getMessageContext(), modelName,
						model, expressionParser, messageCodesResolver, mappingResults);

				if (this.validationHints != null) {
					if (springValidator instanceof SmartValidator) {
						((SmartValidator) springValidator).validate(model, errors, this.validationHints);
					}
					else {
						logger.warn("Validation hints provided but validator not an instance of SmartValidator: ["
								+ springValidator.getClass().getName() + "]");
					}
				}
				else {
					springValidator.validate(model, errors);
				}
			} else {
				if (logger.isDebugEnabled()) {
					logger.debug("Spring Validator '" + ClassUtils.getShortName(validator.getClass())
							+ "' doesn't support model class " + model.getClass());
				}
			}
			return true;
		}
		// preferred
		Method validateMethod = findValidationMethod(model, validator, "validate", ValidationContext.class);
		if (validateMethod != null) {
			if (logger.isDebugEnabled()) {
				logger.debug("Invoking default validator method '" + ClassUtils.getShortName(validator.getClass())
						+ ".validate(" + ClassUtils.getShortName(model.getClass()) + ", ValidationContext)'");
			}
			ReflectionUtils.invokeMethod(validateMethod, validator, model,
					new DefaultValidationContext(requestContext, eventId, mappingResults));
			return true;
		}
		// mvc 2 compatibility only
		validateMethod = findValidationMethod(model, validator, "validate", Errors.class);
		if (validateMethod != null) {
			if (logger.isDebugEnabled()) {
				logger.debug("Invoking default validator method '" + ClassUtils.getShortName(validator.getClass())
						+ ".validate(" + ClassUtils.getShortName(model.getClass()) + ", Errors)'");
			}
			MessageContextErrors errors = new MessageContextErrors(requestContext.getMessageContext(), modelName,
					model, expressionParser, messageCodesResolver, mappingResults);
			ReflectionUtils.invokeMethod(validateMethod, validator, model, errors);
			return true;
		}
		return false;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="357">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="357:5:5" line-data="	private Method findValidationMethod(Object model, Object validator, String methodName, Class&lt;?&gt; context) {">`findValidationMethod`</SwmToken> function finds the validation method on the validator bean for the given method name and context.

```java
	private Method findValidationMethod(Object model, Object validator, String methodName, Class<?> context) {
		Class<?> modelClass = AopUtils.getTargetClass(model);

		List<Class<?>> modelSearchClasses = new ArrayList<>();
		while (modelClass != null) {
			modelSearchClasses.add(modelClass);
			modelClass = modelClass.getSuperclass();
		}
		for (Class<?> searchClass : modelSearchClasses) {
			Method method = ReflectionUtils.findMethod(validator.getClass(), methodName, searchClass, context);
			if (method != null) {
				return method;
			}
		}
		return null;
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-faces/src/main/java/org/springframework/faces/webflow/FlowActionListener.java" line="160">

---

In the <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowActionListener.java" pos="54:4:4" line-data="public class FlowActionListener implements ActionListener {">`FlowActionListener`</SwmToken> class, <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowActionListener.java" pos="163:1:1" line-data="		ValidationHelper helper = new ValidationHelper(model, requestContext, eventId,">`ValidationHelper`</SwmToken> is instantiated with parameters such as <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowActionListener.java" pos="163:11:11" line-data="		ValidationHelper helper = new ValidationHelper(model, requestContext, eventId,">`model`</SwmToken>, <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowActionListener.java" pos="161:11:11" line-data="		Validator validator = (Validator) requestContext.getActiveFlow().getAttributes().get(attr);">`requestContext`</SwmToken>, <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowActionListener.java" pos="163:17:17" line-data="		ValidationHelper helper = new ValidationHelper(model, requestContext, eventId,">`eventId`</SwmToken>, <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowActionListener.java" pos="164:1:1" line-data="				modelName, null, this.messageCodesResolver, null, getHintResolver(requestContext));">`modelName`</SwmToken>, and others. The <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowActionListener.java" pos="161:3:3" line-data="		Validator validator = (Validator) requestContext.getActiveFlow().getAttributes().get(attr);">`validator`</SwmToken> is then set using the <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowActionListener.java" pos="165:3:3" line-data="		helper.setValidator(validator);">`setValidator`</SwmToken> method, and the <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/FlowActionListener.java" pos="166:3:3" line-data="		helper.validate();">`validate`</SwmToken> method is called to perform the validation.

```java
		String attr = FlowModelFlowBuilder.VALIDATOR_FLOW_ATTR;
		Validator validator = (Validator) requestContext.getActiveFlow().getAttributes().get(attr);

		ValidationHelper helper = new ValidationHelper(model, requestContext, eventId,
				modelName, null, this.messageCodesResolver, null, getHintResolver(requestContext));
		helper.setValidator(validator);
		helper.validate();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" line="682">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="73:6:6" line-data="public abstract class AbstractMvcView implements View {">`AbstractMvcView`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="685:1:1" line-data="		ValidationHelper helper = new ValidationHelper(model, requestContext, eventId, getModelExpression()">`ValidationHelper`</SwmToken> is used similarly. It is created with parameters including <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="683:8:8" line-data="			logger.debug(&quot;Validating model&quot;);">`model`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="685:14:14" line-data="		ValidationHelper helper = new ValidationHelper(model, requestContext, eventId, getModelExpression()">`requestContext`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="685:17:17" line-data="		ValidationHelper helper = new ValidationHelper(model, requestContext, eventId, getModelExpression()">`eventId`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="611:11:17" line-data="			BindingModel bindingModel = new BindingModel(getModelExpression().getExpressionString(), modelObject,">`getModelExpression().getExpressionString()`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="686:7:7" line-data="				.getExpressionString(), expressionParser, messageCodesResolver, mappingResults, validationHintResolver);">`expressionParser`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="686:10:10" line-data="				.getExpressionString(), expressionParser, messageCodesResolver, mappingResults, validationHintResolver);">`messageCodesResolver`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="686:13:13" line-data="				.getExpressionString(), expressionParser, messageCodesResolver, mappingResults, validationHintResolver);">`mappingResults`</SwmToken>, and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="686:16:16" line-data="				.getExpressionString(), expressionParser, messageCodesResolver, mappingResults, validationHintResolver);">`validationHintResolver`</SwmToken>. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="687:7:7" line-data="		helper.setValidator(this.validator);">`validator`</SwmToken> is set, and the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/AbstractMvcView.java" pos="688:3:3" line-data="		helper.validate();">`validate`</SwmToken> method is invoked to validate the model.

```java
		if (logger.isDebugEnabled()) {
			logger.debug("Validating model");
		}
		ValidationHelper helper = new ValidationHelper(model, requestContext, eventId, getModelExpression()
				.getExpressionString(), expressionParser, messageCodesResolver, mappingResults, validationHintResolver);
		helper.setValidator(this.validator);
		helper.validate();
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
