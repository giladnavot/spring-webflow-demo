---
title: The Parameters class
---
This document will cover the class <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="43:3:3" line-data="	public Parameters() {">`Parameters`</SwmToken> in the Spring Web Flow project. We will discuss:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="43:3:3" line-data="	public Parameters() {">`Parameters`</SwmToken> is and its purpose.
2. The variables and functions defined in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="43:3:3" line-data="	public Parameters() {">`Parameters`</SwmToken> class.

# What is Parameters

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="43:3:3" line-data="	public Parameters() {">`Parameters`</SwmToken> class in <SwmPath>[spring-binding/…/method/Parameters.java](spring-binding/src/main/java/org/springframework/binding/method/Parameters.java)</SwmPath> is an ordered list of method parameters. It is used to manage and manipulate a list of parameters that can be passed to methods.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="40">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="43:3:3" line-data="	public Parameters() {">`Parameters`</SwmToken> constructor initializes a parameter list of the default size (3 elements).

```java
	/**
	 * Create a parameter list of the default size (3 elements).
	 */
	public Parameters() {
		this(3);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="47">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="51:3:3" line-data="	public Parameters(int size) {">`Parameters`</SwmToken> constructor initializes a parameter list with the specified size.

```java
	/**
	 * Create a parameter list with the specified size.
	 * @param size the size
	 */
	public Parameters(int size) {
		this.parameters = new ArrayList<>(size);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="55">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="59:3:3" line-data="	public Parameters(Parameter parameter) {">`Parameters`</SwmToken> constructor initializes a parameter list with one parameter.

```java
	/**
	 * Create a parameter list with one parameter.
	 * @param parameter the single parameter
	 */
	public Parameters(Parameter parameter) {
		this.parameters = new ArrayList<>(1);
		add(parameter);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="64">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="68:3:3" line-data="	public Parameters(Parameter... parameters) {">`Parameters`</SwmToken> constructor initializes a parameter list from the parameter array.

```java
	/**
	 * Create a parameter list from the parameter array.
	 * @param parameters the parameters
	 */
	public Parameters(Parameter... parameters) {
		this.parameters = new ArrayList<>(parameters.length);
		addAll(parameters);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="73">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="77:5:5" line-data="	public boolean add(Parameter parameter) {">`add`</SwmToken> function adds a new parameter to the list.

```java
	/**
	 * Add a new parameter to this list.
	 * @param parameter the parameter
	 */
	public boolean add(Parameter parameter) {
		return this.parameters.add(parameter);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="81">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="85:5:5" line-data="	public boolean addAll(Parameter... parameters) {">`addAll`</SwmToken> function adds new parameters to the list.

```java
	/**
	 * Add new parameters to this list.
	 * @param parameters the parameters
	 */
	public boolean addAll(Parameter... parameters) {
		return this.parameters.addAll(Arrays.asList(parameters));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="89">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="90:9:9" line-data="	 * Return a parameter iterator.">`iterator`</SwmToken> function returns a parameter iterator.

```java
	/**
	 * Return a parameter iterator.
	 * @return the iterator
	 */
	public Iterator<Parameter> iterator() {
		return parameters.iterator();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="97">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="102:8:8" line-data="	public Class&lt;?&gt;[] getTypesArray() {">`getTypesArray`</SwmToken> function returns an array containing each parameter type. The resulting array could contain null values if the corresponding parameters did not specify a parameter type.

```java
	/**
	 * Get an array containing each parameter type. The resulting array could contain null values if the corresponding
	 * parameters did not specify a parameter type.
	 * @return the types
	 */
	public Class<?>[] getTypesArray() {
		int i = 0;
		Class<?>[] types = new Class[parameters.size()];
		for (Parameter param : parameters) {
			types[i] = param.getType();
			i++;
		}
		return types;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="112">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="114:8:8" line-data="	 * @return the size">`size`</SwmToken> function returns the number of parameters in the list.

```java
	/**
	 * Returns the number of parameters in this list.
	 * @return the size
	 */
	public int size() {
		return parameters.size();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="120">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="126:5:5" line-data="	public Parameter getParameter(int index) throws IndexOutOfBoundsException {">`getParameter`</SwmToken> function returns the parameter at the provided index.

```java
	/**
	 * Return the parameter at the provided index.
	 * @param index the parameter index
	 * @return the parameter at that index
	 * @throws IndexOutOfBoundsException if the provided index is out of bounds
	 */
	public Parameter getParameter(int index) throws IndexOutOfBoundsException {
		return parameters.get(index);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="130">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="130:5:5" line-data="	public boolean equals(Object obj) {">`equals`</SwmToken> function checks if the provided object is equal to the current <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="131:10:10" line-data="		if (!(obj instanceof Parameters)) {">`Parameters`</SwmToken> instance.

```java
	public boolean equals(Object obj) {
		if (!(obj instanceof Parameters)) {
			return false;
		}
		Parameters other = (Parameters) obj;
		return parameters.equals(other.parameters);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="138">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="138:5:5" line-data="	public int hashCode() {">`hashCode`</SwmToken> function returns the hash code of the parameters list.

```java
	public int hashCode() {
		return parameters.hashCode();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" line="142">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/Parameters.java" pos="142:5:5" line-data="	public String toString() {">`toString`</SwmToken> function returns the string representation of the parameters list.

```java
	public String toString() {
		return parameters.toString();
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" line="69">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="35:4:4" line-data="public class MethodInvoker {">`MethodInvoker`</SwmToken> class, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="71:1:1" line-data="		Parameters parameters = signature.getParameters();">`Parameters`</SwmToken> class is used to retrieve the parameters of a method signature. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="69:5:5" line-data="	public Object invoke(MethodSignature signature, Object bean, Object argumentSource)">`invoke`</SwmToken> method utilizes <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="71:1:1" line-data="		Parameters parameters = signature.getParameters();">`Parameters`</SwmToken> to create an array of arguments that are passed to the method being invoked.

```java
	public Object invoke(MethodSignature signature, Object bean, Object argumentSource)
			throws MethodInvocationException {
		Parameters parameters = signature.getParameters();
		Object[] arguments = new Object[parameters.size()];
		for (int i = 0; i < parameters.size(); i++) {
			Parameter parameter = parameters.getParameter(i);
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodSignature.java" line="39">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodSignature.java" pos="45:3:3" line-data="	public MethodSignature(String methodName) {">`MethodSignature`</SwmToken> class, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodSignature.java" pos="39:3:3" line-data="	private Parameters parameters;">`Parameters`</SwmToken> is used to store and manage the parameter types of a method. It is initialized in various constructors of <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodSignature.java" pos="45:3:3" line-data="	public MethodSignature(String methodName) {">`MethodSignature`</SwmToken>, either with no parameters, a single parameter, or multiple parameters.

```java
	private Parameters parameters;

	/**
	 * Creates a method signature with no parameters.
	 * @param methodName the name of the method
	 */
	public MethodSignature(String methodName) {
		this(methodName, Parameters.NONE);
	}

	/**
	 * Creates a method signature with a single parameter.
	 * @param methodName the name of the method
	 * @param parameter the method parameter
	 */
	public MethodSignature(String methodName, Parameter parameter) {
		this(methodName, new Parameters(parameter));
	}

	/**
	 * Creates a method signature with a list of parameters.
	 * @param methodName the name of the method
	 * @param parameters the method parameters
	 */
	public MethodSignature(String methodName, Parameters parameters) {
		Assert.notNull(methodName, "The method name is required");
		Assert.notNull(parameters, "The parameters are required");
		this.methodName = methodName;
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodSignature.java" line="77">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodSignature.java" pos="80:5:5" line-data="	public Parameters getParameters() {">`getParameters`</SwmToken> method in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="69:7:7" line-data="	public Object invoke(MethodSignature signature, Object bean, Object argumentSource)">`MethodSignature`</SwmToken> class returns the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodSignature.java" pos="80:3:3" line-data="	public Parameters getParameters() {">`Parameters`</SwmToken> object, allowing access to the method's parameters.

```java
	/**
	 * Returns the method parameters.
	 */
	public Parameters getParameters() {
		return parameters;
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
