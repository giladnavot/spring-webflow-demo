---
title: Retrieving and Formatting Field Values
---
This document explains the process of retrieving and formatting field values within the application. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken> method is responsible for obtaining the value of a specified field, ensuring it is correctly formatted for display purposes.

For example, if a user inputs data into a form, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken> method retrieves the value of a specific field, checks for any mapping results, and formats the value appropriately for display.

```mermaid
sequenceDiagram
  participant User
  participant Application
  User->>Application: Input data
  Application->>Application: Fix field name
  Application->>Application: Check mapping results
  Application->>Application: Retrieve and format field value
  Application->>User: Display formatted value
```

Here is a high level diagram of the flow, showing only the most important functions:

```mermaid
graph TD;
      subgraph springwebflowsrcmainjavaorgspringframeworkwebflowmvcview[spring-webflow/…/mvc/view]
12d323236dbb5288d76222d8c92f69680b47903b19c55ee05822101eb0f77134(BindingModel.getFieldValue) --> 655d56e871ab38491f9606e6ac42e1837c39b2207416c0e3bcc758086e85e4e5(BindingModel.getFormattedValue)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowmvcview[spring-webflow/…/mvc/view]
655d56e871ab38491f9606e6ac42e1837c39b2207416c0e3bcc758086e85e4e5(BindingModel.getFormattedValue) --> b23e6129a8ed6a251932f246cb9bccb985ee7c2bbce15261474da38439a9ccca(BindingModel.findSpringConvertingPropertyEditor)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowmvcview[spring-webflow/…/mvc/view]
655d56e871ab38491f9606e6ac42e1837c39b2207416c0e3bcc758086e85e4e5(BindingModel.getFormattedValue) --> fa0030213f933076119231abb4c9df33da918249655535dfcaf2f5a2e84cccd2(ConvertingPropertyEditorAdapter.getAsText)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowmvcview[spring-webflow/…/mvc/view]
655d56e871ab38491f9606e6ac42e1837c39b2207416c0e3bcc758086e85e4e5(BindingModel.getFormattedValue) --> f657b61dfc08af91a4e2a9e1abd3e1876a91adbc88a87786a8aa4acc0154049a(BindingModel.parseFieldExpression)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowmvcview[spring-webflow/…/mvc/view]
b23e6129a8ed6a251932f246cb9bccb985ee7c2bbce15261474da38439a9ccca(BindingModel.findSpringConvertingPropertyEditor) --> f657b61dfc08af91a4e2a9e1abd3e1876a91adbc88a87786a8aa4acc0154049a(BindingModel.parseFieldExpression)
end


      classDef mainFlowStyle color:#000000,fill:#7CB9F4
classDef rootsStyle color:#000000,fill:#00FFF4
classDef Style1 color:#000000,fill:#00FFAA
classDef Style2 color:#000000,fill:#FFFF00
classDef Style3 color:#000000,fill:#AA7CB9

%% Swimm:
%% graph TD;
%%       subgraph springwebflowsrcmainjavaorgspringframeworkwebflowmvcview[<SwmPath>[spring-webflow/…/mvc/view/](spring-webflow/src/main/java/org/springframework/webflow/mvc/view/)</SwmPath>]
%% 12d323236dbb5288d76222d8c92f69680b47903b19c55ee05822101eb0f77134(BindingModel.getFieldValue) --> 655d56e871ab38491f9606e6ac42e1837c39b2207416c0e3bcc758086e85e4e5(BindingModel.getFormattedValue)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowmvcview[<SwmPath>[spring-webflow/…/mvc/view/](spring-webflow/src/main/java/org/springframework/webflow/mvc/view/)</SwmPath>]
%% 655d56e871ab38491f9606e6ac42e1837c39b2207416c0e3bcc758086e85e4e5(BindingModel.getFormattedValue) --> b23e6129a8ed6a251932f246cb9bccb985ee7c2bbce15261474da38439a9ccca(BindingModel.findSpringConvertingPropertyEditor)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowmvcview[<SwmPath>[spring-webflow/…/mvc/view/](spring-webflow/src/main/java/org/springframework/webflow/mvc/view/)</SwmPath>]
%% 655d56e871ab38491f9606e6ac42e1837c39b2207416c0e3bcc758086e85e4e5(BindingModel.getFormattedValue) --> fa0030213f933076119231abb4c9df33da918249655535dfcaf2f5a2e84cccd2(ConvertingPropertyEditorAdapter.getAsText)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowmvcview[<SwmPath>[spring-webflow/…/mvc/view/](spring-webflow/src/main/java/org/springframework/webflow/mvc/view/)</SwmPath>]
%% 655d56e871ab38491f9606e6ac42e1837c39b2207416c0e3bcc758086e85e4e5(BindingModel.getFormattedValue) --> f657b61dfc08af91a4e2a9e1abd3e1876a91adbc88a87786a8aa4acc0154049a(BindingModel.parseFieldExpression)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowmvcview[<SwmPath>[spring-webflow/…/mvc/view/](spring-webflow/src/main/java/org/springframework/webflow/mvc/view/)</SwmPath>]
%% b23e6129a8ed6a251932f246cb9bccb985ee7c2bbce15261474da38439a9ccca(BindingModel.findSpringConvertingPropertyEditor) --> f657b61dfc08af91a4e2a9e1abd3e1876a91adbc88a87786a8aa4acc0154049a(BindingModel.parseFieldExpression)
%% end
%% 
%% 
%%       classDef mainFlowStyle color:#000000,fill:#7CB9F4
%% classDef rootsStyle color:#000000,fill:#00FFF4
%% classDef Style1 color:#000000,fill:#00FFAA
%% classDef Style2 color:#000000,fill:#FFFF00
%% classDef Style3 color:#000000,fill:#AA7CB9
```

# Flow drill down

## Inside <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>

```mermaid
graph TD
  subgraph getFieldValue
    getFieldValue:A["Fix field name"] --> getFieldValue:B["Check if mapping results exist"]
    getFieldValue:B --> |Exist| getFieldValue:C["Retrieve list of mapping results"]
    getFieldValue:C --> getFieldValue:D["Check if results list is not empty"]
    getFieldValue:D --> |Not empty| getFieldValue:E["Get the first field error"]
    getFieldValue:E --> getFieldValue:F["Return original value"]
    getFieldValue:D -->|Empty| getFieldValue:G["Return formatted field value"]
    getFieldValue:B --> |Do not exist| getFieldValue:G["Return formatted field value"]
  end

%% Swimm:
%% graph TD
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:A["Fix field name"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:B["Check if mapping results exist"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:B --> |Exist| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:C["Retrieve list of mapping results"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:C --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:D["Check if results list is not empty"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:D --> |Not empty| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:E["Get the first field error"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:E --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:F["Return original value"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:D -->|Empty| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:G["Return formatted field value"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:B --> |Do not exist| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken>:G["Return formatted field value"]
%%   end
```

## Retrieving and Formatting Field Values

First, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="134:5:5" line-data="	public Object getFieldValue(String field) {">`getFieldValue`</SwmToken> method is responsible for retrieving the value of a specified field. It starts by fixing the field name to ensure it is in the correct format.

Next, it checks if there are any mapping results available. If mapping results are present, it retrieves a list of mapping results that meet certain criteria using the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="137:12:12" line-data="			List&lt;MappingResult&gt; results = mappingResults.getResults(new FieldErrorResult(field));">`getResults`</SwmToken> method.

Then, it checks if the list of mapping results is not empty. If there are results, it retrieves the original value of the field from the first mapping result.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="134">

---

If no mapping results are found, the method proceeds to retrieve and format the value of the specified field using the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken> method. This ensures that the field value is properly formatted for display purposes.

```java
	public Object getFieldValue(String field) {
		field = fixedField(field);
		if (mappingResults != null) {
			List<MappingResult> results = mappingResults.getResults(new FieldErrorResult(field));
			if (!results.isEmpty()) {
				MappingResult fieldError = results.get(0);
				return fieldError.getOriginalValue();
			}
		}
		return getFormattedValue(field);
	}
```

---

</SwmSnippet>

## Looking at <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken> & <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken> & <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>

```mermaid
graph TD
  subgraph getFormattedValue
    getFormattedValue:A["Parse field expression with type hint"] --> getFormattedValue:B["Get value type"]
    getFormattedValue:B --> getFormattedValue:C["Check custom converter configuration"]
    getFormattedValue:C -->|Custom converter configured| getFormattedValue:D["Parse field expression without type hint"]
    getFormattedValue:D --> getFormattedValue:E["Get field value"]
    getFormattedValue:C -->|Avoid conversion| getFormattedValue:E
    getFormattedValue:E --> getFormattedValue:F["Check if value is not string"]
    getFormattedValue:F -->|Not String| getFormattedValue:G["Find and use converting property editor"]
    getFormattedValue:G --> getFormattedValue:H["Get value as text"]
    getFormattedValue:H --> getFormattedValue:I["Return value"]
  end
  subgraph getAsText
    getAsText:A["Check if converter ID is provided"] -->|Yes| getAsText:B["Execute conversion using converter ID"]
    getAsText:A -->|No| getAsText:C["Check if can convert to string"]
    getAsText:C -->|Can convert| getAsText:D["Use delegate conversion service to convert"]
    getAsText:C -->|Cannot convert| getAsText:E["Return null"]
  end
  subgraph parseFieldExpression
    parseFieldExpression:A["Create parser context for bound object"] --> parseFieldExpression:B["Check if result type hint is used"]
    parseFieldExpression:B -->|Type hint used| parseFieldExpression:C["Expect result type to be String"]
    parseFieldExpression:C --> parseFieldExpression:D["Parse expression"]
    parseFieldExpression:B -->|Type hint not used| parseFieldExpression:D
  end
  getFormattedValue:A --> parseFieldExpression
  getFormattedValue:D --> parseFieldExpression
  getFormattedValue:H --> getAsText

%% Swimm:
%% graph TD
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:A["Parse field expression with type hint"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:B["Get value type"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:B --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:C["Check custom converter configuration"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:C -->|Custom converter configured| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:D["Parse field expression without type hint"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:D --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:E["Get field value"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:C -->|Avoid conversion| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:E
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:E --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:F["Check if value is not string"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:F -->|Not String| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:G["Find and use converting property editor"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:G --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:H["Get value as text"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:H --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:I["Return value"]
%%   end
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken>:A["Check if converter ID is provided"] -->|Yes| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken>:B["Execute conversion using converter ID"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken>:A -->|No| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken>:C["Check if can convert to string"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken>:C -->|Can convert| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken>:D["Use delegate conversion service to convert"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken>:C -->|Cannot convert| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken>:E["Return null"]
%%   end
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>:A["Create parser context for bound object"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>:B["Check if result type hint is used"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>:B -->|Type hint used| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>:C["Expect result type to be String"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>:C --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>:D["Parse expression"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>:B -->|Type hint not used| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>:D
%%   end
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:A --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:D --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="143:3:3" line-data="		return getFormattedValue(field);">`getFormattedValue`</SwmToken>:H --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken>
```

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="227">

---

First, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="227:5:5" line-data="	private Object getFormattedValue(String field) {">`getFormattedValue`</SwmToken> method parses the field expression using the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken> method. This step is crucial as it interprets the field string into an expression that can be evaluated against the bound object.

```java
	private Object getFormattedValue(String field) {
		Expression fieldExpression = parseFieldExpression(field, true);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="230">

---

Next, if a custom converter is configured or conversion should be avoided, the method re-parses the field expression without the result type hint. It then finds a suitable property editor using the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken> method. This step ensures that the value can be properly converted to a string representation if necessary.

```java
		if (isCustomConverterConfigured(field) || avoidConversion(valueType)) {
			fieldExpression = parseFieldExpression(fieldExpression.getExpressionString(), false);
		}
		Object value = fieldExpression.getValue(boundObject);
		if ((value instanceof String) == false) {
			if (avoidConversion(valueType) == false) {
				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="237">

---

Then, the method retrieves the value of the field expression. If the value is not already a string and conversion is not to be avoided, it uses the property editor to convert the value to its text representation by calling the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="239:7:7" line-data="					value = editor.getAsText();">`getAsText`</SwmToken> method. This step is essential for ensuring that the value is in a displayable format.

```java
				if (editor != null) {
					editor.setValue(value);
					value = editor.getAsText();
```

---

</SwmSnippet>

## A closer look at <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>

```mermaid
graph TD
  subgraph findSpringConvertingPropertyEditor
    findSpringConvertingPropertyEditor:A["Check if conversionService is not null"] --> findSpringConvertingPropertyEditor:B["Check if field is not null"]
    findSpringConvertingPropertyEditor:B --> findSpringConvertingPropertyEditor:C["Get converterId from binderConfiguration"]
    findSpringConvertingPropertyEditor:B --> findSpringConvertingPropertyEditor:D["Get valueType from parseFieldExpression"]
    findSpringConvertingPropertyEditor:B -->|field is null| findSpringConvertingPropertyEditor:E["Check if valueType is not null"]
    findSpringConvertingPropertyEditor:E --> findSpringConvertingPropertyEditor:F["Get BeanWrapper accessor"]
    findSpringConvertingPropertyEditor:F --> findSpringConvertingPropertyEditor:G["Get TypeDescriptor from accessor"]
    findSpringConvertingPropertyEditor:G --> findSpringConvertingPropertyEditor:H["Return ConvertingPropertyEditorAdapter"]
    findSpringConvertingPropertyEditor:E -->|valueType is null| findSpringConvertingPropertyEditor:I["Return null"]
    findSpringConvertingPropertyEditor:A -->|conversionService is null| findSpringConvertingPropertyEditor:J["Return null"]
  end

%% Swimm:
%% graph TD
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:A["Check if <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="265:4:4" line-data="		if (conversionService != null) {">`conversionService`</SwmToken> is not null"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:B["Check if field is not null"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:B --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:C["Get <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="269:1:1" line-data="					converterId = binderConfiguration.getConverterId(field);">`converterId`</SwmToken> from <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="268:4:4" line-data="				if (binderConfiguration != null) {">`binderConfiguration`</SwmToken>"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:B --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:D["Get <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="230:13:13" line-data="		if (isCustomConverterConfigured(field) || avoidConversion(valueType)) {">`valueType`</SwmToken> from <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="228:7:7" line-data="		Expression fieldExpression = parseFieldExpression(field, true);">`parseFieldExpression`</SwmToken>"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:B -->|field is null| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:E["Check if <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="230:13:13" line-data="		if (isCustomConverterConfigured(field) || avoidConversion(valueType)) {">`valueType`</SwmToken> is not null"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:E --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:F["Get <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="276:1:1" line-data="				BeanWrapper accessor = PropertyAccessorFactory.forBeanPropertyAccess(boundObject);">`BeanWrapper`</SwmToken> accessor"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:F --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:G["Get <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="277:1:1" line-data="				TypeDescriptor typeDescriptor = accessor.getPropertyTypeDescriptor(field);">`TypeDescriptor`</SwmToken> from accessor"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:G --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:H["Return <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="278:5:5" line-data="				return new ConvertingPropertyEditorAdapter(conversionService, converterId, typeDescriptor);">`ConvertingPropertyEditorAdapter`</SwmToken>"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:E -->|<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="230:13:13" line-data="		if (isCustomConverterConfigured(field) || avoidConversion(valueType)) {">`valueType`</SwmToken> is null| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:I["Return null"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:A -->|<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="265:4:4" line-data="		if (conversionService != null) {">`conversionService`</SwmToken> is null| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:7:7" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`findSpringConvertingPropertyEditor`</SwmToken>:J["Return null"]
%%   end
```

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="265">

---

First, the method checks if a conversion service is available. If not, it returns null, indicating that no <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="236:1:1" line-data="				PropertyEditor editor = findSpringConvertingPropertyEditor(field, valueType);">`PropertyEditor`</SwmToken> can be found.

```java
		if (conversionService != null) {
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="268">

---

Next, it attempts to retrieve a converter ID from the binder configuration if a field is provided. This converter ID is used to identify the specific converter needed for the field.

```java
				if (binderConfiguration != null) {
					converterId = binderConfiguration.getConverterId(field);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="271">

---

If the value type is not provided, it parses the field expression to determine the value type. This step ensures that the correct type is used for conversion.

```java
				if (valueType == null) {
					valueType = parseFieldExpression(field, false).getValueType(boundObject);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="276">

---

Then, if a value type is determined, it creates a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="276:1:1" line-data="				BeanWrapper accessor = PropertyAccessorFactory.forBeanPropertyAccess(boundObject);">`BeanWrapper`</SwmToken> to access the property type descriptor of the field. This descriptor provides metadata about the property, such as its type.

```java
				BeanWrapper accessor = PropertyAccessorFactory.forBeanPropertyAccess(boundObject);
				TypeDescriptor typeDescriptor = accessor.getPropertyTypeDescriptor(field);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" line="278">

---

Finally, it returns a new <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/mvc/view/BindingModel.java" pos="278:5:5" line-data="				return new ConvertingPropertyEditorAdapter(conversionService, converterId, typeDescriptor);">`ConvertingPropertyEditorAdapter`</SwmToken>, which adapts the conversion service to the property editor interface, using the converter ID and type descriptor. If no value type is determined, it returns null.

```java
				return new ConvertingPropertyEditorAdapter(conversionService, converterId, typeDescriptor);
			} else {
				return null;
			}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
