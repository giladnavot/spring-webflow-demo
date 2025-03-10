---
title: The ELExpressionParser class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="56:3:3" line-data="	public ELExpressionParser(ExpressionFactory expressionFactory) {">`ELExpressionParser`</SwmToken> in detail. We will cover:

1. What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="56:3:3" line-data="	public ELExpressionParser(ExpressionFactory expressionFactory) {">`ELExpressionParser`</SwmToken>
2. Variables and functions in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="56:3:3" line-data="	public ELExpressionParser(ExpressionFactory expressionFactory) {">`ELExpressionParser`</SwmToken>

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="56:3:3" line-data="	public ELExpressionParser(ExpressionFactory expressionFactory) {">`ELExpressionParser`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="56:3:3" line-data="	public ELExpressionParser(ExpressionFactory expressionFactory) {">`ELExpressionParser`</SwmToken> class is an expression parser that parses EL (Expression Language) expressions. It is used to evaluate and parse expressions within the Spring Web Flow framework. This class provides the necessary functionality to handle EL expressions, including type conversions and context management.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="56">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="56:3:3" line-data="	public ELExpressionParser(ExpressionFactory expressionFactory) {">`ELExpressionParser`</SwmToken> constructor initializes the parser with a given <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="56:5:5" line-data="	public ELExpressionParser(ExpressionFactory expressionFactory) {">`ExpressionFactory`</SwmToken> and sets up the necessary context factories.

```java
	public ELExpressionParser(ExpressionFactory expressionFactory) {
		init(expressionFactory);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="64">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="64:5:5" line-data="	public ConversionService getConversionService() {">`getConversionService`</SwmToken> returns the conversion service used to perform type conversions as needed by the Unified EL system.

```java
	public ConversionService getConversionService() {
		return conversionService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="72">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="72:5:5" line-data="	public void setConversionService(ConversionService conversionService) {">`setConversionService`</SwmToken> sets the conversion service to use for type conversions.

```java
	public void setConversionService(ConversionService conversionService) {
		Assert.notNull(conversionService, "The conversion service is required");
		this.conversionService = conversionService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="82">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="82:5:5" line-data="	public void putContextFactory(Class&lt;?&gt; contextType, ELContextFactory contextFactory) {">`putContextFactory`</SwmToken> registers the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="82:13:13" line-data="	public void putContextFactory(Class&lt;?&gt; contextType, ELContextFactory contextFactory) {">`ELContextFactory`</SwmToken> for expressions that evaluate the given class of context object.

```java
	public void putContextFactory(Class<?> contextType, ELContextFactory contextFactory) {
		Assert.notNull(contextFactory, "The EL context factory cannot be null");
		contextFactories.put(contextType, contextFactory);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="87">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="87:5:5" line-data="	public Expression parseExpression(String expressionString, ParserContext context) throws ParserException {">`parseExpression`</SwmToken> parses the given expression string within the provided parser context.

```java
	public Expression parseExpression(String expressionString, ParserContext context) throws ParserException {
		Assert.notNull(expressionString, "The expression string to parse is required");
		if (context == null) {
			context = NullParserContext.INSTANCE;
		}
		if (context.isTemplate()) {
			return parseExpressionInternal(expressionString, context, true);
		} else {
			assertNotDelimited(expressionString);
			assertHasText(expressionString);
			return parseExpressionInternal("#{" + expressionString + "}", context, false);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="101">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="101:5:5" line-data="	private Expression parseExpressionInternal(String expressionString, ParserContext context, boolean template)">`parseExpressionInternal`</SwmToken> is a private method that handles the internal parsing logic for expressions.

```java
	private Expression parseExpressionInternal(String expressionString, ParserContext context, boolean template)
			throws ParserException {
		Assert.notNull(expressionString, "The expression string to parse is required");
		try {
			ValueExpression expression = parseValueExpression(expressionString, context);
			ELContextFactory contextFactory = getContextFactory(context.getEvaluationContextType(), expressionString);
			return new ELExpression(contextFactory, expression);
		} catch (ELException e) {
			throw new ParserException(expressionString, e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="113">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="113:5:5" line-data="	private ValueExpression parseValueExpression(String expressionString, ParserContext context) throws ELException {">`parseValueExpression`</SwmToken> parses the given expression string into a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="113:3:3" line-data="	private ValueExpression parseValueExpression(String expressionString, ParserContext context) throws ELException {">`ValueExpression`</SwmToken>.

```java
	private ValueExpression parseValueExpression(String expressionString, ParserContext context) throws ELException {
		ParserELContext elContext = new ParserELContext();
		elContext.mapVariables(context.getExpressionVariables(), expressionFactory);
		ValueExpression expression = expressionFactory.createValueExpression(elContext, expressionString, Object.class);
		return new BindingValueExpression(expression, getExpectedType(context), conversionService, context.isTemplate());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="120">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="120:6:6" line-data="	private Class&lt;?&gt; getExpectedType(ParserContext context) {">`getExpectedType`</SwmToken> returns the expected evaluation result type from the parser context.

```java
	private Class<?> getExpectedType(ParserContext context) {
		Class<?> expectedType = context.getExpectedEvaluationResultType();
		return expectedType != null ? expectedType : Object.class;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="125">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="125:5:5" line-data="	private ELContextFactory getContextFactory(Class&lt;?&gt; expressionTargetType, String expressionString) {">`getContextFactory`</SwmToken> retrieves the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="125:3:3" line-data="	private ELContextFactory getContextFactory(Class&lt;?&gt; expressionTargetType, String expressionString) {">`ELContextFactory`</SwmToken> for the given expression target type.

```java
	private ELContextFactory getContextFactory(Class<?> expressionTargetType, String expressionString) {
		if (contextFactories.containsKey(expressionTargetType)) {
			return contextFactories.get(expressionTargetType);
		} else {
			return contextFactories.get(Object.class);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="133">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="133:5:5" line-data="	private void init(ExpressionFactory expressionFactory) {">`init`</SwmToken> initializes the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="56:3:3" line-data="	public ELExpressionParser(ExpressionFactory expressionFactory) {">`ELExpressionParser`</SwmToken> with the provided <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="133:7:7" line-data="	private void init(ExpressionFactory expressionFactory) {">`ExpressionFactory`</SwmToken>.

```java
	private void init(ExpressionFactory expressionFactory) {
		this.expressionFactory = expressionFactory;
		DefaultElContextFactory contextFactory = new DefaultElContextFactory();
		putContextFactory(null, contextFactory);
		putContextFactory(Object.class, contextFactory);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="140">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="140:5:5" line-data="	private void assertNotDelimited(String expressionString) {">`assertNotDelimited`</SwmToken> checks if the expression string is not enclosed in delimiters and throws a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="143:5:5" line-data="			throw new ParserException(expressionString, &quot;This expression &#39;&quot; + expressionString">`ParserException`</SwmToken> if it is.

```java
	private void assertNotDelimited(String expressionString) {
		if ((expressionString.startsWith("#{") && expressionString.endsWith("}"))
				|| (expressionString.startsWith("${") && expressionString.endsWith("}"))) {
			throw new ParserException(expressionString, "This expression '" + expressionString
					+ "' being parsed is expected be an 'eval' EL expression string. "
					+ "Do not attempt to enclose such expression strings in #{} or ${} delimiters. "
					+ "If you need to parse a template that mixes literal text with evaluatable blocks, "
					+ "set the 'template' parser context attribute to true.", null);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="151">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="151:5:5" line-data="	private void assertHasText(String expressionString) {">`assertHasText`</SwmToken> checks if the expression string has text and throws a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="153:5:5" line-data="			throw new ParserException(expressionString, &quot;The EL eval expression to parse must have text&quot;, null);">`ParserException`</SwmToken> if it is empty.

```java
	private void assertHasText(String expressionString) {
		if (expressionString.length() == 0) {
			throw new ParserException(expressionString, "The EL eval expression to parse must have text", null);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="160">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="160:5:5" line-data="		public ELResolver getELResolver() {">`getELResolver`</SwmToken> returns <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="161:3:3" line-data="			return null;">`null`</SwmToken> as it is not implemented in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="114:1:1" line-data="		ParserELContext elContext = new ParserELContext();">`ParserELContext`</SwmToken> class.

```java
		public ELResolver getELResolver() {
			return null;
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="164">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="164:5:5" line-data="		public FunctionMapper getFunctionMapper() {">`getFunctionMapper`</SwmToken> returns <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="165:3:3" line-data="			return null;">`null`</SwmToken> as it is not implemented in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="114:1:1" line-data="		ParserELContext elContext = new ParserELContext();">`ParserELContext`</SwmToken> class.

```java
		public FunctionMapper getFunctionMapper() {
			return null;
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="168">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="168:5:5" line-data="		public VariableMapper getVariableMapper() {">`getVariableMapper`</SwmToken> returns the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="168:3:3" line-data="		public VariableMapper getVariableMapper() {">`VariableMapper`</SwmToken> instance in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="114:1:1" line-data="		ParserELContext elContext = new ParserELContext();">`ParserELContext`</SwmToken> class.

```java
		public VariableMapper getVariableMapper() {
			return variableMapper;
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="172">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="172:5:5" line-data="		public void mapVariables(ExpressionVariable[] variables, ExpressionFactory expressionFactory) {">`mapVariables`</SwmToken> maps the provided expression variables to the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="168:3:3" line-data="		public VariableMapper getVariableMapper() {">`VariableMapper`</SwmToken> in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="114:1:1" line-data="		ParserELContext elContext = new ParserELContext();">`ParserELContext`</SwmToken> class.

```java
		public void mapVariables(ExpressionVariable[] variables, ExpressionFactory expressionFactory) {
			if (variables != null && variables.length > 0) {
				variableMapper = new VariableMapperImpl();
				for (ExpressionVariable var : variables) {
					ParserContext context = var.getParserContext() != null ? var.getParserContext()
							: NullParserContext.INSTANCE;
					ValueExpression expr;
					if (context.isTemplate()) {
						expr = parseValueExpression(var.getValueExpression(), context);
					} else {
						assertNotDelimited(var.getValueExpression());
						assertHasText(var.getValueExpression());
						expr = parseValueExpression("#{" + var.getValueExpression() + "}", context);
					}
					variableMapper.setVariable(var.getName(), expr);
				}
			}
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="195">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="195:5:5" line-data="		public ValueExpression resolveVariable(String name) {">`resolveVariable`</SwmToken> resolves the variable with the given name in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="174:7:7" line-data="				variableMapper = new VariableMapperImpl();">`VariableMapperImpl`</SwmToken> class.

```java
		public ValueExpression resolveVariable(String name) {
			return variables.get(name);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="199">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="199:5:5" line-data="		public ValueExpression setVariable(String name, ValueExpression value) {">`setVariable`</SwmToken> sets the variable with the given name and value in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="174:7:7" line-data="				variableMapper = new VariableMapperImpl();">`VariableMapperImpl`</SwmToken> class.

```java
		public ValueExpression setVariable(String name, ValueExpression value) {
			return variables.put(name, value);
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="203">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="203:5:5" line-data="		public String toString() {">`toString`</SwmToken> returns the string representation of the variables in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="174:7:7" line-data="				variableMapper = new VariableMapperImpl();">`VariableMapperImpl`</SwmToken> class.

```java
		public String toString() {
			return variables.toString();
		}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-faces/src/main/java/org/springframework/faces/webflow/JsfManagedBeanAwareELExpressionParser.java" line="44">

---

The <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/JsfManagedBeanAwareELExpressionParser.java" pos="44:4:4" line-data="public class JsfManagedBeanAwareELExpressionParser extends ELExpressionParser {">`JsfManagedBeanAwareELExpressionParser`</SwmToken> class extends <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/JsfManagedBeanAwareELExpressionParser.java" pos="44:8:8" line-data="public class JsfManagedBeanAwareELExpressionParser extends ELExpressionParser {">`ELExpressionParser`</SwmToken> and is used to create an expression parser that is aware of JSF managed beans. This class is instantiated with an <SwmToken path="spring-faces/src/main/java/org/springframework/faces/webflow/JsfManagedBeanAwareELExpressionParser.java" pos="46:5:5" line-data="	public JsfManagedBeanAwareELExpressionParser(ExpressionFactory expressionFactory) {">`ExpressionFactory`</SwmToken> to handle the creation of expressions.

```java
public class JsfManagedBeanAwareELExpressionParser extends ELExpressionParser {

	public JsfManagedBeanAwareELExpressionParser(ExpressionFactory expressionFactory) {
		super(expressionFactory);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/expression/el/WebFlowELExpressionParser.java" line="37">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/expression/el/WebFlowELExpressionParser.java" pos="37:4:4" line-data="public class WebFlowELExpressionParser extends ELExpressionParser {">`WebFlowELExpressionParser`</SwmToken> class also extends <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/expression/el/WebFlowELExpressionParser.java" pos="37:8:8" line-data="public class WebFlowELExpressionParser extends ELExpressionParser {">`ELExpressionParser`</SwmToken> and is specifically designed for use within Spring Web Flow. It provides a specialized implementation for parsing expressions in the context of web flows.

```java
public class WebFlowELExpressionParser extends ELExpressionParser {

	/**
	 * Creates a new Web Flow EL expression parser.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
