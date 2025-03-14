---
title: Getting Started with Spel in Expressions
---
# Introduction to Spel

Spel, or Spring Expression Language, is a powerful expression language that supports querying and manipulating an object graph at runtime.

# How Spel is Used

In the codebase, Spel is utilized through the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="45:4:4" line-data="public class SpringELExpressionParser implements ExpressionParser {">`SpringELExpressionParser`</SwmToken> class, which adapts the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="35:12:12" line-data="import org.springframework.expression.spel.standard.SpelExpressionParser;">`SpelExpressionParser`</SwmToken> to the Spring Binding <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="26:10:10" line-data="import org.springframework.binding.expression.ExpressionParser;">`ExpressionParser`</SwmToken> contract.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" line="5">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="82:13:13" line-data="		org.springframework.expression.Expression spelExpression = parseSpelExpression(expression, context);">`parseSpelExpression`</SwmToken> method is a key component that parses a given expression string into a Spel expression, considering the provided parser context.

```java
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      https://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */
package org.springframework.binding.expression.spel;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

import org.springframework.binding.convert.ConversionService;
import org.springframework.binding.convert.service.DefaultConversionService;
import org.springframework.binding.expression.Expression;
import org.springframework.binding.expression.ExpressionParser;
import org.springframework.binding.expression.ExpressionVariable;
import org.springframework.binding.expression.ParserContext;
import org.springframework.binding.expression.ParserException;
import org.springframework.binding.expression.support.NullParserContext;
import org.springframework.binding.expression.support.SimpleParserContext;
import org.springframework.context.expression.MapAccessor;
import org.springframework.expression.EvaluationContext;
import org.springframework.expression.PropertyAccessor;
import org.springframework.expression.spel.standard.SpelExpressionParser;
import org.springframework.util.Assert;

/**
 * Adapt the Spring EL {@link SpelExpressionParser} to the Spring Binding
 * {@link ExpressionParser} contract.
 *
 * @author Rossen Stoyanchev
 * @since 2.1.0
 */
public class SpringELExpressionParser implements ExpressionParser {

	private final SpelExpressionParser expressionParser;

	private final ConversionService conversionService;

	private final List<PropertyAccessor> propertyAccessors = new ArrayList<>();

	private final SimpleEvaluationContextFactory simpleContextFactory;


	public SpringELExpressionParser(SpelExpressionParser expressionParser) {
		this(expressionParser, new DefaultConversionService());
	}

	public SpringELExpressionParser(SpelExpressionParser expressionParser, ConversionService conversionService) {
		this.expressionParser = expressionParser;
		this.propertyAccessors.add(new MapAccessor());
		this.conversionService = conversionService;
		this.simpleContextFactory = new SimpleEvaluationContextFactory(this.propertyAccessors, conversionService);
	}

	public ConversionService getConversionService() {
		return conversionService;
	}

	public void addPropertyAccessor(PropertyAccessor propertyAccessor) {
		propertyAccessors.add(propertyAccessor);
	}

	public Expression parseExpression(String expression, ParserContext context) throws ParserException {

		Assert.hasText(expression, "The expression string to parse is required and must not be empty");

		context = (context == null) ? NullParserContext.INSTANCE : context;
		Map<String, Expression> expressionVars = parseSpelExpressionVariables(context.getExpressionVariables());

		org.springframework.expression.Expression spelExpression = parseSpelExpression(expression, context);
		Class<?> expectedResultType = context.getExpectedEvaluationResultType();
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

	private org.springframework.expression.Expression parseSpelExpression(String expression, ParserContext context) {
		org.springframework.expression.ParserContext spelParserContext = getSpelParserContext(context);
		if (spelParserContext != null) {
			return expressionParser.parseExpression(expression, spelParserContext);
		}
		return expressionParser.parseExpression(expression);
	}

	private org.springframework.expression.ParserContext getSpelParserContext(ParserContext context) {
		return context.isTemplate() ? org.springframework.expression.ParserContext.TEMPLATE_EXPRESSION : null;
	}

	/**
	 * Turn {@link ExpressionVariable}'s (pairs of variable names and string expressions)
	 * into a map of variable names and parsed Spring EL expressions. The map will be saved
	 * in a Spring EL {@link EvaluationContext} for later use at evaluation time.
```

---

</SwmSnippet>

This method calls <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="107:13:13" line-data="		org.springframework.expression.ParserContext spelParserContext = getSpelParserContext(context);">`getSpelParserContext`</SwmToken> to determine if the context is a template and then uses the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/spel/SpringELExpressionParser.java" pos="47:7:7" line-data="	private final SpelExpressionParser expressionParser;">`expressionParser`</SwmToken> to parse the expression accordingly.

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
