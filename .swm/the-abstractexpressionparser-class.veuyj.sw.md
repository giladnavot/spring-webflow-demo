---
title: The AbstractExpressionParser class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="27:12:12" line-data="import org.springframework.binding.expression.support.AbstractExpressionParser;">`AbstractExpressionParser`</SwmToken> in detail. We will discuss:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="27:12:12" line-data="import org.springframework.binding.expression.support.AbstractExpressionParser;">`AbstractExpressionParser`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="27:12:12" line-data="import org.springframework.binding.expression.support.AbstractExpressionParser;">`AbstractExpressionParser`</SwmToken>.

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="27:12:12" line-data="import org.springframework.binding.expression.support.AbstractExpressionParser;">`AbstractExpressionParser`</SwmToken>

<SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="27:12:12" line-data="import org.springframework.binding.expression.support.AbstractExpressionParser;">`AbstractExpressionParser`</SwmToken> is an abstract base class for parsing expressions in the format `${...}`. It is used to handle the parsing logic for expressions that are enclosed within specific delimiters, such as `${}`. This class provides a foundation for creating custom expression parsers by implementing the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="24:10:10" line-data="import org.springframework.binding.expression.ExpressionParser;">`ExpressionParser`</SwmToken> interface.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="68">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="68:5:5" line-data="	public String getExpressionPrefix() {">`getExpressionPrefix`</SwmToken> returns the configured expression delimiter prefix. By default, it returns `${`.

```java
	public String getExpressionPrefix() {
		return expressionPrefix;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="75">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="75:5:5" line-data="	public void setExpressionPrefix(String expressionPrefix) {">`setExpressionPrefix`</SwmToken> sets the expression delimiter prefix.

```java
	public void setExpressionPrefix(String expressionPrefix) {
		this.expressionPrefix = expressionPrefix;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="82">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="82:5:5" line-data="	public String getExpressionSuffix() {">`getExpressionSuffix`</SwmToken> returns the configured expression delimiter suffix. By default, it returns `}`.

```java
	public String getExpressionSuffix() {
		return expressionSuffix;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="89">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="89:5:5" line-data="	public void setExpressionSuffix(String expressionSuffix) {">`setExpressionSuffix`</SwmToken> sets the expression delimiter suffix.

```java
	public void setExpressionSuffix(String expressionSuffix) {
		this.expressionSuffix = expressionSuffix;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="96">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="96:5:5" line-data="	public boolean getAllowDelimitedEvalExpressions() {">`getAllowDelimitedEvalExpressions`</SwmToken> returns whether the parser allows delimited eval expressions like <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="59:18:23" line-data="	 * Should we allow delimited eval expressions like &quot;${foo.bar}&quot;? If not, evalutable expressions must not be enclosed">`${foo.bar}`</SwmToken>.

```java
	public boolean getAllowDelimitedEvalExpressions() {
		return allowDelimitedEvalExpressions;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="103">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="103:5:5" line-data="	public void setAllowDelimitedEvalExpressions(boolean allowDelmitedEvalExpressions) {">`setAllowDelimitedEvalExpressions`</SwmToken> sets whether the parser allows eval expressions like <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="59:18:23" line-data="	 * Should we allow delimited eval expressions like &quot;${foo.bar}&quot;? If not, evalutable expressions must not be enclosed">`${foo.bar}`</SwmToken>.

```java
	public void setAllowDelimitedEvalExpressions(boolean allowDelmitedEvalExpressions) {
		this.allowDelimitedEvalExpressions = allowDelmitedEvalExpressions;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="109">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="109:5:5" line-data="	public Expression parseExpression(String expressionString, ParserContext context) throws ParserException {">`parseExpression`</SwmToken> parses a given expression string based on the provided <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="109:12:12" line-data="	public Expression parseExpression(String expressionString, ParserContext context) throws ParserException {">`ParserContext`</SwmToken>. It handles both template and non-template expressions.

```java
	public Expression parseExpression(String expressionString, ParserContext context) throws ParserException {
		Assert.notNull(expressionString, "The expression string to parse is required");
		if (context == null) {
			context = NullParserContext.INSTANCE;
		}
		if (context.isTemplate()) {
			return parseTemplate(expressionString, context);
		} else {
			if (expressionString.startsWith(getExpressionPrefix()) && expressionString.endsWith(getExpressionSuffix())) {
				if (!allowDelimitedEvalExpressions) {
					throw new ParserException(
							expressionString,
							"The expression '" + expressionString + "' being parsed is expected be an expression. " +
									"Do not enclose such expression strings in ${} delimiters as it's redundant. " +
									"If you need to parse a template that mixes literal text with evaluatable blocks, " +
									"set the 'template' parser context attribute to true.",
							null);
				} else {
					int lastIndex = expressionString.length() - getExpressionSuffix().length();
					String expression = expressionString.substring(getExpressionPrefix().length(), lastIndex);
					return doParseExpression(expression, context);
				}
			} else {
				return doParseExpression(expressionString, context);
			}
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="137">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="137:5:5" line-data="	private Expression parseTemplate(String expressionString, ParserContext context) throws ParserException {">`parseTemplate`</SwmToken> parses a template expression string, which may contain multiple expressions.

```java
	private Expression parseTemplate(String expressionString, ParserContext context) throws ParserException {
		Assert.notNull(expressionString, "The expression string to parse is required");
		if (expressionString.length() == 0) {
			return parseEmptyExpressionString(context);
		}
		Expression[] expressions = parseExpressions(expressionString, context);
		if (expressions.length == 1) {
			return expressions[0];
		} else {
			return new CompositeStringExpression(expressions);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="155">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="155:5:5" line-data="	private Expression parseEmptyExpressionString(ParserContext context) {">`parseEmptyExpressionString`</SwmToken> handles the parsing of an empty expression string.

```java
	private Expression parseEmptyExpressionString(ParserContext context) {
		if (allowDelimitedEvalExpressions) {
			// let the parser handle it
			return doParseExpression("", context);
		} else {
			// return a literal expression containing the empty string
			return new LiteralExpression("");
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="174">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="174:7:7" line-data="	private Expression[] parseExpressions(String expressionString, ParserContext context) throws ParserException {">`parseExpressions`</SwmToken> parses a given expression string that may contain multiple expressions enclosed in `${...}` markers.

```java
	private Expression[] parseExpressions(String expressionString, ParserContext context) throws ParserException {
		List<Expression> expressions = new LinkedList<>();
		int startIdx = 0;
		while (startIdx < expressionString.length()) {
			int prefixIndex = expressionString.indexOf(getExpressionPrefix(), startIdx);
			if (prefixIndex >= startIdx) {
				// a inner expression was found - this is a composite
				if (prefixIndex > startIdx) {
					expressions.add(new LiteralExpression(expressionString.substring(startIdx, prefixIndex)));
					startIdx = prefixIndex;
				}
				int nextPrefixIndex = expressionString.indexOf(getExpressionPrefix(), prefixIndex
						+ getExpressionPrefix().length());
				int suffixIndex;
				if (nextPrefixIndex == -1) {
					// this is the last expression in the expression string
					suffixIndex = expressionString.lastIndexOf(getExpressionSuffix());
				} else {
					// another expression exists after this one in the expression string
					suffixIndex = expressionString.lastIndexOf(getExpressionSuffix(), nextPrefixIndex);
				}
				if (suffixIndex < (prefixIndex + getExpressionPrefix().length())) {
					throw new ParserException(expressionString, "No ending suffix '" + getExpressionSuffix()
							+ "' for expression starting at character " + prefixIndex + ": "
							+ expressionString.substring(prefixIndex), null);
				} else if (suffixIndex == prefixIndex + getExpressionPrefix().length()) {
					throw new ParserException(expressionString, "No expression defined within delimiter '"
							+ getExpressionPrefix() + getExpressionSuffix() + "' at character " + prefixIndex, null);
				} else {
					String expr = expressionString.substring(prefixIndex + getExpressionPrefix().length(), suffixIndex);
					expressions.add(doParseExpression(expr, context));
					startIdx = suffixIndex + 1;
				}
			} else {
				if (startIdx == 0) {
					// treat the entire string as one expression
					if (allowDelimitedEvalExpressions) {
						expressions.add(doParseExpression(expressionString, context));
					} else {
						// treat entire string as a literal
						expressions.add(new LiteralExpression(expressionString));
					}
				} else {
					// no more ${expressions} found in string, add rest as static text
					expressions.add(new LiteralExpression(expressionString.substring(startIdx)));
				}
				startIdx = expressionString.length();
			}
		}
		return expressions.toArray(new Expression[expressions.size()]);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="226">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="226:11:11" line-data="	protected Map&lt;String, Expression&gt; parseVariableExpressions(ExpressionVariable[] variables) throws ParserException {">`parseVariableExpressions`</SwmToken> parses an array of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="226:13:13" line-data="	protected Map&lt;String, Expression&gt; parseVariableExpressions(ExpressionVariable[] variables) throws ParserException {">`ExpressionVariable`</SwmToken> objects into a map of variable names to their corresponding parsed expressions.

```java
	protected Map<String, Expression> parseVariableExpressions(ExpressionVariable[] variables) throws ParserException {
		if (variables == null || variables.length == 0) {
			return null;
		}
		Map<String, Expression> variableExpressions = new HashMap<>(variables.length, 1);
		for (ExpressionVariable var : variables) {
			variableExpressions.put(var.getName(), parseExpression(var.getValueExpression(), var.getParserContext()));
		}
		return variableExpressions;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" line="237">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/support/AbstractExpressionParser.java" pos="237:7:7" line-data="	protected abstract Expression doParseExpression(String expressionString, ParserContext context)">`doParseExpression`</SwmToken> is an abstract method that must be implemented by subclasses to handle the actual parsing of an expression string.

```java
	protected abstract Expression doParseExpression(String expressionString, ParserContext context)
			throws ParserException;

```

---

</SwmSnippet>

# Usage

## <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="34:4:4" line-data="public class BeanWrapperExpressionParser extends AbstractExpressionParser {">`BeanWrapperExpressionParser`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="27:12:12" line-data="import org.springframework.binding.expression.support.AbstractExpressionParser;">`AbstractExpressionParser`</SwmToken> class is extended by the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="34:4:4" line-data="public class BeanWrapperExpressionParser extends AbstractExpressionParser {">`BeanWrapperExpressionParser`</SwmToken> class. This class is responsible for parsing <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="30:13:13" line-data=" * An expression parser that parses BeanWrapper property expressions.">`BeanWrapper`</SwmToken> property expressions, which are used to access and manipulate JavaBean properties.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" line="24">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="34:4:4" line-data="public class BeanWrapperExpressionParser extends AbstractExpressionParser {">`BeanWrapperExpressionParser`</SwmToken> class includes a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="36:3:3" line-data="	private ConversionService conversionService;">`ConversionService`</SwmToken> to handle type conversions during the parsing process.

```java
import org.springframework.binding.expression.Expression;
import org.springframework.binding.expression.ParserContext;
import org.springframework.binding.expression.ParserException;
import org.springframework.binding.expression.support.AbstractExpressionParser;

/**
 * An expression parser that parses BeanWrapper property expressions.
 *
 * @author Keith Donald
 */
public class BeanWrapperExpressionParser extends AbstractExpressionParser {

	private ConversionService conversionService;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
