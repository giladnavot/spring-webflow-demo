---
title: Overview of BeanWrapperExpression
---
# Overview of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="97:1:1" line-data="		BeanWrapperExpression expression = new BeanWrapperExpression(expressionString, conversionService);">`BeanWrapperExpression`</SwmToken>

<SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="97:1:1" line-data="		BeanWrapperExpression expression = new BeanWrapperExpression(expressionString, conversionService);">`BeanWrapperExpression`</SwmToken> is an implementation that delegates to a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="18:8:8" line-data="import org.springframework.beans.BeanWrapperImpl;">`BeanWrapperImpl`</SwmToken> to evaluate or set a property of a context.

It supports the configuration of a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="22:10:10" line-data="import org.springframework.binding.convert.ConversionService;">`ConversionService`</SwmToken> to allow StringToObject type conversion as part of setting a property.

The StringToObject ConversionExecutors are automatically adapted and registered as PropertyEditors.

<SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="97:1:1" line-data="		BeanWrapperExpression expression = new BeanWrapperExpression(expressionString, conversionService);">`BeanWrapperExpression`</SwmToken> takes advantage of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="30:13:13" line-data=" * An expression parser that parses BeanWrapper property expressions.">`BeanWrapper`</SwmToken>'s unique property access features, such as inferring types of generic collections and maps and performing type coercion on collection elements when setting values.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" line="96">

---

<SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java" pos="97:1:1" line-data="		BeanWrapperExpression expression = new BeanWrapperExpression(expressionString, conversionService);">`BeanWrapperExpression`</SwmToken> is used in <SwmPath>[spring-binding/…/beanwrapper/BeanWrapperExpressionParser.java](spring-binding/src/main/java/org/springframework/binding/expression/beanwrapper/BeanWrapperExpressionParser.java)</SwmPath> to parse expressions and set properties with type conversion.

```java
	protected Expression doParseExpression(String expressionString, ParserContext context) throws ParserException {
		BeanWrapperExpression expression = new BeanWrapperExpression(expressionString, conversionService);
		expression.setAutoGrowNestedPaths(autoGrowNestedPaths);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
