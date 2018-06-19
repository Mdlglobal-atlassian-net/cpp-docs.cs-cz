---
title: Třída single_assignment | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
dev_langs:
- C++
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bacbdaa4af141101863b4d6d81d114d43aced9f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696276"
---
# <a name="singleassignment-class"></a>Třída single_assignment
A `single_assignment` zasílání zpráv blok je více cíl, více zdroje, seřazených `propagator_block` umožňující ukládání jedinou zápisu-po `message`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ datové části zprávy uložené a rozšíří ve vyrovnávací paměti.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[single_assignment](#ctor)|Přetíženo. Vytvoří `single_assignment` zasílání zpráv bloku.|  
|[~ single_assignment – destruktor](#dtor)|Zničí `single_assignment` zasílání zpráv bloku.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[has_value](#has_value)|Kontroluje, zda tato `single_assignment` zasílání zpráv bloku byl inicializován s hodnotou ještě.|  
|[value](#value)|Získá odkaz na aktuální datovou část zprávy ukládají do `single_assignment` zasílání zpráv bloku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Přijme zprávu, která byla nabízí to `single_assignment` zasílání zpráv bloku vrácením volající kopii zprávy.|  
|[consume_message –](#consume_message)|Využívá dříve nabízené zprávy `single_assignment` a vyhrazený pro cíl, vrácením volající kopii zprávy.|  
|[link_target_notification](#link_target_notification)|Zpětné volání, které oznamuje, že nová cílová souvisel s to `single_assignment` zasílání zpráv bloku.|  
|[propagate_message](#propagate_message)|Asynchronně předá zprávu od `ISource` bloku k tomuto `single_assignment` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Míst `message _PMessage` v tomto `single_assignment` zasílání zpráv na úrovni bloku a nabízí ji na všechny propojené cíle.|  
|[release_message](#release_message)|Uvolní předchozí zpráva rezervace. (Přepisuje [source_block::release_message –](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezervuje zprávu dříve nabízí to `single_assignment` zasílání zpráv bloku. (Přepisuje [source_block::reserve_message –](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Obnoví šíření po vydala rezervace. (Přepisuje [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|  
|[send_message –](#send_message)|Synchronně předá zprávu od `ISource` bloku k tomuto `single_assignment` zasílání zpráv bloku. Je volána, pomocí `send` metoda, když volá blok zdroje.|  
  
## <a name="remarks"></a>Poznámky  
 A `single_assignment` zasílání zpráv bloku šíří se kopie jeho zprávu pro každý cíl.  
  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `single_assignment`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept_message"></a> accept_message – 

 Přijme zprávu, která byla nabízí to `single_assignment` zasílání zpráv bloku vrácením volající kopii zprávy.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 `single_assignment` Zasílání zpráv na úrovni bloku kopie vrátí zprávu, která se jeho cíle, nikoli přenos vlastnictví aktuálně udržovaných zprávy.  
  
##  <a name="consume_message"></a> consume_message – 

 Využívá dříve nabízené zprávy `single_assignment` a vyhrazený pro cíl, vrácením volající kopii zprávy.  
  
```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu spotřebovávanou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako `accept`, ale je vždy před voláním `reserve`.  
  
##  <a name="has_value"></a> has_value – 

 Kontroluje, zda tato `single_assignment` zasílání zpráv bloku byl inicializován s hodnotou ještě.  
  
```
bool has_value() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud bloku byl přijat hodnotu, `false` jinak.  
  
##  <a name="link_target_notification"></a> link_target_notification – 

 Zpětné volání, které oznamuje, že nová cílová souvisel s to `single_assignment` zasílání zpráv bloku.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na nově propojené cíl.  
  
##  <a name="propagate_message"></a> propagate_message – 

 Asynchronně předá zprávu od `ISource` bloku k tomuto `single_assignment` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.  
  
```
virtual message_status propagate_message(
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

 Míst `message` `_PMessage` v tomto `single_assignment` zasílání zpráv na úrovni bloku a nabízí ji na všechny propojené cíle.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel na `message` které tento `single_assignment` převzetí vlastnictví těchto zasílání zpráv bloku.  
  
##  <a name="release_message"></a> release_message – 

 Uvolní předchozí zpráva rezervace.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu vydán.  
  
##  <a name="reserve_message"></a> reserve_message – 

 Rezervuje zprávu dříve nabízí to `single_assignment` zasílání zpráv bloku.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu je vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla úspěšně vyhrazené, `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Po `reserve` je volána, vrátí-li `true`, buď `consume` nebo `release` musí být volána buď trvat nebo uvolnění vlastnictví zprávy.  
  
##  <a name="resume_propagation"></a> resume_propagation – 

 Obnoví šíření po vydala rezervace.  
  
```
virtual void resume_propagation();
```  
  
##  <a name="send_message"></a> send_message – 

 Synchronně předá zprávu od `ISource` bloku k tomuto `single_assignment` zasílání zpráv bloku. Je volána, pomocí `send` metoda, když volá blok zdroje.  
  
```
virtual message_status send_message(
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
  
##  <a name="ctor"></a> single_assignment 

 Vytvoří `single_assignment` zasílání zpráv bloku.  
  
```
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter`  
 Filtr funkce, která určuje, zda mají být přijímány nabízený zprávy.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `single_assignment` je naplánováno zasílání zpráv bloku.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `single_assignment` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Typ `filter_method` je functor podpisem `bool (T const &)` který lze vyvolat to `single_assignment` zasílání zpráv blok k určení, zda by měl přijímat nabízený zprávy.  
  
##  <a name="dtor"></a> ~ single_assignment 

 Zničí `single_assignment` zasílání zpráv bloku.  
  
```
~single_assignment();
```  
  
##  <a name="value"></a> Hodnota 

 Získá odkaz na aktuální datovou část zprávy ukládají do `single_assignment` zasílání zpráv bloku.  
  
```
T const& value();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Datová část uložené zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda bude čekat, dokud doručení zprávy, pokud žádná zpráva je uložen v `single_assignment` zasílání zpráv bloku.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Třída overwrite_buffer](overwrite-buffer-class.md)   
 [Třída unbounded_buffer](unbounded-buffer-class.md)

