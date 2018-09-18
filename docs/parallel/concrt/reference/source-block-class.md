---
title: source_block – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
dev_langs:
- C++
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c73fbffa8090f5640db4f2a4d1610442e602739
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069206"
---
# <a name="sourceblock-class"></a>source_block – třída
`source_block` Třída je abstraktní základní třída pro pouze zdrojové bloky. Třída poskytuje funkce správy základní odkaz jako dobře běžné kontroly chyb.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```  
  
#### <a name="parameters"></a>Parametry  
*_TargetLinkRegistry*<br/>
Odkaz registru má být použit pro obsahující cílové odkazy.  
  
*_MessageProcessorType*<br/>
Typ procesoru pro zpracování zpráv.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`target_iterator`|Iterátor, který má procházet připojených cíle.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[source_block –](#ctor)|Vytvoří `source_block` objektu.|  
|[~ source_block – destruktor](#dtor)|Odstraní `source_block` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Přijmout](#accept)|Přijme zprávu, která byly nabízeny situace `source_block` objekt přenos vlastnictví volajícímu.|  
|[acquire_ref](#acquire_ref)|Získá počet odkazů na tomto `source_block` objektu, abyste zabránili odstranění.|  
|[využívání](#consume)|Využívá zprávu nabízely dříve v tomto `source_block` objektu a úspěšně vyhrazená v cíli, přenos vlastnictví volajícímu.|  
|[link_target](#link_target)|K této propojuje cílový blok `source_block` objektu.|  
|[Vydání verze](#release)|Uvolní předchozí vyhrazení úspěšné zprávy.|  
|[release_ref](#release_ref)|Počet odkazů v tomto vydání `source_block` objektu.|  
|[Rezervovat](#reserve)|Vyhradí zprávu nabízely dříve v tomto `source_block` objektu.|  
|[unlink_target](#unlink_target)|Cílový blok z tohoto nebude odpojen `source_block` objektu.|  
|[unlink_targets](#unlink_targets)|Zruší všechny cílové bloky z tohoto propojení `source_block` objektu. (Přepíše [isource::unlink_targets –](isource-class.md#unlink_targets).)|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Při přepisu v odvozené třídě, přijímá nabízená zpráva zdrojem. Bloky zpráv by měly přepsat tuto metodu za účelem ověření `_MsgId` a vrátit zprávu.|  
|[async_send](#async_send)|Asynchronně vloží do fronty zpráv a spustí úlohu šíření hodnoty, pokud to není již bylo provedeno|  
|[consume_message](#consume_message)|Při přepisu v odvozené třídě, využívá zprávu, která byla dříve vyhrazena.|  
|[enable_batched_processing –](#enable_batched_processing)|Umožňuje dávce zpracování pro tento blok.|  
|[initialize_source –](#initialize_source)|Inicializuje `message_propagator` v rámci této `source_block`.|  
|[link_target_notification](#link_target_notification)|Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `source_block` objektu.|  
|[process_input_messages](#process_input_messages)|Zprávy o zadávání procesu. Tím se zajistí Šiřitel bloků, které jsou odvozeny z source_block –|  
|[propagate_output_messages](#propagate_output_messages)|Šíření zpráv do cíle.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Při přepisu v odvozené třídě, rozšíří danou zprávu na některých nebo všech propojených cíle. Toto je hlavní šíření rutina pro bloky zpráv.|  
|[release_message](#release_message)|Při přepisu v odvozené třídě, uvolní předchozí rezervace zprávy.|  
|[remove_targets –](#remove_targets)|Odebere všechny cílové odkazy pro tento blok zdroje. To lze volat z destruktoru.|  
|[reserve_message](#reserve_message)|Při přepisu v odvozené třídě, vyhradí zprávu nabízely dříve v tomto `source_block` objektu.|  
|[resume_propagation](#resume_propagation)|Při přepisu v odvozené třídě, pokračuje v šíření po rezervaci byla uvolněna.|  
|[sync_send](#sync_send)|Synchronně zařadí do fronty zpráv a spustí úlohu šíření hodnoty, pokud to není již bylo provedeno.|  
|[unlink_target_notification](#unlink_target_notification)|Zpětné volání, která upozorňuje, že cíl byla odpojena z tohoto `source_block` objektu.|  
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Čeká na všechny asynchronní šíření dokončete. Tento konkrétní Šiřitel otočný čekání se používá v destruktory blokům zpráv abyste měli jistotu, že všechny asynchronní šíření dostatek času k dokončení a zničení bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Bloky zpráv by měl být odvozen z tohoto bloku výhod správy odkaz a synchronizace k dispozici touto třídou.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Isource –](isource-class.md)  
  
 `source_block`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept"></a> Přijmout 

 Přijme zprávu, která byly nabízeny situace `source_block` objekt přenos vlastnictví volajícímu.  
  
```
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.  
  
*_PTarget*<br/>
Ukazatel na cílový blok, který volá `accept` metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` volající má teď vlastnictví objektu.  
  
### <a name="remarks"></a>Poznámky  
 Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimky-li parametr `_PTarget` je `NULL`.  
  
 `accept` Metoda je volána metodou cíl, zatímco zpráva nabízí situace `ISource` bloku. Vrácený ukazatel zpráva může být jiný než ten, předán `propagate` metodu `ITarget` blokovat, pokud se tento zdroj rozhodne vytvořit kopii zprávy.  
  
##  <a name="accept_message"></a> accept_message 

 Při přepisu v odvozené třídě, přijímá nabízená zpráva zdrojem. Bloky zpráv by měly přepsat tuto metodu za účelem ověření `_MsgId` a vrátit zprávu.  
  
```
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
Identita objektu modulu runtime `message` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zprávu, která má volající nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 Převést vlastnictví, má být vrácen ukazatel na původní zprávu. Zkopírovat datovou část zprávy na údržbu ve vlastnictví musí být provedeny a vrátí.  
  
##  <a name="acquire_ref"></a> acquire_ref – 

 Získá počet odkazů na tomto `source_block` objektu, abyste zabránili odstranění.  
  
```
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který se odkazuje tento zdroj během `link_target` metody.  
  
##  <a name="async_send"></a> async_send – 

 Asynchronně vloží do fronty zpráv a spustí úlohu šíření hodnoty, pokud to není již bylo provedeno  
  
```
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
*_Msg*<br/>
Ukazatel `message` objekt asynchronně posílat.  
  
##  <a name="consume"></a> využívání 

 Využívá zprávu nabízely dříve v tomto `source_block` objektu a úspěšně vyhrazená v cíli, přenos vlastnictví volajícímu.  
  
```
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z vyhrazených `message` objektu.  
  
*_PTarget*<br/>
Ukazatel na cílový blok, který volá `consume` metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` volající má teď vlastnictví objektu.  
  
### <a name="remarks"></a>Poznámky  
 Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimky-li parametr `_PTarget` je `NULL`.  
  
 Vyvolá metodu [bad_target –](bad-target-class.md) výjimky-li parametr `_PTarget` nepředstavuje cíl, který volá `reserve`.  
  
 `consume` Metoda je podobná `accept`, ale musí vždy předcházet volání `reserve` vrácená `true`.  
  
##  <a name="consume_message"></a> consume_message 

 Při přepisu v odvozené třídě, využívá zprávu, která byla dříve vyhrazena.  
  
```
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` objektu spotřebovává.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zprávu, která má volající nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako `accept`, ale vždy předchází volání `reserve`.  
  
##  <a name="enable_batched_processing"></a> enable_batched_processing – 

 Umožňuje dávce zpracování pro tento blok.  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_source"></a> initialize_source – 

 Inicializuje `message_propagator` v rámci této `source_block`.  
  
```
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parametry  
*_PScheduler*<br/>
Plánovač má být použit pro plánování úloh.  
  
*_PScheduleGroup*<br/>
Plánu skupiny, která má být použit pro plánování úloh.  
  
##  <a name="link_target"></a> link_target – 

 K této propojuje cílový blok `source_block` objektu.  
  
```
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel na `ITarget` bloku k propojení této `source_block` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimky-li parametr `_PTarget` je `NULL`.  
  
##  <a name="link_target_notification"></a> link_target_notification – 

 Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `source_block` objektu.  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```  
  
##  <a name="process_input_messages"></a> process_input_messages – 

 Zprávy o zadávání procesu. Tím se zajistí Šiřitel bloků, které jsou odvozeny z source_block –  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.  
  
##  <a name="propagate_output_messages"></a> propagate_output_messages – 

 Šíření zpráv do cíle.  
  
```
virtual void propagate_output_messages();
```  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 Při přepisu v odvozené třídě, rozšíří danou zprávu na některých nebo všech propojených cíle. Toto je hlavní šíření rutina pro bloky zpráv.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
*_PMessage*<br/>
Ukazatel na zprávu, která má být rozšířena.  
  
##  <a name="release"></a> Vydání verze 

 Uvolní předchozí vyhrazení úspěšné zprávy.  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z vyhrazených `message` objektu.  
  
*_PTarget*<br/>
Ukazatel na cílový blok, který volá `release` metody.  
  
### <a name="remarks"></a>Poznámky  
 Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimky-li parametr `_PTarget` je `NULL`.  
  
 Vyvolá metodu [bad_target –](bad-target-class.md) výjimky-li parametr `_PTarget` nepředstavuje cíl, který volá `reserve`.  
  
##  <a name="release_message"></a> release_message 

 Při přepisu v odvozené třídě, uvolní předchozí rezervace zprávy.  
  
```
virtual void release_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` objektu se vydávají.  
  
##  <a name="release_ref"></a> release_ref – 

 Počet odkazů v tomto vydání `source_block` objektu.  
  
```
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel na cílový blok, který je volání této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je právě byl odpojen od tohoto zdroje. Zdrojový blok může uvolnit všechny prostředky, které jsou vyhrazené pro cílový blok.  
  
##  <a name="remove_targets"></a> remove_targets – 

 Odebere všechny cílové odkazy pro tento blok zdroje. To lze volat z destruktoru.  
  
```
void remove_targets();
```  
  
##  <a name="reserve"></a> Rezervovat 

 Vyhradí zprávu nabízely dříve v tomto `source_block` objektu.  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.  
  
*_PTarget*<br/>
Ukazatel na cílový blok, který volá `reserve` metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla úspěšně vyhrazené, `false` jinak. Rezervace může selhat z mnoha důvodů včetně: byla zpráva již vyhrazena nebo přijatý jiný cíl, zdroj může zamítnout rezervace a tak dále.  
  
### <a name="remarks"></a>Poznámky  
 Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimky-li parametr `_PTarget` je `NULL`.  
  
 Po zavolání `reserve`, pokud je úspěšná, musí buď volat `consume` nebo `release` aby bylo možné provést nebo vzdát vlastnictví zprávy, v uvedeném pořadí.  
  
##  <a name="reserve_message"></a> reserve_message 

 Při přepisu v odvozené třídě, vyhradí zprávu nabízely dříve v tomto `source_block` objektu.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` objekt dochází k rezervaci.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla úspěšně vyhrazené, `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Po `reserve` je volána, pokud se vrátí `true`– buď `consume` nebo `release` využít nebo uvolnit vlastnictví zprávy musí být volána.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 Při přepisu v odvozené třídě, pokračuje v šíření po rezervaci byla uvolněna.  
  
```
virtual void resume_propagation() = 0;
```  
  
##  <a name="ctor"></a> source_block – 

 Vytvoří `source_block` objektu.  
  
```
source_block();
```  
  
##  <a name="dtor"></a> ~ source_block – 

 Odstraní `source_block` objektu.  
  
```
virtual ~source_block();
```  
  
##  <a name="sync_send"></a> sync_send – 

 Synchronně zařadí do fronty zpráv a spustí úlohu šíření hodnoty, pokud to není již bylo provedeno.  
  
```
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
*_Msg*<br/>
Ukazatel `message` objekt se má poslat synchronně.  
  
##  <a name="unlink_target"></a> unlink_target – 

 Cílový blok z tohoto nebude odpojen `source_block` objektu.  
  
```
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel `ITarget` bloku se zrušit propojení z tohoto `source_block` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimky-li parametr `_PTarget` je `NULL`.  
  
##  <a name="unlink_target_notification"></a> unlink_target_notification – 

 Zpětné volání, která upozorňuje, že cíl byla odpojena z tohoto `source_block` objektu.  
  
```
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
`ITarget` Blok, který bylo zrušeno.  
  
##  <a name="unlink_targets"></a> unlink_targets – 

 Zruší všechny cílové bloky z tohoto propojení `source_block` objektu.  
  
```
virtual void unlink_targets();
```  
  
##  <a name="wait_for_outstanding_async_sends"></a> wait_for_outstanding_async_sends – 

 Čeká na všechny asynchronní šíření dokončete. Tento konkrétní Šiřitel otočný čekání se používá v destruktory blokům zpráv abyste měli jistotu, že všechny asynchronní šíření dostatek času k dokončení a zničení bloku.  
  
```
void wait_for_outstanding_async_sends();
```  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [ISource – třída](isource-class.md)
