---
title: Retrieving and Constructing Flow Definitions
---
This document explains the process of retrieving or constructing a flow definition within the application. The flow definition is essential for managing the state and transitions of a flow, ensuring that the application behaves as expected during user interactions.

For example, when a user initiates a new flow, the application needs to retrieve the flow definition to determine the initial state and possible transitions. If the flow is in development and has changed, the flow definition is reassembled to reflect the latest changes.

```mermaid
sequenceDiagram
  participant Application
  participant FlowDefinition
  Application->>FlowDefinition: Check if assembling
  alt Assembling
    FlowDefinition->>Application: Return early assembly result
  else Not Assembling
    FlowDefinition->>Application: Check if flowDefinition is null
    alt FlowDefinition is null
      FlowDefinition->>Application: Log assembling first time
      FlowDefinition->>Application: Call assembleFlow
    else FlowDefinition is not null
      FlowDefinition->>Application: Check if in development and changed
      alt In development and changed
        FlowDefinition->>Application: Log reassembling
        FlowDefinition->>Application: Call assembleFlow
      end
    end
    FlowDefinition->>Application: Return flowDefinition
  end

%% Swimm:
%% sequenceDiagram
%%   participant Application
%%   participant <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken>
%%   Application->><SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken>: Check if assembling
%%   alt Assembling
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken>->>Application: Return early assembly result
%%   else Not Assembling
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken>->>Application: Check if <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="82:4:4" line-data="		if (flowDefinition == null) {">`flowDefinition`</SwmToken> is null
%%     alt <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken> is null
%%       <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken>->>Application: Log assembling first time
%%       <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken>->>Application: Call <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>
%%     else <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken> is not null
%%       <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken>->>Application: Check if in development and changed
%%       alt In development and changed
%%         <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken>->>Application: Log reassembling
%%         <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken>->>Application: Call <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>
%%       end
%%     end
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:5:5" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinition`</SwmToken>->>Application: Return <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="82:4:4" line-data="		if (flowDefinition == null) {">`flowDefinition`</SwmToken>
%%   end
```

# Where is this flow used?

This flow is used multiple times in the codebase as represented in the following diagram:

(Note - these are only some of the entry points of this flow)

```mermaid
graph TD;
      subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue) --> 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
387071bce3784df0ea7a19728f499d1c435933f20b4a167c8cc1fedca6204315(parseFlowInputMapping) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
f63b9efcab06b3607d0b6987a03a892b8781397e899614c01b7d7254680472db(parseFlowInputMapper) --> 387071bce3784df0ea7a19728f499d1c435933f20b4a167c8cc1fedca6204315(parseFlowInputMapping)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
49b1ccc3c1b8fa3198436303ff06a5c15d074e48f78e9703c9c0ea93289a81c0(buildInputMapper) --> f63b9efcab06b3607d0b6987a03a892b8781397e899614c01b7d7254680472db(parseFlowInputMapper)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
bcf7d04f200577b40e0b7b535490bb15600fd695cc4744ce27bd877350dc114d(parseSubflowInputMapping) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
556cae6e67cda19644017f7c93aa4102bea14d9cf63e1fa290b3b0a0cfc364a9(parseSubflowInputMapper) --> bcf7d04f200577b40e0b7b535490bb15600fd695cc4744ce27bd877350dc114d(parseSubflowInputMapping)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
d638420117f61b40548ce22530bcd24bf8dde83c8fb60ce1950323cef10e416a(parseSubflowAttributeMapper) --> 556cae6e67cda19644017f7c93aa4102bea14d9cf63e1fa290b3b0a0cfc364a9(parseSubflowInputMapper)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
d638420117f61b40548ce22530bcd24bf8dde83c8fb60ce1950323cef10e416a(parseSubflowAttributeMapper) --> 9ea4aa8de487562a61f6e1683b65a5b41e541b5feaa874d614beb898f8481eb4(parseSubflowOutputMapper)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState) --> d638420117f61b40548ce22530bcd24bf8dde83c8fb60ce1950323cef10e416a(parseSubflowAttributeMapper)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState) --> e8410e3b541ed84cf93d3cf313823226363a4ae835feff87091d6e7e47fa3163(parseTransitions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(buildStates) --> e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(buildStates) --> 0cab62e221f6f1870a5650ab697221b63fe822409850f88ca5dcac0bd1535c43(parseAndAddEndState)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(buildStates) --> b922f3f8059d1568b2222593691e9a43b2e699599d5225e3d5c8deb8ba023976(parseAndAddViewState)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(buildStates) --> bb32a9c3d4535d6be419bc8217ed62afa164f3b728bfed06ba1f00f6874fd79d(parseAndAddActionState)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(buildStates) --> 482009177c92fca2128b523813ac3579e693d0b371473b9d436e20624b85039f(parseAndAddDecisionState)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
2f179427de9ff5829f2fe810c39b13981e127d43d0dd12ffc8c00d73310e2ca5(directAssembly) --> 80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(buildStates)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
98c055c9b71322fa06a3f80b548fc9ac3bba717c9bc5f7729bedda3b5053efba(assembleFlow) --> 2f179427de9ff5829f2fe810c39b13981e127d43d0dd12ffc8c00d73310e2ca5(directAssembly)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
b61d14bc393f7b95415127363fcb9967656809bc62cdaa5ae06d9f081f7afde0(buildFlowDefinition) --> 98c055c9b71322fa06a3f80b548fc9ac3bba717c9bc5f7729bedda3b5053efba(assembleFlow)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowconfig[spring-webflow/…/webflow/config]
ad93a501c5167d5f44320fc4f5bf79429a0a8fa379e0d876b13e591781d40b86(registerFlowBuilders) --> b61d14bc393f7b95415127363fcb9967656809bc62cdaa5ae06d9f081f7afde0(buildFlowDefinition)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowconfig[spring-webflow/…/webflow/config]
1b90ecf800bbc7530a7fa1ce5da86edf43748f2181cd61cce0354fd86270baa3(afterPropertiesSet) --> ad93a501c5167d5f44320fc4f5bf79429a0a8fa379e0d876b13e591781d40b86(registerFlowBuilders)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
55b04cc845d25b7e0c21126e49b46672d760a40484ba2a0968c13813c003e13f(registerFlowBuilders) --> 98c055c9b71322fa06a3f80b548fc9ac3bba717c9bc5f7729bedda3b5053efba(assembleFlow)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowconfig[spring-webflow/…/webflow/config]
5ea9a3feeed8ad6d34de42f261caa9230b8ece470b9be1cfb63b5ac3dff9a97c(build) --> 55b04cc845d25b7e0c21126e49b46672d760a40484ba2a0968c13813c003e13f(registerFlowBuilders)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowconfig[spring-webflow/…/webflow/config]
e8cc0123680495888518bed32ace4fc20e41ea6ec58363164584f8c1c181a00b(FlowDefinitionRegistryBuilder) --> 5ea9a3feeed8ad6d34de42f261caa9230b8ece470b9be1cfb63b5ac3dff9a97c(build)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
0207403ab85551fc7273c1ce26425378adac0cd6340973a20db710e4e64b4bc5(parseFlowOutputMapping) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
c9b9ad019049190fbd9f7a4787ab123a14dc030d6f47190a8d7be29ed4c65925(parseFlowOutputMapper) --> 0207403ab85551fc7273c1ce26425378adac0cd6340973a20db710e4e64b4bc5(parseFlowOutputMapping)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
5459077bd95ac8612d11d46cf3f8adb2116e715211feb455e1cf92552df081f7(buildOutputMapper) --> c9b9ad019049190fbd9f7a4787ab123a14dc030d6f47190a8d7be29ed4c65925(parseFlowOutputMapper)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
0cab62e221f6f1870a5650ab697221b63fe822409850f88ca5dcac0bd1535c43(parseAndAddEndState) --> c9b9ad019049190fbd9f7a4787ab123a14dc030d6f47190a8d7be29ed4c65925(parseFlowOutputMapper)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
0cab62e221f6f1870a5650ab697221b63fe822409850f88ca5dcac0bd1535c43(parseAndAddEndState) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
0cab62e221f6f1870a5650ab697221b63fe822409850f88ca5dcac0bd1535c43(parseAndAddEndState) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
0cab62e221f6f1870a5650ab697221b63fe822409850f88ca5dcac0bd1535c43(parseAndAddEndState) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
a3601179b0f84faf5f6046ac84985a84a5892508e478e00828735a1e51b88d99(parseSubflowOutputMapping) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
9ea4aa8de487562a61f6e1683b65a5b41e541b5feaa874d614beb898f8481eb4(parseSubflowOutputMapper) --> a3601179b0f84faf5f6046ac84985a84a5892508e478e00828735a1e51b88d99(parseSubflowOutputMapping)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
d7ccacea93aad07e4fef28f09e4d920ac8d8138728c77e1cc3f8bb32da8dde03(parseSetAction) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions) --> d7ccacea93aad07e4fef28f09e4d920ac8d8138728c77e1cc3f8bb32da8dde03(parseSetAction)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
db05c4e073fc7adc9ac6c97ec7213eb6445850aca5f2a059f1ec5bd9d6a95013(buildStartActions) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
e8298b856574ac9f33168f6cd2d0a5c1e2f46338422f3e15528045a90ee2fa76(buildEndActions) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
b922f3f8059d1568b2222593691e9a43b2e699599d5225e3d5c8deb8ba023976(parseAndAddViewState) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
b922f3f8059d1568b2222593691e9a43b2e699599d5225e3d5c8deb8ba023976(parseAndAddViewState) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
b922f3f8059d1568b2222593691e9a43b2e699599d5225e3d5c8deb8ba023976(parseAndAddViewState) --> e8410e3b541ed84cf93d3cf313823226363a4ae835feff87091d6e7e47fa3163(parseTransitions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
b922f3f8059d1568b2222593691e9a43b2e699599d5225e3d5c8deb8ba023976(parseAndAddViewState) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
bb32a9c3d4535d6be419bc8217ed62afa164f3b728bfed06ba1f00f6874fd79d(parseAndAddActionState) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
bb32a9c3d4535d6be419bc8217ed62afa164f3b728bfed06ba1f00f6874fd79d(parseAndAddActionState) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
bb32a9c3d4535d6be419bc8217ed62afa164f3b728bfed06ba1f00f6874fd79d(parseAndAddActionState) --> e8410e3b541ed84cf93d3cf313823226363a4ae835feff87091d6e7e47fa3163(parseTransitions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
bb32a9c3d4535d6be419bc8217ed62afa164f3b728bfed06ba1f00f6874fd79d(parseAndAddActionState) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
482009177c92fca2128b523813ac3579e693d0b371473b9d436e20624b85039f(parseAndAddDecisionState) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
482009177c92fca2128b523813ac3579e693d0b371473b9d436e20624b85039f(parseAndAddDecisionState) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
482009177c92fca2128b523813ac3579e693d0b371473b9d436e20624b85039f(parseAndAddDecisionState) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
6ef62679ea6c5d7b1d339b5fd374ec478ed8a66d60ccb4c5e2b8ae25d971e660(parseTransitionExecutingExceptionHandler) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
6c255f7d2531ba8470bf806f2dd526279f0a73de4ef975792be433f325f28046(parseTransitionExecutingExceptionHandlers) --> 6ef62679ea6c5d7b1d339b5fd374ec478ed8a66d60ccb4c5e2b8ae25d971e660(parseTransitionExecutingExceptionHandler)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers) --> 6c255f7d2531ba8470bf806f2dd526279f0a73de4ef975792be433f325f28046(parseTransitionExecutingExceptionHandlers)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
4dc620f1d328175a30900792746e542ac6d86346d524ac58853c3e7c8fabdb7e(buildExceptionHandlers) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
1bbc9fe60a8d0446fa804ad425d685cada8f5e118367cc0bae629f7a86ea551a(parseTransition) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
1bbc9fe60a8d0446fa804ad425d685cada8f5e118367cc0bae629f7a86ea551a(parseTransition) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
e8410e3b541ed84cf93d3cf313823226363a4ae835feff87091d6e7e47fa3163(parseTransitions) --> 1bbc9fe60a8d0446fa804ad425d685cada8f5e118367cc0bae629f7a86ea551a(parseTransition)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
9ff35a0f5ef811ba5664f22e8c6f19aa98eab3bc988feb6941d5ad8080fe3189(buildGlobalTransitions) --> e8410e3b541ed84cf93d3cf313823226363a4ae835feff87091d6e7e47fa3163(parseTransitions)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
f2bf42daf3dea853be5364521925248a521041d28b4d28f11052cf886e87b37d(parseAndPutMetaAttribute) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes) --> f2bf42daf3dea853be5364521925248a521041d28b4d28f11052cf886e87b37d(parseAndPutMetaAttribute)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
3051216588f53cfc54a8774835a481a54c8a160b3d8c37f854aecde3ee9cbc7b(parseFlowMetaAttributes) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
1941ec76fdbbbd18bd110e70f257a0b1893155e90d293a6e829b7f6cb518eb02(createFlow) --> 3051216588f53cfc54a8774835a481a54c8a160b3d8c37f854aecde3ee9cbc7b(parseFlowMetaAttributes)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[spring-webflow/…/builder/model]
1941ec76fdbbbd18bd110e70f257a0b1893155e90d293a6e829b7f6cb518eb02(createFlow) --> 1941ec76fdbbbd18bd110e70f257a0b1893155e90d293a6e829b7f6cb518eb02(createFlow)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
5cb3716abe4012aeb140f6f5c1a60f82128529074fec7248593bfa6fe472e0c4(restoreFlowExecution) --> 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
47c681be45beb9523ccfcb8906e9347cfa8fd2eebac283fa411ac51ea0db470c(launchExecution) --> 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
4810857ef86f98234aafc2e154746369fed43bb1b5f3e52da09e22d7d8ec496e(restoreExecution) --> 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
e8e3df8e5b8a7c670a071e9333c212e5258c247c659c5eb7f9af0fdb935d949d(restoreExecution) --> 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition)
end


      classDef mainFlowStyle color:#000000,fill:#7CB9F4
classDef rootsStyle color:#000000,fill:#00FFF4
classDef Style1 color:#000000,fill:#00FFAA
classDef Style2 color:#000000,fill:#FFFF00
classDef Style3 color:#000000,fill:#AA7CB9

%% Swimm:
%% graph TD;
%%       subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue) --> 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 387071bce3784df0ea7a19728f499d1c435933f20b4a167c8cc1fedca6204315(parseFlowInputMapping) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% f63b9efcab06b3607d0b6987a03a892b8781397e899614c01b7d7254680472db(parseFlowInputMapper) --> 387071bce3784df0ea7a19728f499d1c435933f20b4a167c8cc1fedca6204315(parseFlowInputMapping)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 49b1ccc3c1b8fa3198436303ff06a5c15d074e48f78e9703c9c0ea93289a81c0(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="104:3:3" line-data="		flowBuilder.buildInputMapper();">`buildInputMapper`</SwmToken>) --> f63b9efcab06b3607d0b6987a03a892b8781397e899614c01b7d7254680472db(parseFlowInputMapper)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% bcf7d04f200577b40e0b7b535490bb15600fd695cc4744ce27bd877350dc114d(parseSubflowInputMapping) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 556cae6e67cda19644017f7c93aa4102bea14d9cf63e1fa290b3b0a0cfc364a9(parseSubflowInputMapper) --> bcf7d04f200577b40e0b7b535490bb15600fd695cc4744ce27bd877350dc114d(parseSubflowInputMapping)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% d638420117f61b40548ce22530bcd24bf8dde83c8fb60ce1950323cef10e416a(parseSubflowAttributeMapper) --> 556cae6e67cda19644017f7c93aa4102bea14d9cf63e1fa290b3b0a0cfc364a9(parseSubflowInputMapper)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% d638420117f61b40548ce22530bcd24bf8dde83c8fb60ce1950323cef10e416a(parseSubflowAttributeMapper) --> 9ea4aa8de487562a61f6e1683b65a5b41e541b5feaa874d614beb898f8481eb4(parseSubflowOutputMapper)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState) --> d638420117f61b40548ce22530bcd24bf8dde83c8fb60ce1950323cef10e416a(parseSubflowAttributeMapper)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState) --> e8410e3b541ed84cf93d3cf313823226363a4ae835feff87091d6e7e47fa3163(parseTransitions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="106:3:3" line-data="		flowBuilder.buildStates();">`buildStates`</SwmToken>) --> e1f5d334a044786e4a4cb53ecd3cbd5ee18181025b5d82616afd24f0b2deeb17(parseAndAddSubflowState)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="106:3:3" line-data="		flowBuilder.buildStates();">`buildStates`</SwmToken>) --> 0cab62e221f6f1870a5650ab697221b63fe822409850f88ca5dcac0bd1535c43(parseAndAddEndState)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="106:3:3" line-data="		flowBuilder.buildStates();">`buildStates`</SwmToken>) --> b922f3f8059d1568b2222593691e9a43b2e699599d5225e3d5c8deb8ba023976(parseAndAddViewState)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="106:3:3" line-data="		flowBuilder.buildStates();">`buildStates`</SwmToken>) --> bb32a9c3d4535d6be419bc8217ed62afa164f3b728bfed06ba1f00f6874fd79d(parseAndAddActionState)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="106:3:3" line-data="		flowBuilder.buildStates();">`buildStates`</SwmToken>) --> 482009177c92fca2128b523813ac3579e693d0b371473b9d436e20624b85039f(parseAndAddDecisionState)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 2f179427de9ff5829f2fe810c39b13981e127d43d0dd12ffc8c00d73310e2ca5(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="91:1:1" line-data="			directAssembly();">`directAssembly`</SwmToken>) --> 80d714d24669a6d98648cb807f43932b2ad32db2684e3fd188cea80062eb1604(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="106:3:3" line-data="		flowBuilder.buildStates();">`buildStates`</SwmToken>)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% 98c055c9b71322fa06a3f80b548fc9ac3bba717c9bc5f7729bedda3b5053efba(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>) --> 2f179427de9ff5829f2fe810c39b13981e127d43d0dd12ffc8c00d73310e2ca5(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="91:1:1" line-data="			directAssembly();">`directAssembly`</SwmToken>)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% b61d14bc393f7b95415127363fcb9967656809bc62cdaa5ae06d9f081f7afde0(buildFlowDefinition) --> 98c055c9b71322fa06a3f80b548fc9ac3bba717c9bc5f7729bedda3b5053efba(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowconfig[<SwmPath>[spring-webflow/…/webflow/config/](spring-webflow/src/main/java/org/springframework/webflow/config/)</SwmPath>]
%% ad93a501c5167d5f44320fc4f5bf79429a0a8fa379e0d876b13e591781d40b86(registerFlowBuilders) --> b61d14bc393f7b95415127363fcb9967656809bc62cdaa5ae06d9f081f7afde0(buildFlowDefinition)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowconfig[<SwmPath>[spring-webflow/…/webflow/config/](spring-webflow/src/main/java/org/springframework/webflow/config/)</SwmPath>]
%% 1b90ecf800bbc7530a7fa1ce5da86edf43748f2181cd61cce0354fd86270baa3(afterPropertiesSet) --> ad93a501c5167d5f44320fc4f5bf79429a0a8fa379e0d876b13e591781d40b86(registerFlowBuilders)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% 55b04cc845d25b7e0c21126e49b46672d760a40484ba2a0968c13813c003e13f(registerFlowBuilders) --> 98c055c9b71322fa06a3f80b548fc9ac3bba717c9bc5f7729bedda3b5053efba(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowconfig[<SwmPath>[spring-webflow/…/webflow/config/](spring-webflow/src/main/java/org/springframework/webflow/config/)</SwmPath>]
%% 5ea9a3feeed8ad6d34de42f261caa9230b8ece470b9be1cfb63b5ac3dff9a97c(build) --> 55b04cc845d25b7e0c21126e49b46672d760a40484ba2a0968c13813c003e13f(registerFlowBuilders)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowconfig[<SwmPath>[spring-webflow/…/webflow/config/](spring-webflow/src/main/java/org/springframework/webflow/config/)</SwmPath>]
%% e8cc0123680495888518bed32ace4fc20e41ea6ec58363164584f8c1c181a00b(FlowDefinitionRegistryBuilder) --> 5ea9a3feeed8ad6d34de42f261caa9230b8ece470b9be1cfb63b5ac3dff9a97c(build)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 0207403ab85551fc7273c1ce26425378adac0cd6340973a20db710e4e64b4bc5(parseFlowOutputMapping) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% c9b9ad019049190fbd9f7a4787ab123a14dc030d6f47190a8d7be29ed4c65925(parseFlowOutputMapper) --> 0207403ab85551fc7273c1ce26425378adac0cd6340973a20db710e4e64b4bc5(parseFlowOutputMapping)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 5459077bd95ac8612d11d46cf3f8adb2116e715211feb455e1cf92552df081f7(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="109:3:3" line-data="		flowBuilder.buildOutputMapper();">`buildOutputMapper`</SwmToken>) --> c9b9ad019049190fbd9f7a4787ab123a14dc030d6f47190a8d7be29ed4c65925(parseFlowOutputMapper)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 0cab62e221f6f1870a5650ab697221b63fe822409850f88ca5dcac0bd1535c43(parseAndAddEndState) --> c9b9ad019049190fbd9f7a4787ab123a14dc030d6f47190a8d7be29ed4c65925(parseFlowOutputMapper)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 0cab62e221f6f1870a5650ab697221b63fe822409850f88ca5dcac0bd1535c43(parseAndAddEndState) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 0cab62e221f6f1870a5650ab697221b63fe822409850f88ca5dcac0bd1535c43(parseAndAddEndState) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 0cab62e221f6f1870a5650ab697221b63fe822409850f88ca5dcac0bd1535c43(parseAndAddEndState) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% a3601179b0f84faf5f6046ac84985a84a5892508e478e00828735a1e51b88d99(parseSubflowOutputMapping) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 9ea4aa8de487562a61f6e1683b65a5b41e541b5feaa874d614beb898f8481eb4(parseSubflowOutputMapper) --> a3601179b0f84faf5f6046ac84985a84a5892508e478e00828735a1e51b88d99(parseSubflowOutputMapping)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% d7ccacea93aad07e4fef28f09e4d920ac8d8138728c77e1cc3f8bb32da8dde03(parseSetAction) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions) --> d7ccacea93aad07e4fef28f09e4d920ac8d8138728c77e1cc3f8bb32da8dde03(parseSetAction)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% db05c4e073fc7adc9ac6c97ec7213eb6445850aca5f2a059f1ec5bd9d6a95013(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="105:3:3" line-data="		flowBuilder.buildStartActions();">`buildStartActions`</SwmToken>) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% e8298b856574ac9f33168f6cd2d0a5c1e2f46338422f3e15528045a90ee2fa76(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="108:3:3" line-data="		flowBuilder.buildEndActions();">`buildEndActions`</SwmToken>) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% b922f3f8059d1568b2222593691e9a43b2e699599d5225e3d5c8deb8ba023976(parseAndAddViewState) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% b922f3f8059d1568b2222593691e9a43b2e699599d5225e3d5c8deb8ba023976(parseAndAddViewState) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% b922f3f8059d1568b2222593691e9a43b2e699599d5225e3d5c8deb8ba023976(parseAndAddViewState) --> e8410e3b541ed84cf93d3cf313823226363a4ae835feff87091d6e7e47fa3163(parseTransitions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% b922f3f8059d1568b2222593691e9a43b2e699599d5225e3d5c8deb8ba023976(parseAndAddViewState) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% bb32a9c3d4535d6be419bc8217ed62afa164f3b728bfed06ba1f00f6874fd79d(parseAndAddActionState) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% bb32a9c3d4535d6be419bc8217ed62afa164f3b728bfed06ba1f00f6874fd79d(parseAndAddActionState) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% bb32a9c3d4535d6be419bc8217ed62afa164f3b728bfed06ba1f00f6874fd79d(parseAndAddActionState) --> e8410e3b541ed84cf93d3cf313823226363a4ae835feff87091d6e7e47fa3163(parseTransitions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% bb32a9c3d4535d6be419bc8217ed62afa164f3b728bfed06ba1f00f6874fd79d(parseAndAddActionState) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 482009177c92fca2128b523813ac3579e693d0b371473b9d436e20624b85039f(parseAndAddDecisionState) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 482009177c92fca2128b523813ac3579e693d0b371473b9d436e20624b85039f(parseAndAddDecisionState) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 482009177c92fca2128b523813ac3579e693d0b371473b9d436e20624b85039f(parseAndAddDecisionState) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 6ef62679ea6c5d7b1d339b5fd374ec478ed8a66d60ccb4c5e2b8ae25d971e660(parseTransitionExecutingExceptionHandler) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 6c255f7d2531ba8470bf806f2dd526279f0a73de4ef975792be433f325f28046(parseTransitionExecutingExceptionHandlers) --> 6ef62679ea6c5d7b1d339b5fd374ec478ed8a66d60ccb4c5e2b8ae25d971e660(parseTransitionExecutingExceptionHandler)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers) --> 6c255f7d2531ba8470bf806f2dd526279f0a73de4ef975792be433f325f28046(parseTransitionExecutingExceptionHandlers)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 4dc620f1d328175a30900792746e542ac6d86346d524ac58853c3e7c8fabdb7e(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="110:3:3" line-data="		flowBuilder.buildExceptionHandlers();">`buildExceptionHandlers`</SwmToken>) --> de5b3eddca6e2a99352d93468bf0f4c0593c418654d8c72b0bc260032ce0e0f1(parseExceptionHandlers)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 1bbc9fe60a8d0446fa804ad425d685cada8f5e118367cc0bae629f7a86ea551a(parseTransition) --> d3facd470e16c34d6307594c98edf473886bf3b7accdc03109d550cd71d872c9(parseActions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 1bbc9fe60a8d0446fa804ad425d685cada8f5e118367cc0bae629f7a86ea551a(parseTransition) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% e8410e3b541ed84cf93d3cf313823226363a4ae835feff87091d6e7e47fa3163(parseTransitions) --> 1bbc9fe60a8d0446fa804ad425d685cada8f5e118367cc0bae629f7a86ea551a(parseTransition)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 9ff35a0f5ef811ba5664f22e8c6f19aa98eab3bc988feb6941d5ad8080fe3189(<SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="107:3:3" line-data="		flowBuilder.buildGlobalTransitions();">`buildGlobalTransitions`</SwmToken>) --> e8410e3b541ed84cf93d3cf313823226363a4ae835feff87091d6e7e47fa3163(parseTransitions)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% f2bf42daf3dea853be5364521925248a521041d28b4d28f11052cf886e87b37d(parseAndPutMetaAttribute) --> 6fc1f0760777f884437e2dd8128a8d5d38ca9e9715b180ad516bc9f46c457071(getValue)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes) --> f2bf42daf3dea853be5364521925248a521041d28b4d28f11052cf886e87b37d(parseAndPutMetaAttribute)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 3051216588f53cfc54a8774835a481a54c8a160b3d8c37f854aecde3ee9cbc7b(parseFlowMetaAttributes) --> 878f12a5f11889a915a25a51f23d1ab4a14461f3434220ad2f375fe32b78aad1(parseMetaAttributes)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 1941ec76fdbbbd18bd110e70f257a0b1893155e90d293a6e829b7f6cb518eb02(createFlow) --> 3051216588f53cfc54a8774835a481a54c8a160b3d8c37f854aecde3ee9cbc7b(parseFlowMetaAttributes)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuildermodel[<SwmPath>[spring-webflow/…/builder/model/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/)</SwmPath>]
%% 1941ec76fdbbbd18bd110e70f257a0b1893155e90d293a6e829b7f6cb518eb02(createFlow) --> 1941ec76fdbbbd18bd110e70f257a0b1893155e90d293a6e829b7f6cb518eb02(createFlow)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% 5cb3716abe4012aeb140f6f5c1a60f82128529074fec7248593bfa6fe472e0c4(restoreFlowExecution) --> 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% 47c681be45beb9523ccfcb8906e9347cfa8fd2eebac283fa411ac51ea0db470c(launchExecution) --> 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% 4810857ef86f98234aafc2e154746369fed43bb1b5f3e52da09e22d7d8ec496e(restoreExecution) --> 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% e8e3df8e5b8a7c670a071e9333c212e5258c247c659c5eb7f9af0fdb935d949d(restoreExecution) --> 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition)
%% end
%% 
%% 
%%       classDef mainFlowStyle color:#000000,fill:#7CB9F4
%% classDef rootsStyle color:#000000,fill:#00FFF4
%% classDef Style1 color:#000000,fill:#00FFAA
%% classDef Style2 color:#000000,fill:#FFFF00
%% classDef Style3 color:#000000,fill:#AA7CB9
```

Here is a high level diagram of the flow, showing only the most important functions:

```mermaid
graph TD;
      subgraph springwebflowsrcmainjavaorgspringframeworkwebflowengine[spring-webflow/…/webflow/engine]
80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition) --> 6bfab42892a40839befca0267b3ce70bc063dd13bd346cd0937da0ace69c5d77(Flow.inDevelopment)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition) --> c87de7a2c294c679b12567657f29d9dea463c9ea99acca38e43a54a8695f41b0(DefaultFlowHolder.assembleFlow)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition) --> 6d8a1c0a46965ecb36057512cfa135786ad6d362179eb36879da1542b13867e1(DefaultFlowHolder.getFlowBuilder)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition) --> ae6773a1ecaa4043f72b3cd2fa74bf8891af8152dda5e964022f760799708f89(AbstractFlowBuilder.getFlow)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowcorecollectionLocalParameterMapjava[spring-webflow/…/collection/LocalParameterMap.java]
6bfab42892a40839befca0267b3ce70bc063dd13bd346cd0937da0ace69c5d77(Flow.inDevelopment) --> 8a9cab8f07aa5d5c3c9121c3fce0548329df9d0a62a89c62c117e2dc7b509380(LocalParameterMap.getBoolean)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowengine[spring-webflow/…/webflow/engine]
6bfab42892a40839befca0267b3ce70bc063dd13bd346cd0937da0ace69c5d77(Flow.inDevelopment) --> f951d2af92840d649bfc63c39986eb5a359fec153775d6ce34aee4c79aac2c15(RequestControlContextImpl.getAttributes)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowcorecollectionLocalParameterMapjava[spring-webflow/…/collection/LocalParameterMap.java]
8a9cab8f07aa5d5c3c9121c3fce0548329df9d0a62a89c62c117e2dc7b509380(LocalParameterMap.getBoolean) --> ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowcorecollectionLocalParameterMapjava[spring-webflow/…/collection/LocalParameterMap.java]
ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get) --> ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowcorecollectionLocalParameterMapjava[spring-webflow/…/collection/LocalParameterMap.java]
ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get) --> ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get)
end

subgraph springbindingsrcmainjavaorgspringframeworkbindingcollection[spring-binding/…/binding/collection]
ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get) --> 91c82ad6a52191598992822d6b77ff27e818070807c0ab99ea9d77c1e980bb20(MapAccessor.assertKeyValueInstanceOf)
end

subgraph springbindingsrcmainjavaorgspringframeworkbindingcollection[spring-binding/…/binding/collection]
ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get) --> 9dcdc8d837a56621e7fa71143692173af675c9d663c3518cdcc0a4336f6b3299(SharedMapDecorator.containsKey)
end

subgraph springbindingsrcmainjavaorgspringframeworkbindingexpressionExpressionVariablejava[spring-binding/…/expression/ExpressionVariable.java]
91c82ad6a52191598992822d6b77ff27e818070807c0ab99ea9d77c1e980bb20(MapAccessor.assertKeyValueInstanceOf) --> 3500726e0c49042d641271faa7ee523b360f832c4563885d68091ffac3acc656(ExpressionVariable.getName)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
c87de7a2c294c679b12567657f29d9dea463c9ea99acca38e43a54a8695f41b0(DefaultFlowHolder.assembleFlow) --> ad6414323e7d4256f85ec74492171f0dc6f2ac273d9a2a5692b018e8c61ac301(FlowAssembler.getFlowBuilderContext)
end

subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[spring-webflow/…/engine/builder]
c87de7a2c294c679b12567657f29d9dea463c9ea99acca38e43a54a8695f41b0(DefaultFlowHolder.assembleFlow) --> 4c49f48c294835a08aad95350156a6466ae06523b696c4cc0a96cb31dd65d0f4(LocalFlowBuilderContext.getFlowId)
end


      classDef mainFlowStyle color:#000000,fill:#7CB9F4
classDef rootsStyle color:#000000,fill:#00FFF4
classDef Style1 color:#000000,fill:#00FFAA
classDef Style2 color:#000000,fill:#FFFF00
classDef Style3 color:#000000,fill:#AA7CB9

%% Swimm:
%% graph TD;
%%       subgraph springwebflowsrcmainjavaorgspringframeworkwebflowengine[<SwmPath>[spring-webflow/…/webflow/engine/](spring-webflow/src/main/java/org/springframework/webflow/engine/)</SwmPath>]
%% 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition) --> 6bfab42892a40839befca0267b3ce70bc063dd13bd346cd0937da0ace69c5d77(Flow.inDevelopment)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition) --> c87de7a2c294c679b12567657f29d9dea463c9ea99acca38e43a54a8695f41b0(DefaultFlowHolder.assembleFlow)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition) --> 6d8a1c0a46965ecb36057512cfa135786ad6d362179eb36879da1542b13867e1(DefaultFlowHolder.getFlowBuilder)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% 80b7a63b4ecf5c25b7d9897b4b4723d53841a226c726a8ded944576e0e6166a0(DefaultFlowHolder.getFlowDefinition) --> ae6773a1ecaa4043f72b3cd2fa74bf8891af8152dda5e964022f760799708f89(AbstractFlowBuilder.getFlow)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowcorecollectionLocalParameterMapjava[<SwmPath>[spring-webflow/…/collection/LocalParameterMap.java](spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java)</SwmPath>]
%% 6bfab42892a40839befca0267b3ce70bc063dd13bd346cd0937da0ace69c5d77(Flow.inDevelopment) --> 8a9cab8f07aa5d5c3c9121c3fce0548329df9d0a62a89c62c117e2dc7b509380(LocalParameterMap.getBoolean)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowengine[<SwmPath>[spring-webflow/…/webflow/engine/](spring-webflow/src/main/java/org/springframework/webflow/engine/)</SwmPath>]
%% 6bfab42892a40839befca0267b3ce70bc063dd13bd346cd0937da0ace69c5d77(Flow.inDevelopment) --> f951d2af92840d649bfc63c39986eb5a359fec153775d6ce34aee4c79aac2c15(RequestControlContextImpl.getAttributes)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowcorecollectionLocalParameterMapjava[<SwmPath>[spring-webflow/…/collection/LocalParameterMap.java](spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java)</SwmPath>]
%% 8a9cab8f07aa5d5c3c9121c3fce0548329df9d0a62a89c62c117e2dc7b509380(LocalParameterMap.getBoolean) --> ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowcorecollectionLocalParameterMapjava[<SwmPath>[spring-webflow/…/collection/LocalParameterMap.java](spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java)</SwmPath>]
%% ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get) --> ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowcorecollectionLocalParameterMapjava[<SwmPath>[spring-webflow/…/collection/LocalParameterMap.java](spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java)</SwmPath>]
%% ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get) --> ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get)
%% end
%% 
%% subgraph springbindingsrcmainjavaorgspringframeworkbindingcollection[<SwmPath>[spring-binding/…/binding/collection/](spring-binding/src/main/java/org/springframework/binding/collection/)</SwmPath>]
%% ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get) --> 91c82ad6a52191598992822d6b77ff27e818070807c0ab99ea9d77c1e980bb20(MapAccessor.assertKeyValueInstanceOf)
%% end
%% 
%% subgraph springbindingsrcmainjavaorgspringframeworkbindingcollection[<SwmPath>[spring-binding/…/binding/collection/](spring-binding/src/main/java/org/springframework/binding/collection/)</SwmPath>]
%% ab91978c37e084fb70248f7783576b9b3ff97f2e078f11bc238b57c97c6fbe11(LocalParameterMap.get) --> 9dcdc8d837a56621e7fa71143692173af675c9d663c3518cdcc0a4336f6b3299(SharedMapDecorator.containsKey)
%% end
%% 
%% subgraph springbindingsrcmainjavaorgspringframeworkbindingexpressionExpressionVariablejava[<SwmPath>[spring-binding/…/expression/ExpressionVariable.java](spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java)</SwmPath>]
%% 91c82ad6a52191598992822d6b77ff27e818070807c0ab99ea9d77c1e980bb20(MapAccessor.assertKeyValueInstanceOf) --> 3500726e0c49042d641271faa7ee523b360f832c4563885d68091ffac3acc656(ExpressionVariable.getName)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% c87de7a2c294c679b12567657f29d9dea463c9ea99acca38e43a54a8695f41b0(DefaultFlowHolder.assembleFlow) --> ad6414323e7d4256f85ec74492171f0dc6f2ac273d9a2a5692b018e8c61ac301(FlowAssembler.getFlowBuilderContext)
%% end
%% 
%% subgraph springwebflowsrcmainjavaorgspringframeworkwebflowenginebuilder[<SwmPath>[spring-webflow/…/engine/builder/](spring-webflow/src/main/java/org/springframework/webflow/engine/builder/)</SwmPath>]
%% c87de7a2c294c679b12567657f29d9dea463c9ea99acca38e43a54a8695f41b0(DefaultFlowHolder.assembleFlow) --> 4c49f48c294835a08aad95350156a6466ae06523b696c4cc0a96cb31dd65d0f4(LocalFlowBuilderContext.getFlowId)
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

## Looking at <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken> & <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:3:3" line-data="			return getFlowBuilder().getFlow();">`getFlowBuilder`</SwmToken> & <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:7:7" line-data="			return getFlowBuilder().getFlow();">`getFlow`</SwmToken>

```mermaid
graph TD
  subgraph getFlowDefinition
    getFlowDefinition:A["Check if assembling"] -->|True| getFlowDefinition:B["Call getFlowBuilder"]
    getFlowDefinition:B --> getFlowDefinition:C["Return early assembly result"]
    getFlowDefinition:A -->|False| getFlowDefinition:D["Check if flowDefinition is null"]
    getFlowDefinition:D -->|True| getFlowDefinition:E["Log assembling first time"]
    getFlowDefinition:E --> getFlowDefinition:F["Call assembleFlow"]
    getFlowDefinition:D -->|False| getFlowDefinition:G["Check if flowDefinition in Development and has changed"]
    getFlowDefinition:G -->|True| getFlowDefinition:H["Log reassembling"]
    getFlowDefinition:H --> getFlowDefinition:I["Call assembleFlow"]
    getFlowDefinition:F --> getFlowDefinition:J["Return flowDefinition"]
    getFlowDefinition:I --> getFlowDefinition:J
  end
  subgraph getFlowBuilder
    getFlowBuilder:A["Call assembler.getFlowBuilder"] --> getFlowBuilder:B["Return FlowBuilder"]
  end
  subgraph getFlow
    getFlow:A["Return flow"]
  end
  getFlowDefinition:B --> getFlowBuilder
  getFlowBuilder:B --> getFlow

%% Swimm:
%% graph TD
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:A["Check if assembling"] -->|True| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:B["Call <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:3:3" line-data="			return getFlowBuilder().getFlow();">`getFlowBuilder`</SwmToken>"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:B --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:C["Return early assembly result"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:A -->|False| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:D["Check if <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="82:4:4" line-data="		if (flowDefinition == null) {">`flowDefinition`</SwmToken> is null"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:D -->|True| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:E["Log assembling first time"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:E --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:F["Call <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:D -->|False| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:G["Check if <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="82:4:4" line-data="		if (flowDefinition == null) {">`flowDefinition`</SwmToken> in Development and has changed"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:G -->|True| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:H["Log reassembling"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:H --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:I["Call <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:F --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:J["Return <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="82:4:4" line-data="		if (flowDefinition == null) {">`flowDefinition`</SwmToken>"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:I --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:J
%%   end
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:3:3" line-data="			return getFlowBuilder().getFlow();">`getFlowBuilder`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:3:3" line-data="			return getFlowBuilder().getFlow();">`getFlowBuilder`</SwmToken>:A["Call <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="74:3:5" line-data="		return assembler.getFlowBuilder().getFlowResourceString();">`assembler.getFlowBuilder`</SwmToken>"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:3:3" line-data="			return getFlowBuilder().getFlow();">`getFlowBuilder`</SwmToken>:B["Return <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="117:3:3" line-data="	private FlowBuilder getFlowBuilder() {">`FlowBuilder`</SwmToken>"]
%%   end
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:7:7" line-data="			return getFlowBuilder().getFlow();">`getFlow`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:7:7" line-data="			return getFlowBuilder().getFlow();">`getFlow`</SwmToken>:A["Return flow"]
%%   end
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken>:B --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:3:3" line-data="			return getFlowBuilder().getFlow();">`getFlowBuilder`</SwmToken>
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:3:3" line-data="			return getFlowBuilder().getFlow();">`getFlowBuilder`</SwmToken>:B --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="80:7:7" line-data="			return getFlowBuilder().getFlow();">`getFlow`</SwmToken>
```

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" line="77">

---

First, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:7:7" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`getFlowDefinition`</SwmToken> method checks if the flow is currently being assembled. If it is, it returns the early assembly result to handle recursive flow calls. This ensures that the flow can call itself without causing issues.

```java
	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {
		if (assembling) {
			// must return early assembly result for when a flow calls itself recursively
			return getFlowBuilder().getFlow();
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" line="82">

---

Next, if the flow definition is null, it logs a debug message indicating that the flow is being assembled for the first time and calls the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken> method. This step is crucial for initializing the flow definition.

```java
		if (flowDefinition == null) {
			logger.debug("Assembling the flow for the first time");
			assembleFlow();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" line="86">

---

Then, if the flow is in development and has changed, it logs a debug message and reassembles the flow by calling the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="88:1:1" line-data="				assembleFlow();">`assembleFlow`</SwmToken> method again. This ensures that any changes made during development are reflected in the flow definition.

```java
			if (flowDefinition.inDevelopment() && getFlowBuilder().hasFlowChanged()) {
				logger.debug("The flow under development has changed; reassembling...");
				assembleFlow();
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" line="91">

---

Finally, the method returns the flow definition. This step concludes the process of retrieving or constructing the flow definition, ensuring that the most up-to-date version is used.

```java
		return flowDefinition;
	}
```

---

</SwmSnippet>

## A closer look at <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="86:6:6" line-data="			if (flowDefinition.inDevelopment() &amp;&amp; getFlowBuilder().hasFlowChanged()) {">`inDevelopment`</SwmToken> & <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="240:3:3" line-data="		return getAttributes().getBoolean(&quot;development&quot;, false);">`getAttributes`</SwmToken>

```mermaid
graph TD
  subgraph inDevelopment
    inDevelopment:A["Call getAttributes"] --> inDevelopment:B["Get boolean 'development'"]
  end
  subgraph getAttributes
    getAttributes:A["Return attributes"]
  end
  inDevelopment:A --> getAttributes

%% Swimm:
%% graph TD
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="86:6:6" line-data="			if (flowDefinition.inDevelopment() &amp;&amp; getFlowBuilder().hasFlowChanged()) {">`inDevelopment`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="86:6:6" line-data="			if (flowDefinition.inDevelopment() &amp;&amp; getFlowBuilder().hasFlowChanged()) {">`inDevelopment`</SwmToken>:A["Call <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="240:3:3" line-data="		return getAttributes().getBoolean(&quot;development&quot;, false);">`getAttributes`</SwmToken>"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="86:6:6" line-data="			if (flowDefinition.inDevelopment() &amp;&amp; getFlowBuilder().hasFlowChanged()) {">`inDevelopment`</SwmToken>:B["Get boolean 'development'"]
%%   end
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="240:3:3" line-data="		return getAttributes().getBoolean(&quot;development&quot;, false);">`getAttributes`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="240:3:3" line-data="		return getAttributes().getBoolean(&quot;development&quot;, false);">`getAttributes`</SwmToken>:A["Return attributes"]
%%   end
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="86:6:6" line-data="			if (flowDefinition.inDevelopment() &amp;&amp; getFlowBuilder().hasFlowChanged()) {">`inDevelopment`</SwmToken>:A --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="240:3:3" line-data="		return getAttributes().getBoolean(&quot;development&quot;, false);">`getAttributes`</SwmToken>
```

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" line="239">

---

First, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="239:5:5" line-data="	public boolean inDevelopment() {">`inDevelopment`</SwmToken> method checks if the application is running in development mode. This is crucial for enabling or disabling certain features that should only be available during development. The method retrieves the 'development' attribute and returns its boolean value, defaulting to false if the attribute is not present.

```java
	public boolean inDevelopment() {
		return getAttributes().getBoolean("development", false);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" line="169">

---

Next, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="169:8:8" line-data="	public MutableAttributeMap&lt;Object&gt; getAttributes() {">`getAttributes`</SwmToken> method is called to retrieve the attributes associated with the current request context. These attributes are stored in a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/impl/RequestControlContextImpl.java" pos="169:3:3" line-data="	public MutableAttributeMap&lt;Object&gt; getAttributes() {">`MutableAttributeMap`</SwmToken> and are essential for various flow operations, such as determining the current state and handling user inputs.

```java
	public MutableAttributeMap<Object> getAttributes() {
		return attributes;
	}
```

---

</SwmSnippet>

## Exploring <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="240:7:7" line-data="		return getAttributes().getBoolean(&quot;development&quot;, false);">`getBoolean`</SwmToken>

```mermaid
graph TD
  subgraph getBoolean
    getBoolean:A["Retrieve parameter value"] --> getBoolean:B["Convert value to Boolean"]
  end

%% Swimm:
%% graph TD
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="240:7:7" line-data="		return getAttributes().getBoolean(&quot;development&quot;, false);">`getBoolean`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="240:7:7" line-data="		return getAttributes().getBoolean(&quot;development&quot;, false);">`getBoolean`</SwmToken>:A["Retrieve parameter value"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="240:7:7" line-data="		return getAttributes().getBoolean(&quot;development&quot;, false);">`getBoolean`</SwmToken>:B["Convert value to Boolean"]
%%   end
```

## Evaluating boolean parameters

First, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/Flow.java" pos="240:7:7" line-data="		return getAttributes().getBoolean(&quot;development&quot;, false);">`getBoolean`</SwmToken> method is responsible for retrieving a boolean parameter from the local parameter map. This method takes a parameter name as input and attempts to convert the corresponding value to a Boolean.

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="235">

---

Moving to the implementation, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="235:5:5" line-data="	public Boolean getBoolean(String parameterName) throws ConversionExecutionException {">`getBoolean`</SwmToken> method internally calls the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="236:3:3" line-data="		return get(parameterName, Boolean.class);">`get`</SwmToken> method, passing the parameter name and the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="236:8:10" line-data="		return get(parameterName, Boolean.class);">`Boolean.class`</SwmToken> type. This ensures that the value retrieved is specifically converted to a Boolean type.

```java
	public Boolean getBoolean(String parameterName) throws ConversionExecutionException {
		return get(parameterName, Boolean.class);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="236">

---

Next, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="236:3:3" line-data="		return get(parameterName, Boolean.class);">`get`</SwmToken> method is invoked to fetch the value associated with the given parameter name. This method handles the retrieval and type conversion, ensuring that the value is returned as a Boolean.

```java
		return get(parameterName, Boolean.class);
```

---

</SwmSnippet>

## Breaking down get

```mermaid
graph TD
 subgraph get
 get:A["Receive parameterName"] --> get:B["Call get with parameterName and null"] --> get:C["Return result of get"]
 end

%% Swimm:
%% graph TD
%%  subgraph get
%%  get:A["Receive <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="114:9:9" line-data="	public String get(String parameterName) {">`parameterName`</SwmToken>"] --> get:B["Call get with <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="114:9:9" line-data="	public String get(String parameterName) {">`parameterName`</SwmToken> and null"] --> get:C["Return result of get"]
%%  end
```

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="114">

---

First, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="114:5:5" line-data="	public String get(String parameterName) {">`get`</SwmToken> method in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="43:4:4" line-data="public class LocalParameterMap implements ParameterMap, Serializable {">`LocalParameterMap`</SwmToken> is responsible for retrieving the value of a parameter given its name. This is crucial for accessing specific parameters that are needed for further processing in the flow.

```java
	public String get(String parameterName) {
		return get(parameterName, (String) null);
	}
```

---

</SwmSnippet>

## A closer look at get & <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="119:7:7" line-data="		if (!parameters.containsKey(parameterName)) {">`containsKey`</SwmToken>

```mermaid
graph TD
  subgraph get
    get:A["Check if parameterName exists"] -->|No| get:B["Return defaultValue"]
    get:A -->|Yes| get:C["Get value from parameters"]
    get:C --> get:D["Check if value is array"]
    get:D --> |Yes| get:E["Assert array values are of type String[]"]
    get:E --> get:F["Check array length"]
    get:F --> |length == 0| get:G["Return null"]
    get:F --> |length > 0| get:H["Return first element in array"]
    get:D --> |No| get:I["Assert value is of type String"]
    get:I --> get:J["Return value"]
  end
  subgraph containsKey
    containsKey:A["Check if key exists in map"] --> containsKey:B["Return result"]
  end
  get:A --> containsKey

%% Swimm:
%% graph TD
%%   subgraph get
%%     get:A["Check if <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="114:9:9" line-data="	public String get(String parameterName) {">`parameterName`</SwmToken> exists"] -->|No| get:B["Return <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="118:14:14" line-data="	public String get(String parameterName, String defaultValue) {">`defaultValue`</SwmToken>"]
%%     get:A -->|Yes| get:C["Get value from parameters"]
%%     get:C --> get:D["Check if value is array"]
%%     get:D --> |Yes| get:E["Assert array values are of type String[]"]
%%     get:E --> get:F["Check array length"]
%%     get:F --> |length == 0| get:G["Return null"]
%%     get:F --> |length > 0| get:H["Return first element in array"]
%%     get:D --> |No| get:I["Assert value is of type String"]
%%     get:I --> get:J["Return value"]
%%   end
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="119:7:7" line-data="		if (!parameters.containsKey(parameterName)) {">`containsKey`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="119:7:7" line-data="		if (!parameters.containsKey(parameterName)) {">`containsKey`</SwmToken>:A["Check if key exists in map"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="119:7:7" line-data="		if (!parameters.containsKey(parameterName)) {">`containsKey`</SwmToken>:B["Return result"]
%%   end
%%   get:A --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="119:7:7" line-data="		if (!parameters.containsKey(parameterName)) {">`containsKey`</SwmToken>
```

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="118">

---

First, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="118:5:5" line-data="	public String get(String parameterName, String defaultValue) {">`get`</SwmToken> method in <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="43:4:4" line-data="public class LocalParameterMap implements ParameterMap, Serializable {">`LocalParameterMap`</SwmToken> is responsible for retrieving a parameter value based on its name. If the parameter does not exist, it returns a default value.

```java
	public String get(String parameterName, String defaultValue) {
		if (!parameters.containsKey(parameterName)) {
			return defaultValue;
		}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="122">

---

Next, if the parameter exists, the method checks if the value is an array. If it is, it validates that the array contains strings and returns the first element of the array.

```java
		Object value = parameters.get(parameterName);
		if (value.getClass().isArray()) {
			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);
			String[] array = (String[]) value;
			if (array.length == 0) {
				return null;
			} else {
				Object first = ((String[]) value)[0];
				parameterAccessor.assertKeyValueInstanceOf(parameterName, first, String.class);
				return (String) first;
			}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" line="133">

---

If the value is not an array, it validates that the value is a string and returns it.

```java

		} else {
			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String.class);
			return (String) value;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" line="52">

---

Moving to the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="52:5:5" line-data="	public boolean containsKey(Object key) {">`containsKey`</SwmToken> method in <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/SharedMapDecorator.java" pos="31:4:4" line-data="public class SharedMapDecorator&lt;K, V&gt; implements SharedMap&lt;K, V&gt;, Serializable {">`SharedMapDecorator`</SwmToken>, it checks if a specific key exists in the map, which is crucial for determining the presence of parameters before attempting to retrieve them.

```java
	public boolean containsKey(Object key) {
		return map.containsKey(key);
	}
```

---

</SwmSnippet>

## Looking at <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="124:3:3" line-data="			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);">`assertKeyValueInstanceOf`</SwmToken> & <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/MapAccessor.java" pos="429:9:9" line-data="					+ value.getClass().getName() + &quot;]&quot;);">`getName`</SwmToken>

```mermaid
graph TD
  subgraph assertKeyValueInstanceOf
    assertKeyValueInstanceOf:A["Check if required type is not null"] --> assertKeyValueInstanceOf:B["Check if value is not null and not instance of required type"]
    assertKeyValueInstanceOf:B -->|True| assertKeyValueInstanceOf:C["Throw IllegalArgumentException"]
    assertKeyValueInstanceOf:B -->|False| assertKeyValueInstanceOf:D["Return value"]
  end
  subgraph getName
    getName:A["Return the variable name"]
  end

%% Swimm:
%% graph TD
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="124:3:3" line-data="			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);">`assertKeyValueInstanceOf`</SwmToken>
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="124:3:3" line-data="			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);">`assertKeyValueInstanceOf`</SwmToken>:A["Check if required type is not null"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="124:3:3" line-data="			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);">`assertKeyValueInstanceOf`</SwmToken>:B["Check if value is not null and not instance of required type"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="124:3:3" line-data="			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);">`assertKeyValueInstanceOf`</SwmToken>:B -->|True| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="124:3:3" line-data="			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);">`assertKeyValueInstanceOf`</SwmToken>:C["Throw <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/MapAccessor.java" pos="427:5:5" line-data="			throw new IllegalArgumentException(&quot;Map key &#39;&quot; + key + &quot;&#39; has value [&quot; + value">`IllegalArgumentException`</SwmToken>"]
%%     <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="124:3:3" line-data="			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);">`assertKeyValueInstanceOf`</SwmToken>:B -->|False| <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/core/collection/LocalParameterMap.java" pos="124:3:3" line-data="			parameterAccessor.assertKeyValueInstanceOf(parameterName, value, String[].class);">`assertKeyValueInstanceOf`</SwmToken>:D["Return value"]
%%   end
%%   subgraph <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/MapAccessor.java" pos="429:9:9" line-data="					+ value.getClass().getName() + &quot;]&quot;);">`getName`</SwmToken>
%%     <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/MapAccessor.java" pos="429:9:9" line-data="					+ value.getClass().getName() + &quot;]&quot;);">`getName`</SwmToken>:A["Return the variable name"]
%%   end
```

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/collection/MapAccessor.java" line="416">

---

First, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/MapAccessor.java" pos="424:9:9" line-data="	public &lt;T&gt; T assertKeyValueInstanceOf(Object key, Object value, Class&lt;T&gt; requiredType) {">`assertKeyValueInstanceOf`</SwmToken> method ensures that the value associated with a given key is of the required type. This validation is crucial for maintaining data integrity and preventing type-related errors during runtime. If the value is not of the expected type, an <SwmToken path="spring-binding/src/main/java/org/springframework/binding/collection/MapAccessor.java" pos="427:5:5" line-data="			throw new IllegalArgumentException(&quot;Map key &#39;&quot; + key + &quot;&#39; has value [&quot; + value">`IllegalArgumentException`</SwmToken> is thrown, providing a clear error message that includes the key, the incorrect value, and the expected type.

```java
	/**
	 * Assert that the key value, if non null, is an instance of the required type.
	 * @param key the key
	 * @param value the value
	 * @param requiredType the required type
	 * @return the value
	 */
	@SuppressWarnings("unchecked")
	public <T> T assertKeyValueInstanceOf(Object key, Object value, Class<T> requiredType) {
		Assert.notNull(requiredType, "The required type to assert is required");
		if (value != null && !requiredType.isInstance(value)) {
			throw new IllegalArgumentException("Map key '" + key + "' has value [" + value
					+ "] that is not of expected type [" + requiredType + "], instead it is of type ["
					+ value.getClass().getName() + "]");
		}
		return (T) value;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" line="51">

---

Next, the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="55:5:5" line-data="	public String getName() {">`getName`</SwmToken> method in the <SwmToken path="spring-binding/src/main/java/org/springframework/binding/expression/ExpressionVariable.java" pos="24:4:4" line-data="public class ExpressionVariable {">`ExpressionVariable`</SwmToken> class is used to retrieve the name of a variable. This method simply returns the name of the variable, which is essential for identifying and referencing variables within expressions. This functionality supports the dynamic evaluation of expressions by providing a way to access variable names programmatically.

```java
	/**
	 * Returns the variable name.
	 * @return the variable name
	 */
	public String getName() {
		return name;
	}
```

---

</SwmSnippet>

## Zooming into <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken> & <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="111:9:9" line-data="			throw new FlowDefinitionConstructionException(assembler.getFlowBuilderContext().getFlowId(), e);">`getFlowBuilderContext`</SwmToken> & <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="111:13:13" line-data="			throw new FlowDefinitionConstructionException(assembler.getFlowBuilderContext().getFlowId(), e);">`getFlowId`</SwmToken>

```mermaid
graph TD
  subgraph assembleFlow
  assembleFlow:A["Set assembling to true"] --> assembleFlow:B["Call assembler.assembleFlow"]
  assembleFlow:C["Call assembler.getFlowBuilderContext"] --> assembleFlow:D["Throw FlowDefinitionConstructionException"]
  assembleFlow:E["Set assembling to false"]
  assembleFlow:B --> assembleFlow:C
  assembleFlow:C --> assembleFlow:D
  assembleFlow:D --> assembleFlow:E
  assembleFlow:B --> assembleFlow:E
  end
  subgraph getFlowBuilderContext
  getFlowBuilderContext:A["Return flowBuilderContext"]
  end
  subgraph getFlowId
  getFlowId:A["Return parent.getFlowId"]
  end
  assembleFlow:C --> getFlowBuilderContext

%% Swimm:
%% graph TD
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:A["Set assembling to true"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:B["Call <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="109:5:7" line-data="			flowDefinition = assembler.assembleFlow();">`assembler.assembleFlow`</SwmToken>"]
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:C["Call <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="111:7:9" line-data="			throw new FlowDefinitionConstructionException(assembler.getFlowBuilderContext().getFlowId(), e);">`assembler.getFlowBuilderContext`</SwmToken>"] --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:D["Throw <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="77:13:13" line-data="	public synchronized FlowDefinition getFlowDefinition() throws FlowDefinitionConstructionException {">`FlowDefinitionConstructionException`</SwmToken>"]
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:E["Set assembling to false"]
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:B --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:C
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:C --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:D
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:D --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:E
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:B --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:E
%%   end
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="111:9:9" line-data="			throw new FlowDefinitionConstructionException(assembler.getFlowBuilderContext().getFlowId(), e);">`getFlowBuilderContext`</SwmToken>
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="111:9:9" line-data="			throw new FlowDefinitionConstructionException(assembler.getFlowBuilderContext().getFlowId(), e);">`getFlowBuilderContext`</SwmToken>:A["Return <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="75:3:3" line-data="		return flowBuilderContext;">`flowBuilderContext`</SwmToken>"]
%%   end
%%   subgraph <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="111:13:13" line-data="			throw new FlowDefinitionConstructionException(assembler.getFlowBuilderContext().getFlowId(), e);">`getFlowId`</SwmToken>
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="111:13:13" line-data="			throw new FlowDefinitionConstructionException(assembler.getFlowBuilderContext().getFlowId(), e);">`getFlowId`</SwmToken>:A["Return <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/LocalFlowBuilderContext.java" pos="51:3:5" line-data="		return parent.getFlowId();">`parent.getFlowId`</SwmToken>"]
%%   end
%%   <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="84:1:1" line-data="			assembleFlow();">`assembleFlow`</SwmToken>:C --> <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="111:9:9" line-data="			throw new FlowDefinitionConstructionException(assembler.getFlowBuilderContext().getFlowId(), e);">`getFlowBuilderContext`</SwmToken>
```

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" line="106">

---

First, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="106:5:5" line-data="	private void assembleFlow() throws FlowDefinitionConstructionException {">`assembleFlow`</SwmToken> method is responsible for assembling the flow definition. This method sets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="108:1:1" line-data="			assembling = true;">`assembling`</SwmToken> flag to true, indicating that the flow assembly process is in progress. It then calls the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="106:5:5" line-data="	private void assembleFlow() throws FlowDefinitionConstructionException {">`assembleFlow`</SwmToken> method on the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="109:5:5" line-data="			flowDefinition = assembler.assembleFlow();">`assembler`</SwmToken> object to construct the flow definition. If an exception occurs during this process, it catches the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="110:6:6" line-data="		} catch (FlowBuilderException e) {">`FlowBuilderException`</SwmToken> and throws a <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="106:11:11" line-data="	private void assembleFlow() throws FlowDefinitionConstructionException {">`FlowDefinitionConstructionException`</SwmToken> with the flow ID and the original exception. Finally, it sets the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/DefaultFlowHolder.java" pos="108:1:1" line-data="			assembling = true;">`assembling`</SwmToken> flag back to false, indicating that the assembly process is complete.

```java
	private void assembleFlow() throws FlowDefinitionConstructionException {
		try {
			assembling = true;
			flowDefinition = assembler.assembleFlow();
		} catch (FlowBuilderException e) {
			throw new FlowDefinitionConstructionException(assembler.getFlowBuilderContext().getFlowId(), e);
		} finally {
			assembling = false;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" line="74">

---

Next, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="74:5:5" line-data="	public FlowBuilderContext getFlowBuilderContext() {">`getFlowBuilderContext`</SwmToken> method is used to retrieve the flow builder context. This context provides essential information required during the flow assembly process. The method simply returns the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/FlowAssembler.java" pos="75:3:3" line-data="		return flowBuilderContext;">`flowBuilderContext`</SwmToken> object, which contains the necessary context data.

```java
	public FlowBuilderContext getFlowBuilderContext() {
		return flowBuilderContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/LocalFlowBuilderContext.java" line="50">

---

Then, the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/LocalFlowBuilderContext.java" pos="50:5:5" line-data="	public String getFlowId() {">`getFlowId`</SwmToken> method is responsible for retrieving the flow ID. This ID uniquely identifies the flow being assembled. The method calls the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/LocalFlowBuilderContext.java" pos="50:5:5" line-data="	public String getFlowId() {">`getFlowId`</SwmToken> method on the <SwmToken path="spring-webflow/src/main/java/org/springframework/webflow/engine/builder/model/LocalFlowBuilderContext.java" pos="51:3:3" line-data="		return parent.getFlowId();">`parent`</SwmToken> object to obtain the flow ID and returns it.

```java
	public String getFlowId() {
		return parent.getFlowId();
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctZGVtbyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-demo"><sup>Powered by [Swimm](/)</sup></SwmMeta>
