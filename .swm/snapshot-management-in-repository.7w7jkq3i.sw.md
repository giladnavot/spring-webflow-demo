---
title: Snapshot Management in Repository
---
# What is Snapshot

A Snapshot refers to a saved state of a flow execution at a particular point in time. It is used to capture the current state of a flow execution so that it can be restored later if needed.

# How Snapshot is Used

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="34:6:6" line-data="public abstract class AbstractSnapshottingFlowExecutionRepository extends AbstractFlowExecutionRepository {">`AbstractSnapshottingFlowExecutionRepository`</SwmToken> class is responsible for managing these snapshots. It uses a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="30:29:29" line-data=" * Base class for repositories that take flow execution snapshots using a {@link FlowExecutionSnapshotFactory}.">`FlowExecutionSnapshotFactory`</SwmToken> to create and restore snapshots.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" line="69">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="70:13:13" line-data="	 * Take a new flow execution snapshot.">`snapshot`</SwmToken> method in this class takes a new snapshot of the current flow execution by calling the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="75:5:5" line-data="		return snapshotFactory.createSnapshot(flowExecution);">`createSnapshot`</SwmToken> method of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="30:29:29" line-data=" * Base class for repositories that take flow execution snapshots using a {@link FlowExecutionSnapshotFactory}.">`FlowExecutionSnapshotFactory`</SwmToken>.

```java
	/**
	 * Take a new flow execution snapshot.
	 * @param flowExecution the execution to snapshot
	 * @return the snapshot
	 */
	protected FlowExecutionSnapshot snapshot(FlowExecution flowExecution) {
		return snapshotFactory.createSnapshot(flowExecution);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" line="78">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="86:5:5" line-data="	protected FlowExecution restoreFlowExecution(FlowExecutionSnapshot snapshot, FlowExecutionKey key,">`restoreFlowExecution`</SwmToken> method is used to restore a flow execution from a previously taken snapshot. It uses the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="91:5:5" line-data="		return snapshotFactory.restoreExecution(snapshot, flowId, key, conversationScope, this);">`restoreExecution`</SwmToken> method of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="30:29:29" line-data=" * Base class for repositories that take flow execution snapshots using a {@link FlowExecutionSnapshotFactory}.">`FlowExecutionSnapshotFactory`</SwmToken>.

```java
	/**
	 * Restore a flow execution from a snapshot.
	 * @param snapshot the snapshot
	 * @param key the flow execution snapshot key
	 * @param conversation the governing conversation
	 * @return the restored flow execution
	 */
	@SuppressWarnings("unchecked")
	protected FlowExecution restoreFlowExecution(FlowExecutionSnapshot snapshot, FlowExecutionKey key,
			Conversation conversation) {
		MutableAttributeMap<Object> conversationScope = (MutableAttributeMap<Object>) conversation
				.getAttribute("scope");
		String flowId = (String) conversation.getAttribute("name");
		return snapshotFactory.restoreExecution(snapshot, flowId, key, conversationScope, this);
	}
```

---

</SwmSnippet>

# Main Functions

There are several main functions related to Snapshot. Some of them are <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="70:13:13" line-data="	 * Take a new flow execution snapshot.">`snapshot`</SwmToken>, <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="86:5:5" line-data="	protected FlowExecution restoreFlowExecution(FlowExecutionSnapshot snapshot, FlowExecutionKey key,">`restoreFlowExecution`</SwmToken>, and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="65:5:5" line-data="	protected Serializable getSnapshotId(FlowExecutionKey key) {">`getSnapshotId`</SwmToken>. We will dive a little into <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="70:13:13" line-data="	 * Take a new flow execution snapshot.">`snapshot`</SwmToken> and <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="86:5:5" line-data="	protected FlowExecution restoreFlowExecution(FlowExecutionSnapshot snapshot, FlowExecutionKey key,">`restoreFlowExecution`</SwmToken>.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" line="69">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="70:13:13" line-data="	 * Take a new flow execution snapshot.">`snapshot`</SwmToken> function is responsible for taking a new snapshot of the current flow execution. It utilizes the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="75:5:5" line-data="		return snapshotFactory.createSnapshot(flowExecution);">`createSnapshot`</SwmToken> method of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="30:29:29" line-data=" * Base class for repositories that take flow execution snapshots using a {@link FlowExecutionSnapshotFactory}.">`FlowExecutionSnapshotFactory`</SwmToken> to generate the snapshot.

```java
	/**
	 * Take a new flow execution snapshot.
	 * @param flowExecution the execution to snapshot
	 * @return the snapshot
	 */
	protected FlowExecutionSnapshot snapshot(FlowExecution flowExecution) {
		return snapshotFactory.createSnapshot(flowExecution);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" line="78">

---

The <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="86:5:5" line-data="	protected FlowExecution restoreFlowExecution(FlowExecutionSnapshot snapshot, FlowExecutionKey key,">`restoreFlowExecution`</SwmToken> function is used to restore a flow execution from a previously taken snapshot. It calls the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="91:5:5" line-data="		return snapshotFactory.restoreExecution(snapshot, flowId, key, conversationScope, this);">`restoreExecution`</SwmToken> method of the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/execution/repository/snapshot/AbstractSnapshottingFlowExecutionRepository.java" pos="30:29:29" line-data=" * Base class for repositories that take flow execution snapshots using a {@link FlowExecutionSnapshotFactory}.">`FlowExecutionSnapshotFactory`</SwmToken> to achieve this.

```java
	/**
	 * Restore a flow execution from a snapshot.
	 * @param snapshot the snapshot
	 * @param key the flow execution snapshot key
	 * @param conversation the governing conversation
	 * @return the restored flow execution
	 */
	@SuppressWarnings("unchecked")
	protected FlowExecution restoreFlowExecution(FlowExecutionSnapshot snapshot, FlowExecutionKey key,
			Conversation conversation) {
		MutableAttributeMap<Object> conversationScope = (MutableAttributeMap<Object>) conversation
				.getAttribute("scope");
		String flowId = (String) conversation.getAttribute("name");
		return snapshotFactory.restoreExecution(snapshot, flowId, key, conversationScope, this);
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
