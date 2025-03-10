---
title: The StringToDate class
---
This document will provide an overview of the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="47:3:3" line-data="	public StringToDate() {">`StringToDate`</SwmToken> class. We will cover:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="47:3:3" line-data="	public StringToDate() {">`StringToDate`</SwmToken> is and its purpose.
2. The variables and functions defined in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="47:3:3" line-data="	public StringToDate() {">`StringToDate`</SwmToken>.

## What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="47:3:3" line-data="	public StringToDate() {">`StringToDate`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="47:3:3" line-data="	public StringToDate() {">`StringToDate`</SwmToken> class is a formatter for <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="48:3:3" line-data="		super(Date.class);">`Date`</SwmToken> types in the Spring framework. It allows the configuration of an explicit date pattern and locale. This class is used to convert <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="55:3:3" line-data="	public String getPattern() {">`String`</SwmToken> values to <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="48:3:3" line-data="		super(Date.class);">`Date`</SwmToken> objects and vice versa, providing flexibility in date formatting and parsing.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="47">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="47:3:3" line-data="	public StringToDate() {">`StringToDate`</SwmToken> constructor initializes the class by calling the superclass constructor with <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="48:3:5" line-data="		super(Date.class);">`Date.class`</SwmToken> as the target type.

```java
	public StringToDate() {
		super(Date.class);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="55">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="55:5:5" line-data="	public String getPattern() {">`getPattern`</SwmToken> function returns the date formatting pattern. If no pattern is specified, it returns the default pattern <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="41:14:18" line-data="	private static final String DEFAULT_PATTERN = &quot;yyyy-MM-dd&quot;;">`yyyy-MM-dd`</SwmToken>.

```java
	public String getPattern() {
		return pattern;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="63">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="63:5:5" line-data="	public void setPattern(String pattern) {">`setPattern`</SwmToken> function sets the pattern to use for formatting date values.

```java
	public void setPattern(String pattern) {
		this.pattern = pattern;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="72">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="72:5:5" line-data="	public Locale getLocale() {">`getLocale`</SwmToken> function returns the locale used for formatting date values. If no locale is specified, it returns the locale of the current thread.

```java
	public Locale getLocale() {
		return locale;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="80">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="80:5:5" line-data="	public void setLocale(Locale locale) {">`setLocale`</SwmToken> function sets the locale to use for formatting date values.

```java
	public void setLocale(Locale locale) {
		this.locale = locale;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="84">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="84:5:5" line-data="	public Object toObject(String string, Class&lt;?&gt; targetClass) {">`toObject`</SwmToken> function converts a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="84:7:7" line-data="	public Object toObject(String string, Class&lt;?&gt; targetClass) {">`String`</SwmToken> to a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="48:3:3" line-data="		super(Date.class);">`Date`</SwmToken> object using the specified date format. If the string is empty, it returns null.

```java
	public Object toObject(String string, Class<?> targetClass) {
		if (!StringUtils.hasText(string)) {
			return null;
		}
		DateFormat dateFormat = getDateFormat();
		try {
			return dateFormat.parse(string);
		} catch (ParseException e) {
			throw new InvalidFormatException(string, getPattern(dateFormat), e);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="96">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="96:5:5" line-data="	public String toString(Object target) {">`toString`</SwmToken> function converts a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="97:1:1" line-data="		Date date = (Date) target;">`Date`</SwmToken> object to a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="96:3:3" line-data="	public String toString(Object target) {">`String`</SwmToken> using the specified date format. If the date is null, it returns an empty string.

```java
	public String toString(Object target) {
		Date date = (Date) target;
		if (date == null) {
			return "";
		}
		return getDateFormat().format(date);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="106">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="106:5:5" line-data="	protected DateFormat getDateFormat() {">`getDateFormat`</SwmToken> function returns a <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="106:3:3" line-data="	protected DateFormat getDateFormat() {">`DateFormat`</SwmToken> instance based on the specified or default locale and pattern. It ensures the date format is not lenient and applies the pattern if the format is an instance of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="110:8:8" line-data="		if (format instanceof SimpleDateFormat) {">`SimpleDateFormat`</SwmToken>.

```java
	protected DateFormat getDateFormat() {
		Locale locale = determineLocale(this.locale);
		DateFormat format = DateFormat.getDateInstance(DateFormat.SHORT, locale);
		format.setLenient(false);
		if (format instanceof SimpleDateFormat) {
			String pattern = determinePattern(this.pattern);
			((SimpleDateFormat) format).applyPattern(pattern);
		} else {
			logger.warn("Unable to apply format pattern '" + pattern
					+ "'; Returned DateFormat is not a SimpleDateFormat");
		}
		return format;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="122">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="122:5:5" line-data="	private String determinePattern(String pattern) {">`determinePattern`</SwmToken> function returns the specified pattern or the default pattern if none is specified.

```java
	private String determinePattern(String pattern) {
		return pattern != null ? pattern : DEFAULT_PATTERN;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="126">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="126:5:5" line-data="	private Locale determineLocale(Locale locale) {">`determineLocale`</SwmToken> function returns the specified locale or the locale of the current thread if none is specified.

```java
	private Locale determineLocale(Locale locale) {
		return locale != null ? locale : LocaleContextHolder.getLocale();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" line="130">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="130:5:5" line-data="	private String getPattern(DateFormat format) {">`getPattern`</SwmToken> function for <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="130:7:7" line-data="	private String getPattern(DateFormat format) {">`DateFormat`</SwmToken> returns the pattern if the format is an instance of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/convert/converters/StringToDate.java" pos="131:8:8" line-data="		if (format instanceof SimpleDateFormat) {">`SimpleDateFormat`</SwmToken>. Otherwise, it logs a warning and returns a default string.

```java
	private String getPattern(DateFormat format) {
		if (format instanceof SimpleDateFormat) {
			return ((SimpleDateFormat) format).toPattern();
		} else {
			logger.warn("Pattern string cannot be determined because DateFormat is not a SimpleDateFormat");
			return "defaultDateFormatInstance";
		}
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
