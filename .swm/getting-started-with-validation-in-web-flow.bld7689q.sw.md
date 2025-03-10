---
title: Getting Started with Validation in Web Flow
---
# Getting Started with Validation in Web Flow

Validation in Web Flow refers to the process of ensuring that data entered by users meets certain criteria before it is processed or stored.

## What is Validation

Validation ensures that user input meets predefined criteria, preventing invalid data from being processed or stored. This is crucial for maintaining data integrity and providing a seamless user experience.

## How Validation is Used

Validation can be performed programmatically by defining a separate object, called a validator, which validates your model object. To do this, create a class whose name follows the pattern `${model}Validator`, where `${model}` is the capitalized form of the model expression, such as `Booking`. Then define a public method with a name of `validate${state}`, where `${state}` is the ID of your `view-state`, such as `enterBookingDetails`.

## Where Validation is Used

Validation is used in the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="53:4:4" line-data="public class ValidationHelper {">`ValidationHelper`</SwmToken> class, which encapsulates conventions to invoke validation logic. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="313:9:9" line-data="						((SmartValidator) springValidator).validate(model, errors, this.validationHints);">`validate`</SwmToken> method in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="53:4:4" line-data="public class ValidationHelper {">`ValidationHelper`</SwmToken> is responsible for invoking the appropriate validation methods on the model object or a validator bean.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" line="300">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="313:9:9" line-data="						((SmartValidator) springValidator).validate(model, errors, this.validationHints);">`validate`</SwmToken> method in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="53:4:4" line-data="public class ValidationHelper {">`ValidationHelper`</SwmToken> is responsible for invoking the appropriate validation methods on the model object or a validator bean. For example, the method <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="300:5:5" line-data="	private boolean invokeValidatorDefaultValidateMethod(Object validator) {">`invokeValidatorDefaultValidateMethod`</SwmToken> is called within <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="313:9:9" line-data="						((SmartValidator) springValidator).validate(model, errors, this.validationHints);">`validate`</SwmToken> to invoke the default validation method on the validator object.

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
```

---

</SwmSnippet>

## Validation Methods

Validation methods can be named according to the current state of the flow, such as <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="80:19:22" line-data="	 * on either object is in the form of validate[viewStateId]. A ValidationContext is passed in the method signature">`validate[viewStateId]`</SwmToken>, and can accept a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="33:10:10" line-data="import org.springframework.binding.validation.ValidationContext;">`ValidationContext`</SwmToken> or <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="31:10:10" line-data="import org.springframework.binding.message.MessageContext;">`MessageContext`</SwmToken> as parameters.

## Validation Hint Resolver

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="95:6:6" line-data="			MappingResults mappingResults, ValidationHintResolver hintResolver) {">`ValidationHintResolver`</SwmToken> interface provides a strategy for resolving string-based hints to objects, such as validation groups against a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/validation/ValidationHelper.java" pos="165:15:17" line-data="	 * Provide validation hints (e.g. JSR-303 validation groups). Note that the constructor">`JSR-303`</SwmToken> provider.

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
