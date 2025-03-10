---
title: The MethodKey class
---
This document will provide an overview of the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="61:3:3" line-data="	public MethodKey(Class&lt;?&gt; declaredType, String methodName, Class&lt;?&gt;... parameterTypes) {">`MethodKey`</SwmToken> class. We will cover:

1. What <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="61:3:3" line-data="	public MethodKey(Class&lt;?&gt; declaredType, String methodName, Class&lt;?&gt;... parameterTypes) {">`MethodKey`</SwmToken> is.
2. Variables and functions defined in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="61:3:3" line-data="	public MethodKey(Class&lt;?&gt; declaredType, String methodName, Class&lt;?&gt;... parameterTypes) {">`MethodKey`</SwmToken>.

# What is <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="61:3:3" line-data="	public MethodKey(Class&lt;?&gt; declaredType, String methodName, Class&lt;?&gt;... parameterTypes) {">`MethodKey`</SwmToken>

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="61:3:3" line-data="	public MethodKey(Class&lt;?&gt; declaredType, String methodName, Class&lt;?&gt;... parameterTypes) {">`MethodKey`</SwmToken> class in <SwmPath>[spring-binding/…/method/MethodKey.java](spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java)</SwmPath> is a helper for resolving and caching a Java method by reflection. It is used to identify a method by its declaring class, name, and parameter types, and to cache the resolved method for efficient access.

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="61">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="61:3:3" line-data="	public MethodKey(Class&lt;?&gt; declaredType, String methodName, Class&lt;?&gt;... parameterTypes) {">`MethodKey`</SwmToken> is a constructor that initializes a new method key with the specified class, method name, and parameter types.

```java
	public MethodKey(Class<?> declaredType, String methodName, Class<?>... parameterTypes) {
		Assert.notNull(declaredType, "The method's declared type is required");
		Assert.notNull(methodName, "The method name is required");
		this.declaredType = declaredType;
		this.methodName = methodName;
		this.parameterTypes = parameterTypes;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="72">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="72:6:6" line-data="	public Class&lt;?&gt; getDeclaredType() {">`getDeclaredType`</SwmToken> returns the class the method is a member of.

```java
	public Class<?> getDeclaredType() {
		return declaredType;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="79">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="79:5:5" line-data="	public String getMethodName() {">`getMethodName`</SwmToken> returns the method name.

```java
	public String getMethodName() {
		return methodName;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="87">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="87:8:8" line-data="	public Class&lt;?&gt;[] getParameterTypes() {">`getParameterTypes`</SwmToken> returns the method parameter types. It could contain null values if no type was specified for the corresponding parameter.

```java
	public Class<?>[] getParameterTypes() {
		return parameterTypes;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="94">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="94:5:5" line-data="	public Method getMethod() throws InvalidMethodKeyException {">`getMethod`</SwmToken> returns the keyed method, resolving it if necessary via reflection.

```java
	public Method getMethod() throws InvalidMethodKeyException {
		if (method == null) {
			method = resolveMethod();
		}
		return method;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="106">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="106:5:5" line-data="	protected Method resolveMethod() throws InvalidMethodKeyException {">`resolveMethod`</SwmToken> resolves the keyed method.

```java
	protected Method resolveMethod() throws InvalidMethodKeyException {
		try {
			return declaredType.getMethod(methodName, parameterTypes);
		} catch (NoSuchMethodException e) {
			Method method = findMethodConsiderAssignableParameterTypes();
			if (method != null) {
				return method;
			} else {
				throw new InvalidMethodKeyException(this, e);
			}
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="122">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="122:5:5" line-data="	protected Method findMethodConsiderAssignableParameterTypes() {">`findMethodConsiderAssignableParameterTypes`</SwmToken> finds the keyed method using 'relaxed' typing.

```java
	protected Method findMethodConsiderAssignableParameterTypes() {
		Method[] candidateMethods = getDeclaredType().getMethods();
		for (Method candidateMethod : candidateMethods) {
			if (candidateMethod.getName().equals(methodName)) {
				// Check if the method has the correct number of parameters.
				Class<?>[] candidateParameterTypes = candidateMethod.getParameterTypes();
				if (candidateParameterTypes.length == parameterTypes.length) {
					int numberOfCorrectArguments = 0;
					for (int j = 0; j < candidateParameterTypes.length; j++) {
						// Check if the candidate type is assignable to the sig
						// parameter type.
						Class<?> candidateType = candidateParameterTypes[j];
						Class<?> parameterType = parameterTypes[j];
						if (parameterType != null) {
							if (isAssignable(candidateType, parameterType)) {
								numberOfCorrectArguments++;
							}
						} else {
							// just match on a null param type (effectively 'any')
							numberOfCorrectArguments++;
						}
					}
					if (numberOfCorrectArguments == parameterTypes.length) {
						return candidateMethod;
					}
				}
			}
		}
		return null;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="153">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="153:5:5" line-data="	public boolean equals(Object obj) {">`equals`</SwmToken> checks if the given object is equal to this <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="154:10:10" line-data="		if (!(obj instanceof MethodKey)) {">`MethodKey`</SwmToken>.

```java
	public boolean equals(Object obj) {
		if (!(obj instanceof MethodKey)) {
			return false;
		}
		MethodKey other = (MethodKey) obj;
		return declaredType.equals(other.declaredType) && methodName.equals(other.methodName)
				&& parameterTypesEqual(other.parameterTypes);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="162">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="162:5:5" line-data="	private boolean parameterTypesEqual(Class&lt;?&gt;[] other) {">`parameterTypesEqual`</SwmToken> checks if the parameter types are equal to the given parameter types.

```java
	private boolean parameterTypesEqual(Class<?>[] other) {
		if (parameterTypes == other) {
			return true;
		}
		if (parameterTypes.length != other.length) {
			return false;
		}
		for (int i = 0; i < this.parameterTypes.length; i++) {
			if (!ObjectUtils.nullSafeEquals(parameterTypes[i], other[i])) {
				return false;
			}
		}
		return true;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="177">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="177:5:5" line-data="	public int hashCode() {">`hashCode`</SwmToken> returns the hash code for this <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="61:3:3" line-data="	public MethodKey(Class&lt;?&gt; declaredType, String methodName, Class&lt;?&gt;... parameterTypes) {">`MethodKey`</SwmToken>.

```java
	public int hashCode() {
		return declaredType.hashCode() + methodName.hashCode() + parameterTypesHash();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="181">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="181:5:5" line-data="	private int parameterTypesHash() {">`parameterTypesHash`</SwmToken> returns the hash code for the parameter types.

```java
	private int parameterTypesHash() {
		if (parameterTypes == null) {
			return 0;
		}
		int hash = 0;
		for (Class<?> parameterType : parameterTypes) {
			if (parameterType != null) {
				hash += parameterType.hashCode();
			}
		}
		return hash;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="194">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="194:5:5" line-data="	public String toString() {">`toString`</SwmToken> returns a string representation of the method key.

```java
	public String toString() {
		return methodName + "(" + parameterTypesString() + ")";
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="201">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="201:5:5" line-data="	private String parameterTypesString() {">`parameterTypesString`</SwmToken> returns the parameter types describing the signature of the method as a string.

```java
	private String parameterTypesString() {
		StringBuilder parameterTypesString = new StringBuilder();
		for (int i = 0; i < parameterTypes.length; i++) {
			if (parameterTypes[i] == null) {
				parameterTypesString.append("<any>");
			} else {
				parameterTypesString.append(ClassUtils.getShortName(parameterTypes[i]));
			}
			if (i < parameterTypes.length - 1) {
				parameterTypesString.append(',');
			}
		}
		return parameterTypesString.toString();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" line="227">

---

The function <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodKey.java" pos="227:7:7" line-data="	private static boolean isAssignable(Class&lt;?&gt; targetType, Class&lt;?&gt; valueType) {">`isAssignable`</SwmToken> determines if the given target type is assignable from the given value type, assuming setting by reflection.

```java
	private static boolean isAssignable(Class<?> targetType, Class<?> valueType) {
		return (targetType.isAssignableFrom(valueType) || targetType.equals(PRIMITIVE_WRAPPER_TYPE_MAP.get(valueType)));
	}
```

---

</SwmSnippet>

# Usage

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/action/DispatchMethodInvoker.java" line="51">

---

In the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/DispatchMethodInvoker.java" pos="34:2:2" line-data="class DispatchMethodInvoker {">`DispatchMethodInvoker`</SwmToken> class, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/DispatchMethodInvoker.java" pos="54:5:5" line-data="				return new MethodKey(target.getClass(), methodName, parameterTypes).getMethod();">`MethodKey`</SwmToken> is used to create a method instance from a given key. The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/DispatchMethodInvoker.java" pos="51:5:5" line-data="		public Method create(String key) {">`create`</SwmToken> method attempts to resolve the method name using <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/DispatchMethodInvoker.java" pos="54:5:5" line-data="				return new MethodKey(target.getClass(), methodName, parameterTypes).getMethod();">`MethodKey`</SwmToken> and throws an <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/action/DispatchMethodInvoker.java" pos="55:6:6" line-data="			} catch (InvalidMethodKeyException e) {">`InvalidMethodKeyException`</SwmToken> if the method cannot be found.

```java
		public Method create(String key) {
			String methodName = key;
			try {
				return new MethodKey(target.getClass(), methodName, parameterTypes).getMethod();
			} catch (InvalidMethodKeyException e) {
				throw new MethodLookupException("Unable to resolve dispatch method " + e.getMethodKey()
						+ "'; make sure the method name is correct and such a method is defined on targetClass "
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/InvalidMethodKeyException.java" line="25">

---

The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/InvalidMethodKeyException.java" pos="35:3:3" line-data="	public InvalidMethodKeyException(MethodKey methodKey, Exception cause) {">`InvalidMethodKeyException`</SwmToken> class uses <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/InvalidMethodKeyException.java" pos="28:3:3" line-data="	private MethodKey methodKey;">`MethodKey`</SwmToken> to store the method key that could not be resolved. This class provides a constructor to initialize the exception with the invalid method key and a method to retrieve it.

```java
	/**
	 * The method key that could not be resolved.
	 */
	private MethodKey methodKey;

	/**
	 * Creates an exception signaling an invalid method signature.
	 * @param methodKey the class method key
	 * @param cause the cause
	 */
	public InvalidMethodKeyException(MethodKey methodKey, Exception cause) {
		super("Could not resolve method with key " + methodKey, cause);
		this.methodKey = methodKey;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" line="47">

---

In the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="35:4:4" line-data="public class MethodInvoker {">`MethodInvoker`</SwmToken> class, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="48:5:5" line-data="	private AbstractCachingMapDecorator&lt;MethodKey, Method&gt; methodCache = new AbstractCachingMapDecorator&lt;MethodKey, Method&gt;(true) {">`MethodKey`</SwmToken> is used to cache invoked bean methods. The <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="48:11:11" line-data="	private AbstractCachingMapDecorator&lt;MethodKey, Method&gt; methodCache = new AbstractCachingMapDecorator&lt;MethodKey, Method&gt;(true) {">`methodCache`</SwmToken> is a map that uses <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="48:5:5" line-data="	private AbstractCachingMapDecorator&lt;MethodKey, Method&gt; methodCache = new AbstractCachingMapDecorator&lt;MethodKey, Method&gt;(true) {">`MethodKey`</SwmToken> as the key to store and retrieve method instances. Additionally, <SwmToken path="spring-binding/src/main/java/org/springframework/binding/method/MethodInvoker.java" pos="48:5:5" line-data="	private AbstractCachingMapDecorator&lt;MethodKey, Method&gt; methodCache = new AbstractCachingMapDecorator&lt;MethodKey, Method&gt;(true) {">`MethodKey`</SwmToken> is used to create a key for method lookup in the cache.

```java
	@SuppressWarnings("serial")
	private AbstractCachingMapDecorator<MethodKey, Method> methodCache = new AbstractCachingMapDecorator<MethodKey, Method>(true) {
		public Method create(MethodKey key) {
			return key.getMethod();
		}
	};

	/**
	 * Sets the conversion service to convert argument values as needed.
	 */
	public void setConversionService(ConversionService conversionService) {
		this.conversionService = conversionService;
	}

	/**
	 * Invoke the method on the bean provided. Argument values are pulled from the provided argument source.
	 * @param signature the definition of the method to invoke, including the method name and the method argument types
	 * @param bean the bean to invoke
	 * @param argumentSource the source for method arguments
	 * @return the invoked method's return value
	 * @throws MethodInvocationException the method could not be invoked
	 */
	public Object invoke(MethodSignature signature, Object bean, Object argumentSource)
			throws MethodInvocationException {
		Parameters parameters = signature.getParameters();
		Object[] arguments = new Object[parameters.size()];
		for (int i = 0; i < parameters.size(); i++) {
			Parameter parameter = parameters.getParameter(i);
			Object argument = parameter.evaluateArgument(argumentSource);
			arguments[i] = applyTypeConversion(argument, parameter.getType());
		}
		Class<?>[] parameterTypes = parameters.getTypesArray();
		for (int i = 0; i < parameterTypes.length; i++) {
			if (parameterTypes[i] == null) {
				Object argument = arguments[i];
				if (argument != null) {
					parameterTypes[i] = argument.getClass();
				}
			}
		}
		MethodKey key = new MethodKey(bean.getClass(), signature.getMethodName(), parameterTypes);
		try {
			Method method = methodCache.get(key);
			if (logger.isDebugEnabled()) {
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
