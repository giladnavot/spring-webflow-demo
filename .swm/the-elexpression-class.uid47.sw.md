---
title: The ELExpression class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="44:3:3" line-data="	public ELExpression(ELContextFactory factory, ValueExpression valueExpression) {">`ELExpression`</SwmToken> in the Spring Web Flow project. We will cover:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="44:3:3" line-data="	public ELExpression(ELContextFactory factory, ValueExpression valueExpression) {">`ELExpression`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="44:3:3" line-data="	public ELExpression(ELContextFactory factory, ValueExpression valueExpression) {">`ELExpression`</SwmToken>.

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="44:3:3" line-data="	public ELExpression(ELContextFactory factory, ValueExpression valueExpression) {">`ELExpression`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="44:3:3" line-data="	public ELExpression(ELContextFactory factory, ValueExpression valueExpression) {">`ELExpression`</SwmToken> class in <SwmPath>[spring-binding/…/el/ELExpression.java](spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java)</SwmPath> is used to evaluate parsed EL (Expression Language) expressions. It leverages the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="35:3:3" line-data="	private ELContextFactory elContextFactory;">`ELContextFactory`</SwmToken> to create the necessary EL context for expression evaluation and uses <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="37:3:3" line-data="	private ValueExpression valueExpression;">`ValueExpression`</SwmToken> to perform the actual evaluation.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="35">

---

The variable <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="35:5:5" line-data="	private ELContextFactory elContextFactory;">`elContextFactory`</SwmToken> is used to store the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="35:3:3" line-data="	private ELContextFactory elContextFactory;">`ELContextFactory`</SwmToken> instance, which is responsible for creating the EL context used during expression evaluation.

```java
	private ELContextFactory elContextFactory;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="37">

---

The variable <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="37:5:5" line-data="	private ValueExpression valueExpression;">`valueExpression`</SwmToken> is used to store the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="37:3:3" line-data="	private ValueExpression valueExpression;">`ValueExpression`</SwmToken> instance, which represents the parsed EL expression to be evaluated.

```java
	private ValueExpression valueExpression;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="44">

---

The constructor <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="44:3:3" line-data="	public ELExpression(ELContextFactory factory, ValueExpression valueExpression) {">`ELExpression`</SwmToken> initializes the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="47:3:3" line-data="		this.elContextFactory = factory;">`elContextFactory`</SwmToken> and <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="44:12:12" line-data="	public ELExpression(ELContextFactory factory, ValueExpression valueExpression) {">`valueExpression`</SwmToken> variables. It ensures that both parameters are not null before assigning them.

```java
	public ELExpression(ELContextFactory factory, ValueExpression valueExpression) {
		Assert.notNull(factory, "The ELContextFactory is required to evaluate EL expressions");
		Assert.notNull(valueExpression, "The EL ValueExpression is required for evaluation");
		this.elContextFactory = factory;
		this.valueExpression = valueExpression;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="51">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="51:5:5" line-data="	public Object getValue(Object context) throws EvaluationException {">`getValue`</SwmToken> evaluates the EL expression against the provided context and returns the result. If the expression does not resolve, it throws an <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="51:14:14" line-data="	public Object getValue(Object context) throws EvaluationException {">`EvaluationException`</SwmToken>.

```java
	public Object getValue(Object context) throws EvaluationException {
		ELContext ctx = elContextFactory.getELContext(context);
		try {
			Object result = valueExpression.getValue(ctx);
			if (result == null && !ctx.isPropertyResolved()) {
				if (getExpressionString().equals("null")) {
					// special case for handling reserved null keyword
					return null;
				} else {
					throw new EvaluationException(context.getClass(), getExpressionString(), "The expression '"
							+ getExpressionString() + "' did not resolve... is the base variable '" + getBaseVariable()
							+ "' spelled correctly?");
				}
			}
			return result;
		} catch (jakarta.el.PropertyNotFoundException e) {
			throw new PropertyNotFoundException(context.getClass(), getExpressionString(), e);
		} catch (ELException e) {
			throw new EvaluationException(context.getClass(), getExpressionString(),
					"An ELException occurred getting the value for expression '" + getExpressionString()
							+ "' on context [" + context.getClass() + "]", e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="75">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="75:5:5" line-data="	public void setValue(Object context, Object value) throws EvaluationException {">`setValue`</SwmToken> sets the value of the EL expression in the provided context. If the expression does not resolve, it throws an <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="75:19:19" line-data="	public void setValue(Object context, Object value) throws EvaluationException {">`EvaluationException`</SwmToken>.

```java
	public void setValue(Object context, Object value) throws EvaluationException {
		ELContext ctx = elContextFactory.getELContext(context);
		try {
			valueExpression.setValue(ctx, value);
			if (!ctx.isPropertyResolved()) {
				throw new EvaluationException(context.getClass(), getExpressionString(), "The expression '"
						+ getExpressionString() + "' did not resolve... is the base variable ''" + getBaseVariable()
						+ "' spelled correctly?");
			}
		} catch (jakarta.el.PropertyNotFoundException e) {
			throw new PropertyNotFoundException(context.getClass(), getExpressionString(), e);
		} catch (ELException e) {
			throw new EvaluationException(context.getClass(), getExpressionString(),
					"An ELException occurred setting the value of expression '" + getExpressionString()
							+ "' on context [" + context.getClass() + "] to [" + value + "]", e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="93">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="93:6:6" line-data="	public Class&lt;?&gt; getValueType(Object context) {">`getValueType`</SwmToken> returns the type of the value that the EL expression evaluates to in the provided context.

```java
	public Class<?> getValueType(Object context) {
		ELContext ctx = elContextFactory.getELContext(context);
		try {
			return valueExpression.getType(ctx);
		} catch (jakarta.el.PropertyNotFoundException e) {
			throw new PropertyNotFoundException(context.getClass(), getExpressionString(), e);
		} catch (ELException e) {
			throw new EvaluationException(context.getClass(), getExpressionString(),
					"An ELException occurred getting the value type for expression '" + getExpressionString()
							+ "' on context [" + context.getClass() + "]", e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="106">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="106:5:5" line-data="	public String getExpressionString() {">`getExpressionString`</SwmToken> returns the original EL expression string.

```java
	public String getExpressionString() {
		return valueExpression.getExpressionString();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="110">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="110:5:5" line-data="	private String getBaseVariable() {">`getBaseVariable`</SwmToken> extracts and returns the base variable from the EL expression string.

```java
	private String getBaseVariable() {
		String expressionString = getExpressionString();
		int firstDot = expressionString.indexOf('.');
		if (firstDot == -1) {
			return expressionString;
		} else {
			return expressionString.substring(0, firstDot);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="120">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="120:5:5" line-data="	public int hashCode() {">`hashCode`</SwmToken> returns the hash code of the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="121:3:3" line-data="		return valueExpression.hashCode();">`valueExpression`</SwmToken>.

```java
	public int hashCode() {
		return valueExpression.hashCode();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="124">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="124:5:5" line-data="	public boolean equals(Object o) {">`equals`</SwmToken> checks if another object is equal to this <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="125:10:10" line-data="		if (!(o instanceof ELExpression)) {">`ELExpression`</SwmToken> instance by comparing their <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="129:3:3" line-data="		return valueExpression.equals(other.valueExpression);">`valueExpression`</SwmToken> fields.

```java
	public boolean equals(Object o) {
		if (!(o instanceof ELExpression)) {
			return false;
		}
		ELExpression other = (ELExpression) o;
		return valueExpression.equals(other.valueExpression);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" line="132">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="132:5:5" line-data="	public String toString() {">`toString`</SwmToken> returns the string representation of the EL expression by calling <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpression.java" pos="133:3:3" line-data="		return getExpressionString();">`getExpressionString`</SwmToken>.

```java
	public String toString() {
		return getExpressionString();
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="104">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="45:4:4" line-data="public class ELExpressionParser implements ExpressionParser {">`ELExpressionParser`</SwmToken> class, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="107:5:5" line-data="			return new ELExpression(contextFactory, expression);">`ELExpression`</SwmToken> is instantiated within a try-catch block. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="105:7:7" line-data="			ValueExpression expression = parseValueExpression(expressionString, context);">`parseValueExpression`</SwmToken> method is called to parse the expression string and create a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="105:1:1" line-data="			ValueExpression expression = parseValueExpression(expressionString, context);">`ValueExpression`</SwmToken> object. Then, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="106:7:7" line-data="			ELContextFactory contextFactory = getContextFactory(context.getEvaluationContextType(), expressionString);">`getContextFactory`</SwmToken> method is used to obtain an <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="106:1:1" line-data="			ELContextFactory contextFactory = getContextFactory(context.getEvaluationContextType(), expressionString);">`ELContextFactory`</SwmToken> based on the evaluation context type and expression string. Finally, a new <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="107:5:5" line-data="			return new ELExpression(contextFactory, expression);">`ELExpression`</SwmToken> object is created using the context factory and the parsed value expression.

```java
		try {
			ValueExpression expression = parseValueExpression(expressionString, context);
			ELContextFactory contextFactory = getContextFactory(context.getEvaluationContextType(), expressionString);
			return new ELExpression(contextFactory, expression);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
