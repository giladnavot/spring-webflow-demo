---
title: Getting Started with Persistence in Web Flow
---
# Introduction to Persistence in Web Flow

Persistence in Web Flow refers to the management of the persistence context during the lifecycle of a flow execution. This involves creating, binding, unbinding, and closing the persistence context as the flow progresses through its various states.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" line="41">

---

When a flow execution starts, a new persistence context is created and bound to the flow scope under the name <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" pos="52:31:31" line-data=" * &lt;li&gt;Create a new persistence context when a new flow execution with the &#39;persistenceContext&#39; attribute starts">`persistenceContext`</SwmToken>. This context is then exposed as the current session or entity manager for the current thread before processing a flow execution request.

```java
 * <li>When a flow execution starts, create a new JPA persistence context and bind it to flow scope under the name
 * {@link #PERSISTENCE_CONTEXT_ATTRIBUTE}.
 * <li>Before processing a flow execution request, expose the flow-scoped persistence context as the "current"
 * persistence context for the current thread.
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" line="112">

---

As the flow execution pauses, the persistence context is unbound from the current thread. When the flow execution resumes, the persistence context is re-bound to the current thread.

```java
		if (isPersistenceContext(context.getActiveFlow())) {
			unbind(getEntityManager(context.getFlowExecutionContext().getActiveSession()));
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/persistence/JpaFlowExecutionListener.java" line="127">

---

Upon successful completion of the flow, if the ending state is a commit state, the changes made to the persistence context are committed in a transaction. The persistence context is then unbound and closed.

```java
		if (isPersistenceContext(session.getDefinition())) {
			final EntityManager em = getEntityManager(session);
			Boolean commitStatus = session.getState().getAttributes().getBoolean("commit");
			if (Boolean.TRUE.equals(commitStatus)) {
				transactionTemplate.execute(new TransactionCallbackWithoutResult() {
					protected void doInTransactionWithoutResult(TransactionStatus status) {
						em.joinTransaction();
					}
				});
			}
			unbind(em);
			em.close();
		}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
