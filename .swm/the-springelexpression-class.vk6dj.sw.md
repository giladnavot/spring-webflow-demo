---
title: The SpringELExpression class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="50:7:7" line-data="	 * Constructor for SpringELExpression.">`SpringELExpression`</SwmToken> in detail. We will discuss:

1. What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="50:7:7" line-data="	 * Constructor for SpringELExpression.">`SpringELExpression`</SwmToken>
2. Variables and functions in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="50:7:7" line-data="	 * Constructor for SpringELExpression.">`SpringELExpression`</SwmToken>

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="50:7:7" line-data="	 * Constructor for SpringELExpression.">`SpringELExpression`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="50:7:7" line-data="	 * Constructor for SpringELExpression.">`SpringELExpression`</SwmToken> class is a wrapper for a Spring Expression Language (EL) <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="61:11:11" line-data="	public SpringELExpression(org.springframework.expression.Expression expression,">`Expression`</SwmToken>, allowing it to be used under the Spring Binding <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="61:11:11" line-data="	public SpringELExpression(org.springframework.expression.Expression expression,">`Expression`</SwmToken> abstraction. It provides a way to evaluate expressions in a Spring context, supporting features like type conversion and property access.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" line="49">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="50:7:7" line-data="	 * Constructor for SpringELExpression.">`SpringELExpression`</SwmToken> constructor initializes the class with a parsed Spring EL expression instance, a mapping of variable names to parsed expressions, an expected target type, a conversion service for type conversion, and property accessors for evaluating expressions.

```java
	/**
	 * Constructor for SpringELExpression.
	 *
	 * @param expression a parsed Spring EL expression instance. Must not be null.
	 * @param expressionVars provides a mapping between variables names and
	 * parsed Spring EL expression instances.
	 * This parameter is optional (may be null).
	 * @param expectedType the target type expected from the evaluation of the expression or null.
	 * This parameter is optional (may be null).
	 * @param conversionService the Spring ConversionService instance to use for type conversion
	 * @param propertyAccessors propertyAccessors for Spring EL to use when evaluating expressions
	 */
	public SpringELExpression(org.springframework.expression.Expression expression,
			Map<String, Expression> expressionVars, Class<?> expectedType, ConversionService conversionService,
			List<PropertyAccessor> propertyAccessors) {

		this(expression, expectedType,
				new StandardEvaluationContextFactory(propertyAccessors, conversionService, expressionVars));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" line="69">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="73:3:3" line-data="	public SpringELExpression(org.springframework.expression.Expression expression, Class&lt;?&gt; expectedType,">`SpringELExpression`</SwmToken> constructor variant accepts an <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="70:19:19" line-data="	 * Generalized constructor variant that accepts an {@link EvaluationContextFactory}.">`EvaluationContextFactory`</SwmToken> to create evaluation contexts for the expression.

```java
	/**
	 * Generalized constructor variant that accepts an {@link EvaluationContextFactory}.
	 * @since 2.4.8
	 */
	public SpringELExpression(org.springframework.expression.Expression expression, Class<?> expectedType,
			EvaluationContextFactory contextFactory) {

		Assert.notNull(expression, "The SpelExpression is required for evaluation");
		Assert.notNull(contextFactory, "The EvaluationContextFactory is required");
		this.expression = expression;
		this.expectedType = expectedType;
		this.contextFactory = contextFactory;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" line="83">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="83:5:5" line-data="	public String getExpressionString() {">`getExpressionString`</SwmToken> function returns the string representation of the underlying Spring EL expression.

```java
	public String getExpressionString() {
		return expression.getExpressionString();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" line="87">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="88:5:5" line-data="	public Object getValue(Object rootObject) throws EvaluationException {">`getValue`</SwmToken> function evaluates the expression against a given root object and returns the result. It handles various exceptions that may occur during evaluation.

```java
	@SuppressWarnings("deprecation")
	public Object getValue(Object rootObject) throws EvaluationException {
		try {
			EvaluationContext context = contextFactory.createContext(rootObject);
			if (context instanceof StandardEvaluationContext) {
				extendEvaluationContext((StandardEvaluationContext) context);
			}
			return expression.getValue(context, expectedType);
		} catch (SpelEvaluationException e) {
			if (e.getMessageCode().equals(SpelMessage.PROPERTY_OR_FIELD_NOT_READABLE)) {
				throw new PropertyNotFoundException(rootObject.getClass(), getExpressionString(), e);
			}
			if (e.getMessageCode().equals(SpelMessage.TYPE_CONVERSION_ERROR)) {
				throw new ValueCoercionException(rootObject.getClass(), getExpressionString(), null, expectedType, e);
			}
			throw new EvaluationException(rootObject.getClass(), expression.getExpressionString(),
					"An ELException occurred getting the value for expression '" + getExpressionString()
							+ "' on context [" + rootObject.getClass() + "]", e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" line="108">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="109:6:6" line-data="	public Class&lt;?&gt; getValueType(Object rootObject) throws EvaluationException {">`getValueType`</SwmToken> function returns the type of the value that the expression evaluates to, given a root object.

```java
	@SuppressWarnings("deprecation")
	public Class<?> getValueType(Object rootObject) throws EvaluationException {
		try {
			EvaluationContext context = contextFactory.createContext(rootObject);
			if (context instanceof StandardEvaluationContext) {
				extendEvaluationContext((StandardEvaluationContext) context);
			}
			return expression.getValueType(context);
		} catch (SpelEvaluationException e) {
			if (e.getMessageCode().equals(SpelMessage.PROPERTY_OR_FIELD_NOT_READABLE)) {
				throw new PropertyNotFoundException(rootObject.getClass(), getExpressionString(), e);
			}
			throw new EvaluationException(rootObject.getClass(), getExpressionString(),
					"An ELException occurred getting the value type for expression '" + getExpressionString()
							+ "' on context [" + rootObject.getClass() + "]", e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" line="126">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="127:5:5" line-data="	public void setValue(Object rootObject, Object value) throws EvaluationException {">`setValue`</SwmToken> function sets the value of the expression on a given root object. It handles exceptions related to property write operations.

```java
	@SuppressWarnings("deprecation")
	public void setValue(Object rootObject, Object value) throws EvaluationException {
		try {
			EvaluationContext context = contextFactory.createContext(rootObject);
			if (context instanceof StandardEvaluationContext) {
				extendEvaluationContext((StandardEvaluationContext) context);
			}
			expression.setValue(context, value);
		} catch (SpelEvaluationException e) {
			if (e.getMessageCode().equals(SpelMessage.PROPERTY_OR_FIELD_NOT_WRITABLE)) {
				throw new PropertyNotFoundException(rootObject.getClass(), getExpressionString(), e);
			}
			if (e.getMessageCode().equals(SpelMessage.EXCEPTION_DURING_PROPERTY_WRITE)) {
				throw new ValueCoercionException(rootObject.getClass(), getExpressionString(), value, expectedType, e);
			}
			throw new EvaluationException(rootObject.getClass(), getExpressionString(),
					"An ELException occurred setting the value of expression '" + getExpressionString()
							+ "' on context [" + rootObject.getClass() + "] to [" + value + "]", e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" line="147">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="154:5:5" line-data="	protected void extendEvaluationContext(StandardEvaluationContext context) {">`extendEvaluationContext`</SwmToken> function is a deprecated method that allows further initialization of the evaluation context from subclasses.

```java
	/**
	 * Invoked every time an evaluation context is created allowing further
	 * initialization from sub-classes.
	 * @deprecated as of 2.4.8, to customize the context, please use the constructor
	 * that accepts an {@link EvaluationContextFactory}.
	 */
	@Deprecated
	protected void extendEvaluationContext(StandardEvaluationContext context) {
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" line="157">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="157:5:5" line-data="	public String toString() {">`toString`</SwmToken> function returns the string representation of the expression by calling <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpression.java" pos="158:3:3" line-data="		return getExpressionString();">`getExpressionString`</SwmToken>.

```java
	public String toString() {
		return getExpressionString();
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" line="84">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="45:4:4" line-data="public class SpringELExpressionParser implements ExpressionParser {">`SpringELExpressionParser`</SwmToken> class, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="87:3:3" line-data="				new SpringELExpression(spelExpression, expectedResultType, simpleContextFactory) :">`SpringELExpression`</SwmToken> is used to create expressions based on the provided context and expected result type. The method <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="88:1:1" line-data="				createSpringELExpression(expressionVars, spelExpression, expectedResultType, cs);">`createSpringELExpression`</SwmToken> is responsible for instantiating <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="87:3:3" line-data="				new SpringELExpression(spelExpression, expectedResultType, simpleContextFactory) :">`SpringELExpression`</SwmToken> with various parameters such as <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="87:5:5" line-data="				new SpringELExpression(spelExpression, expectedResultType, simpleContextFactory) :">`spelExpression`</SwmToken>, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="88:3:3" line-data="				createSpringELExpression(expressionVars, spelExpression, expectedResultType, cs);">`expressionVars`</SwmToken>, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="87:8:8" line-data="				new SpringELExpression(spelExpression, expectedResultType, simpleContextFactory) :">`expectedResultType`</SwmToken>, and <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="84:15:15" line-data="		org.springframework.core.convert.ConversionService cs = conversionService.getDelegateConversionService();">`conversionService`</SwmToken>.

```java
		org.springframework.core.convert.ConversionService cs = conversionService.getDelegateConversionService();

		return context instanceof SimpleParserContext ?
				new SpringELExpression(spelExpression, expectedResultType, simpleContextFactory) :
				createSpringELExpression(expressionVars, spelExpression, expectedResultType, cs);
	}

	/**
	 * Create the {@link SpringELExpression}.
	 * <p><strong>Note:</strong> as of 2.4.8, this method is not invoked when a
	 * {@link SimpleParserContext} is passed in, which is mainly the case when using
	 * SpEL for data binding. In those scenarios, the configuration options are
	 * limited to the use of property accessors and a ConversionService.
	 */
	protected SpringELExpression createSpringELExpression(Map<String, Expression> expressionVars,
			org.springframework.expression.Expression spelExpression, Class<?> expectedResultType,
			org.springframework.core.convert.ConversionService conversionService) {

		return new SpringELExpression(spelExpression, expressionVars,
				expectedResultType, conversionService, propertyAccessors);
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
