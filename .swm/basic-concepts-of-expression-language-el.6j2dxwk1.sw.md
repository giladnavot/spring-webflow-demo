---
title: Basic Concepts of Expression Language (EL)
---
# What is EL

Expression Language (EL) is used within the Spring Web Flow framework to evaluate expressions in a flow definition. It allows for dynamic evaluation of expressions and binding of results to variables within different scopes such as flow scope, view scope, or request scope.

# How EL is Used

EL is used by defining expressions within XML tags such as `<evaluate>` and specifying the result scope. For example, you can use the `<evaluate>` tag to call a method on a service and store the result in a specific scope.

# Where EL is Used

EL is used in various parts of the flow definition, including within `<evaluate>` tags and custom EL resolvers. It is commonly used to evaluate service methods and bind the results to variables within the flow.

An example of using EL is evaluating a search service method and storing the result in the view scope. For instance, the following code evaluates the `searchService.findHotels(searchCriteria)` expression and stores the result in the `viewScope.hotels` variable.

The `WebFlowELExpressionParser` class allows for Unified EL expressions in a `FlowDefinition` by creating a new Web Flow EL expression parser.

This parser uses an underlying EL expression factory, which is provider-specific, to create EL context instances for evaluating against a Web Flow request context.

The `RequestContextELContextFactory` class configures these EL context instances, adding custom resolvers such as `RequestContextELResolver`, `FlowResourceELResolver`, `ImplicitFlowVariableELResolver`, `ScopeSearchingELResolver`, `SpringBeanWebFlowELResolver`, and `ActionMethodELResolver`.

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
