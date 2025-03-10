---
title: The BeanWrapperExpression class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="64:3:3" line-data="	public BeanWrapperExpression(String expression, ConversionService conversionService) {">`BeanWrapperExpression`</SwmToken> in detail. We will explain:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="64:3:3" line-data="	public BeanWrapperExpression(String expression, ConversionService conversionService) {">`BeanWrapperExpression`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="64:3:3" line-data="	public BeanWrapperExpression(String expression, ConversionService conversionService) {">`BeanWrapperExpression`</SwmToken>.

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="64:3:3" line-data="	public BeanWrapperExpression(String expression, ConversionService conversionService) {">`BeanWrapperExpression`</SwmToken>

<SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="64:3:3" line-data="	public BeanWrapperExpression(String expression, ConversionService conversionService) {">`BeanWrapperExpression`</SwmToken> is a class in <SwmPath>[spring-binding/…/beanwrapper/BeanWrapperExpression.java](spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java)</SwmPath>. It is used to evaluate or set a property of a context by delegating to a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="102:1:1" line-data="			BeanWrapperImpl beanWrapper = new BeanWrapperImpl(context);">`BeanWrapperImpl`</SwmToken> bean wrapper. This class supports the configuration of a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="64:10:10" line-data="	public BeanWrapperExpression(String expression, ConversionService conversionService) {">`ConversionService`</SwmToken> to allow <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="33:26:26" line-data=" * Also supports the configuration of a {@link ConversionService} to allow StringToObject type conversion to occur as">`StringToObject`</SwmToken> type conversion as part of setting a property. It mainly exists to take advantage of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="70:9:9" line-data="	 * Set whether this BeanWrapper should attempt to &quot;auto-grow&quot; a nested path that contains a null value.">`BeanWrapper`</SwmToken>'s unique property access features, such as inferring types of generic collections and maps and performing type coercion on collection elements when setting values.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" line="58">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="64:3:3" line-data="	public BeanWrapperExpression(String expression, ConversionService conversionService) {">`BeanWrapperExpression`</SwmToken> is a constructor that initializes the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="59:13:13" line-data="	 * Creates a new bean wrapper expression.">`expression`</SwmToken> and <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="61:6:6" line-data="	 * @param conversionService the conversion service containing converters to use as PropertyEditors for type">`conversionService`</SwmToken> variables.

```java
	/**
	 * Creates a new bean wrapper expression.
	 * @param expression the property expression string
	 * @param conversionService the conversion service containing converters to use as PropertyEditors for type
	 * conversion
	 */
	public BeanWrapperExpression(String expression, ConversionService conversionService) {
		this.expression = expression;
		this.conversionService = conversionService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" line="69">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="76:5:5" line-data="	public void setAutoGrowNestedPaths(boolean autoGrowNestedPaths) {">`setAutoGrowNestedPaths`</SwmToken> sets whether the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="70:9:9" line-data="	 * Set whether this BeanWrapper should attempt to &quot;auto-grow&quot; a nested path that contains a null value.">`BeanWrapper`</SwmToken> should attempt to <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="70:18:20" line-data="	 * Set whether this BeanWrapper should attempt to &quot;auto-grow&quot; a nested path that contains a null value.">`auto-grow`</SwmToken> a nested path that contains a null value.

```java
	/**
	 * Set whether this BeanWrapper should attempt to "auto-grow" a nested path that contains a null value.
	 * <p>If "true", a null path location will be populated with a default object value and traversed
	 * instead of resulting in a {@link NullValueInNestedPathException}. Turning this flag on also
	 * enables auto-growth of collection elements when accessing an out-of-bounds index.
	 * <p>Default is "false" on a plain BeanWrapper.
	 */
	public void setAutoGrowNestedPaths(boolean autoGrowNestedPaths) {
		this.autoGrowNestedPaths = autoGrowNestedPaths;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" line="80">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="84:5:5" line-data="	public void setAutoGrowCollectionLimit(int autoGrowCollectionLimit) {">`setAutoGrowCollectionLimit`</SwmToken> specifies a limit for array and collection <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="81:17:19" line-data="	 * Specify a limit for array and collection auto-growing.">`auto-growing`</SwmToken>.

```java
	/**
	 * Specify a limit for array and collection auto-growing.
	 * <p>Default is unlimited on a plain BeanWrapper.
	 */
	public void setAutoGrowCollectionLimit(int autoGrowCollectionLimit) {
		this.autoGrowCollectionLimit = autoGrowCollectionLimit;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" line="88">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="88:5:5" line-data="	public boolean equals(Object o) {">`equals`</SwmToken> checks if another object is equal to this <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="89:10:10" line-data="		if (!(o instanceof BeanWrapperExpression)) {">`BeanWrapperExpression`</SwmToken> instance.

```java
	public boolean equals(Object o) {
		if (!(o instanceof BeanWrapperExpression)) {
			return false;
		}
		BeanWrapperExpression other = (BeanWrapperExpression) o;
		return expression.equals(other.expression);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" line="96">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="96:5:5" line-data="	public int hashCode() {">`hashCode`</SwmToken> returns the hash code of the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="97:3:3" line-data="		return expression.hashCode();">`expression`</SwmToken>.

```java
	public int hashCode() {
		return expression.hashCode();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" line="100">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="100:5:5" line-data="	public Object getValue(Object context) throws EvaluationException {">`getValue`</SwmToken> retrieves the value of the property specified by the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="105:7:7" line-data="			return beanWrapper.getPropertyValue(expression);">`expression`</SwmToken> from the given context.

```java
	public Object getValue(Object context) throws EvaluationException {
		try {
			BeanWrapperImpl beanWrapper = new BeanWrapperImpl(context);
			beanWrapper.setAutoGrowNestedPaths(autoGrowNestedPaths);
			beanWrapper.setAutoGrowCollectionLimit(autoGrowCollectionLimit);
			return beanWrapper.getPropertyValue(expression);
		} catch (NotReadablePropertyException e) {
			throw new PropertyNotFoundException(context.getClass(), expression, e);
		} catch (BeansException e) {
			throw new EvaluationException(context.getClass(), getExpressionString(),
					"A BeansException occurred getting the value for expression '" + getExpressionString()
							+ "' on context [" + context.getClass() + "]", e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" line="115">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="115:5:5" line-data="	public void setValue(Object context, Object value) {">`setValue`</SwmToken> sets the value of the property specified by the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="121:5:5" line-data="			beanWrapper.setPropertyValue(expression, value);">`expression`</SwmToken> in the given context.

```java
	public void setValue(Object context, Object value) {
		try {
			BeanWrapperImpl beanWrapper = new BeanWrapperImpl(context);
			beanWrapper.setAutoGrowNestedPaths(autoGrowNestedPaths);
			beanWrapper.setAutoGrowCollectionLimit(autoGrowCollectionLimit);
			beanWrapper.setConversionService(conversionService.getDelegateConversionService());
			beanWrapper.setPropertyValue(expression, value);
		} catch (NotWritablePropertyException e) {
			throw new PropertyNotFoundException(context.getClass(), expression, e);
		} catch (TypeMismatchException e) {
			throw new ValueCoercionException(context.getClass(), expression, value, e.getRequiredType(), e);
		} catch (BeansException e) {
			throw new EvaluationException(context.getClass(), getExpressionString(),
					"A BeansException occurred setting the value of expression '" + getExpressionString()
							+ "' on context [" + context.getClass() + "] to [" + value + "]", e);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" line="133">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="133:6:6" line-data="	public Class&lt;?&gt; getValueType(Object context) {">`getValueType`</SwmToken> returns the type of the property specified by the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="136:7:7" line-data="			return beanWrapper.getPropertyType(expression);">`expression`</SwmToken> in the given context.

```java
	public Class<?> getValueType(Object context) {
		try {
			BeanWrapperImpl beanWrapper = new BeanWrapperImpl(context);
			return beanWrapper.getPropertyType(expression);
		} catch (NotReadablePropertyException e) {
			throw new PropertyNotFoundException(context.getClass(), expression, e);
		} catch (BeansException e) {
			throw new EvaluationException(context.getClass(), getExpressionString(),
					"An BeansException occurred getting the value type for expression '" + getExpressionString()
							+ "' on context [" + context.getClass() + "]", e);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" line="146">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="146:5:5" line-data="	public String getExpressionString() {">`getExpressionString`</SwmToken> returns the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="147:3:3" line-data="		return expression;">`expression`</SwmToken> string.

```java
	public String getExpressionString() {
		return expression;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" line="150">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="150:5:5" line-data="	public String toString() {">`toString`</SwmToken> returns the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpression.java" pos="151:3:3" line-data="		return expression;">`expression`</SwmToken> string.

```java
	public String toString() {
		return expression;
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" line="96">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="34:4:4" line-data="public class BeanWrapperExpressionParser extends AbstractExpressionParser {">`BeanWrapperExpressionParser`</SwmToken> class, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="97:1:1" line-data="		BeanWrapperExpression expression = new BeanWrapperExpression(expressionString, conversionService);">`BeanWrapperExpression`</SwmToken> is instantiated within the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="96:5:5" line-data="	protected Expression doParseExpression(String expressionString, ParserContext context) throws ParserException {">`doParseExpression`</SwmToken> method. This method takes an expression string and a parser context as parameters and returns an <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="96:3:3" line-data="	protected Expression doParseExpression(String expressionString, ParserContext context) throws ParserException {">`Expression`</SwmToken> object. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="97:1:1" line-data="		BeanWrapperExpression expression = new BeanWrapperExpression(expressionString, conversionService);">`BeanWrapperExpression`</SwmToken> is created using the provided expression string and a conversion service. Additionally, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="98:5:5" line-data="		expression.setAutoGrowNestedPaths(autoGrowNestedPaths);">`autoGrowNestedPaths`</SwmToken> and <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="99:5:5" line-data="		expression.setAutoGrowCollectionLimit(autoGrowCollectionLimit);">`autoGrowCollectionLimit`</SwmToken> properties are set on the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="97:1:1" line-data="		BeanWrapperExpression expression = new BeanWrapperExpression(expressionString, conversionService);">`BeanWrapperExpression`</SwmToken> instance before it is returned.

```java
	protected Expression doParseExpression(String expressionString, ParserContext context) throws ParserException {
		BeanWrapperExpression expression = new BeanWrapperExpression(expressionString, conversionService);
		expression.setAutoGrowNestedPaths(autoGrowNestedPaths);
		expression.setAutoGrowCollectionLimit(autoGrowCollectionLimit);
		return expression;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
