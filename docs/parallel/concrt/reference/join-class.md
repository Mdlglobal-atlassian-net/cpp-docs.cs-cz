---
title: "JOIN – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
dev_langs:
- C++
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ee69daa9ec5570d89d407c980e4ff20deca6360
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="join-class"></a>join – třída
A `join` zasílání zpráv blok je jeden cíl, více zdroje, seřazených `propagator_block` který kombinuje společně zprávy typu `T` z každé její zdroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```   
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ datové části zprávy připojený a rozšířit pomocí bloku.  
  
 `_Jtype`  
 Druh z `join` bloku toto je buď `greedy` nebo `non_greedy`  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[join](#ctor)|Přetíženo. Vytvoří `join` zasílání zpráv bloku.|  
|[~join Destructor](#dtor)|Zničí `join` bloku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Přijme zprávu, která byla nabízí to `join` bloku zasílání zpráv, přenos vlastnictví volajícímu.|  
|[consume_message](#consume_message)|Využívá dříve nabízené zprávy `join` zasílání zpráv na úrovni bloku a rezervován cíl, přenos vlastnictví volajícímu.|  
|[link_target_notification](#link_target_notification)|Zpětné volání, které oznamuje, že nová cílová souvisel s to `join` zasílání zpráv bloku.|  
|[propagate_message](#propagate_message)|Asynchronně předá zprávu od `ISource` bloku k tomuto `join` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Vytvoří zprávu výstup obsahujícím zprávu vstupní z každého zdroje při mít rozšíří zprávu. Odešle tento výstup zprávu pro každý z jeho cíle.|  
|[release_message](#release_message)|Uvolní předchozí zpráva rezervace. (Přepisuje [source_block::release_message –](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezervuje zprávu dříve nabízí to `join` zasílání zpráv bloku. (Přepisuje [source_block::reserve_message –](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Obnoví šíření po vydala rezervace. (Přepisuje [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `join`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept_message"></a> accept_message – 

 Přijme zprávu, která byla nabízí to `join` bloku zasílání zpráv, přenos vlastnictví volajícímu.  
  
```
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
##  <a name="consume_message"></a> consume_message – 

 Využívá dříve nabízené zprávy `join` zasílání zpráv na úrovni bloku a rezervován cíl, přenos vlastnictví volajícímu.  
  
```
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu spotřebovávanou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako `accept`, ale je vždy před voláním `reserve`.  
  
##  <a name="ctor"></a> Připojení k 

 Vytvoří `join` zasílání zpráv bloku.  
  
```
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_NumInputs`  
 Počet vstupů to `join` bloku bude možné.  
  
 `_Filter`  
 Filtr funkce, která určuje, zda mají být přijímány nabízený zprávy.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `join` je naplánováno zasílání zpráv bloku.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `join` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Typ `filter_method` je functor podpisem `bool (T const &)` který lze vyvolat to `join` zasílání zpráv blok k určení, zda by měl přijímat nabízený zprávy.  
  
##  <a name="dtor"></a> ~join 

 Zničí `join` bloku.  
  
```
~join();
```  
  
##  <a name="link_target_notification"></a> link_target_notification – 

 Zpětné volání, které oznamuje, že nová cílová souvisel s to `join` zasílání zpráv bloku.  
  
```
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```  
  
##  <a name="propagate_message"></a> propagate_message – 

 Asynchronně předá zprávu od `ISource` bloku k tomuto `join` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.  
  
```
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel `message` objektu.  
  
 `_PSource`  
 Ukazatele na blok zdroje nabídky zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status](concurrency-namespace-enums.md) znamenat cíl rozhodli udělat se zprávou.  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets – 

 Vytvoří zprávu výstup obsahujícím zprávu vstupní z každého zdroje při mít rozšíří zprávu. Odešle tento výstup zprávu pro každý z jeho cíle.  
  
```
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```  
  
##  <a name="release_message"></a> release_message – 

 Uvolní předchozí zpráva rezervace.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu vydán.  
  
##  <a name="reserve_message"></a> reserve_message – 

 Rezervuje zprávu dříve nabízí to `join` zasílání zpráv bloku.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla úspěšně vyhrazené, `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Po `reserve` je volána, vrátí-li `true`, buď `consume` nebo `release` musí být volána buď trvat nebo uvolnění vlastnictví zprávy.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 Obnoví šíření po vydala rezervace.  
  
```
virtual void resume_propagation();
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Třída Choice](choice-class.md)   
 [multitype_join – třída](multitype-join-class.md)
