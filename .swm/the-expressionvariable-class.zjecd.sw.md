---
title: The ExpressionVariable class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="37:3:3" line-data="	public ExpressionVariable(String name, String valueExpression) {">`ExpressionVariable`</SwmToken> in the Spring Web Flow project. We will discuss:

1. What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="37:3:3" line-data="	public ExpressionVariable(String name, String valueExpression) {">`ExpressionVariable`</SwmToken>
2. Variables and functions in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="37:3:3" line-data="	public ExpressionVariable(String name, String valueExpression) {">`ExpressionVariable`</SwmToken>

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="37:3:3" line-data="	public ExpressionVariable(String name, String valueExpression) {">`ExpressionVariable`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="37:3:3" line-data="	public ExpressionVariable(String name, String valueExpression) {">`ExpressionVariable`</SwmToken> class in <SwmPath>[spring-binding/…/expression/ExpressionVariable.java](spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java)</SwmPath> is used to represent a variable that holds an expression. This class is primarily used to define variables that can be referenced by their names in other expressions. It provides a convenient way to alias complex expressions and manage them within a specific context.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" line="32">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="37:3:3" line-data="	public ExpressionVariable(String name, String valueExpression) {">`ExpressionVariable`</SwmToken> constructor initializes a new expression variable with a name and a value expression.

```java
	/**
	 * Creates a new expression variable.
	 * @param name the name of the variable, acting as an convenient alias (required)
	 * @param valueExpression the value expression (required)
	 */
	public ExpressionVariable(String name, String valueExpression) {
		init(name, valueExpression, null);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" line="41">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="47:3:3" line-data="	public ExpressionVariable(String name, String valueExpression, ParserContext parserContext) {">`ExpressionVariable`</SwmToken> constructor initializes a new expression variable with a name, a value expression, and a parser context.

```java
	/**
	 * Creates a new expression variable with a populated parser context.
	 * @param name the name of the variable, acting as an convenient alias (required)
	 * @param valueExpression the value expression (required)
	 * @param parserContext the parser context to use to parse the value expression (optional)
	 */
	public ExpressionVariable(String name, String valueExpression, ParserContext parserContext) {
		init(name, valueExpression, parserContext);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" line="51">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="55:5:5" line-data="	public String getName() {">`getName`</SwmToken> function returns the name of the variable.

```java
	/**
	 * Returns the variable name.
	 * @return the variable name
	 */
	public String getName() {
		return name;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" line="59">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="63:5:5" line-data="	public String getValueExpression() {">`getValueExpression`</SwmToken> function returns the expression that will be evaluated when the variable is referenced by its name in another expression.

```java
	/**
	 * Returns the expression that will be evaluated when the variable is referenced by its name in another expression.
	 * @return the expression value.
	 */
	public String getValueExpression() {
		return valueExpression;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" line="67">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="71:5:5" line-data="	public ParserContext getParserContext() {">`getParserContext`</SwmToken> function returns the parser context to use to parse the variable's value expression.

```java
	/**
	 * Returns the parser context to use to parse the variable's value expression.
	 * @return the value expression parser context
	 */
	public ParserContext getParserContext() {
		return parserContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" line="75">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="75:5:5" line-data="	public boolean equals(Object o) {">`equals`</SwmToken> function checks if another object is equal to this <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="76:10:10" line-data="		if (!(o instanceof ExpressionVariable)) {">`ExpressionVariable`</SwmToken> instance based on the variable name.

```java
	public boolean equals(Object o) {
		if (!(o instanceof ExpressionVariable)) {
			return false;
		}
		ExpressionVariable var = (ExpressionVariable) o;
		return name.equals(var.name);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" line="83">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="83:5:5" line-data="	public int hashCode() {">`hashCode`</SwmToken> function returns the hash code of the variable name.

```java
	public int hashCode() {
		return name.hashCode();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" line="87">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="87:5:5" line-data="	public String toString() {">`toString`</SwmToken> function returns a string representation of the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="37:3:3" line-data="	public ExpressionVariable(String name, String valueExpression) {">`ExpressionVariable`</SwmToken> instance.

```java
	public String toString() {
		return "[Expression Variable '" + name + "']";
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" line="91">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="91:5:5" line-data="	private void init(String name, String valueExpression, ParserContext parserContext) {">`init`</SwmToken> function initializes the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="37:3:3" line-data="	public ExpressionVariable(String name, String valueExpression) {">`ExpressionVariable`</SwmToken> instance with the provided name, value expression, and parser context.

```java
	private void init(String name, String valueExpression, ParserContext parserContext) {
		Assert.hasText(name, "The expression variable must be named");
		Assert.hasText(valueExpression, "The expression variable's value expression is required");
		this.name = name;
		this.valueExpression = valueExpression;
		this.parserContext = parserContext;
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/FluentParserContext.java" line="35">

---

In <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/FluentParserContext.java" pos="29:4:4" line-data="public class FluentParserContext implements ParserContext {">`FluentParserContext`</SwmToken>, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/FluentParserContext.java" pos="35:5:5" line-data="	private List&lt;ExpressionVariable&gt; expressionVariables;">`ExpressionVariable`</SwmToken> is used to store a list of expression variables that can be referenced during expression evaluation. The method <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/FluentParserContext.java" pos="59:7:7" line-data="	public ExpressionVariable[] getExpressionVariables() {">`getExpressionVariables`</SwmToken> returns these variables as an array.

```java
	private List<ExpressionVariable> expressionVariables;

```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/FluentParserContext.java" line="59">

---

&nbsp;

```java
	public ExpressionVariable[] getExpressionVariables() {
		return expressionVariables.toArray(new ExpressionVariable[expressionVariables.size()]);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/NullParserContext.java" line="44">

---

In <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="177:3:3" line-data="							: NullParserContext.INSTANCE;">`NullParserContext`</SwmToken>, the method <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/NullParserContext.java" pos="44:7:7" line-data="	public ExpressionVariable[] getExpressionVariables() {">`getExpressionVariables`</SwmToken> returns null, indicating that no expression variables are available in this context.

```java
	public ExpressionVariable[] getExpressionVariables() {
		return null;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/SimpleParserContext.java" line="50">

---

Similarly, in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/SimpleParserContext.java" pos="32:6:6" line-data="public final class SimpleParserContext implements ParserContext {">`SimpleParserContext`</SwmToken>, the method <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/SimpleParserContext.java" pos="50:7:7" line-data="	public ExpressionVariable[] getExpressionVariables() {">`getExpressionVariables`</SwmToken> also returns null, indicating the absence of expression variables.

```java
	public ExpressionVariable[] getExpressionVariables() {
		return null;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="226">

---

In <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="36:6:6" line-data="public abstract class AbstractExpressionParser implements ExpressionParser {">`AbstractExpressionParser`</SwmToken>, the method <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="226:11:11" line-data="	protected Map&lt;String, Expression&gt; parseVariableExpressions(ExpressionVariable[] variables) throws ParserException {">`parseVariableExpressions`</SwmToken> takes an array of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="226:13:13" line-data="	protected Map&lt;String, Expression&gt; parseVariableExpressions(ExpressionVariable[] variables) throws ParserException {">`ExpressionVariable`</SwmToken> and parses them into a map of variable names and their corresponding expressions.

```java
	protected Map<String, Expression> parseVariableExpressions(ExpressionVariable[] variables) throws ParserException {
		if (variables == null || variables.length == 0) {
			return null;
		}
		Map<String, Expression> variableExpressions = new HashMap<>(variables.length, 1);
		for (ExpressionVariable var : variables) {
			variableExpressions.put(var.getName(), parseExpression(var.getValueExpression(), var.getParserContext()));
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ParserContext.java" line="42">

---

In <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="47:15:15" line-data="	public ExpressionVariable(String name, String valueExpression, ParserContext parserContext) {">`ParserContext`</SwmToken>, the method <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ParserContext.java" pos="42:5:5" line-data="	ExpressionVariable[] getExpressionVariables();">`getExpressionVariables`</SwmToken> is defined to return an array of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ParserContext.java" pos="42:1:1" line-data="	ExpressionVariable[] getExpressionVariables();">`ExpressionVariable`</SwmToken>, which can be referenced during expression evaluation.

```java
	ExpressionVariable[] getExpressionVariables();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" line="126">

---

In <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="45:4:4" line-data="public class SpringELExpressionParser implements ExpressionParser {">`SpringELExpressionParser`</SwmToken>, the method <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="126:11:11" line-data="	private Map&lt;String, Expression&gt; parseSpelExpressionVariables(ExpressionVariable[] expressionVars) {">`parseSpelExpressionVariables`</SwmToken> converts an array of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="126:13:13" line-data="	private Map&lt;String, Expression&gt; parseSpelExpressionVariables(ExpressionVariable[] expressionVars) {">`ExpressionVariable`</SwmToken> into a map of variable names and parsed Spring EL expressions.

```java
	private Map<String, Expression> parseSpelExpressionVariables(ExpressionVariable[] expressionVars) {
		if (expressionVars == null || expressionVars.length == 0) {
			return null;
		}
		Map<String, Expression> result = new HashMap<>(expressionVars.length);
		for (ExpressionVariable var : expressionVars) {
			result.put(var.getName(), parseExpression(var.getValueExpression(), var.getParserContext()));
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" line="172">

---

In <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="45:4:4" line-data="public class ELExpressionParser implements ExpressionParser {">`ELExpressionParser`</SwmToken>, the method <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="172:5:5" line-data="		public void mapVariables(ExpressionVariable[] variables, ExpressionFactory expressionFactory) {">`mapVariables`</SwmToken> maps an array of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="172:7:7" line-data="		public void mapVariables(ExpressionVariable[] variables, ExpressionFactory expressionFactory) {">`ExpressionVariable`</SwmToken> to a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/el/ELExpressionParser.java" pos="174:7:7" line-data="				variableMapper = new VariableMapperImpl();">`VariableMapperImpl`</SwmToken> for use in expression evaluation.

```java
		public void mapVariables(ExpressionVariable[] variables, ExpressionFactory expressionFactory) {
			if (variables != null && variables.length > 0) {
				variableMapper = new VariableMapperImpl();
				for (ExpressionVariable var : variables) {
					ParserContext context = var.getParserContext() != null ? var.getParserContext()
							: NullParserContext.INSTANCE;
					ValueExpression expr;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
