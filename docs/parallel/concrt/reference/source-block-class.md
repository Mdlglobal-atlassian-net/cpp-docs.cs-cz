---
title: source_block – třída | Microsoft Docs
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
ms.openlocfilehash: 64b9873ef6da00b4ef0fb03e43f61fa704484389
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="sourceblock-class"></a>source_block – třída
`source_block` Třída je abstraktní základní třídu pro jen zdroj bloky. Třída poskytuje funkce správy základní odkaz jako dobře běžné chyby kontroly.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_TargetLinkRegistry`  
 Odkaz registru, který se má použít pro uložení cílové odkazy.  
  
 `_MessageProcessorType`  
 Typ procesoru pro zpracování zprávy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`target_iterator`|Iterator vás připojené cíle.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[source_block](#ctor)|Vytvoří `source_block` objektu.|  
|[~ source_block – destruktor](#dtor)|Zničí `source_block` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Přijmout](#accept)|Přijme zprávu, která byla nabízí to `source_block` objekt, přenos vlastnictví volajícímu.|  
|[acquire_ref](#acquire_ref)|Získá počet odkazů v tomto `source_block` objekt, aby se zabránilo odstranění.|  
|[Využívat](#consume)|Využívá zprávu dříve nabízí to `source_block` objektu a úspěšně rezervován cíl, přenos vlastnictví volajícímu.|  
|[link_target](#link_target)|Cílový blok odkazuje na tato `source_block` objektu.|  
|[Verze](#release)|Uvolní předchozí rezervace úspěšné zprávy.|  
|[release_ref](#release_ref)|Uvolní počet odkazů v tomto `source_block` objektu.|  
|[Rezervovat](#reserve)|Rezervuje zprávu dříve nabízí to `source_block` objektu.|  
|[unlink_target](#unlink_target)|Zruší propojení cílový blok z tohoto `source_block` objektu.|  
|[unlink_targets](#unlink_targets)|Zruší všechny bloky cílový z tohoto propojení `source_block` objektu. (Přepisuje [isource::unlink_targets –](isource-class.md#unlink_targets).)|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Při přepisu v odvozené třídě, přijme zprávu nabízený zdroj. Bloky zpráv by měly přepsat tuto metodu pro ověření `_MsgId` a vrátí zprávu.|  
|[async_send](#async_send)|Asynchronně fronty zpráv a spustí úlohu šíření, pokud to není již bylo provedeno|  
|[consume_message –](#consume_message)|Při přepisu v odvozené třídě, využívá zprávu, která byla dříve vyhrazena.|  
|[enable_batched_processing –](#enable_batched_processing)|Umožňuje zpracovat v dávce zpracování tohoto bloku.|  
|[initialize_source –](#initialize_source)|Inicializuje `message_propagator` v rámci to `source_block`.|  
|[link_target_notification](#link_target_notification)|Zpětné volání, které oznamuje, že nová cílová souvisel s to `source_block` objektu.|  
|[process_input_messages](#process_input_messages)|Zpracování vstupu zpráv. To je vhodné pro Šiřitel bloků, které jsou odvozeny od source_block|  
|[propagate_output_messages](#propagate_output_messages)|Rozšíří zprávy k cílům.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Při přepisu v odvozené třídě, rozšíří danou zprávu, která se některé nebo všechny propojené cíle. Toto je hlavní šíření rutiny pro bloky zpráv.|  
|[release_message](#release_message)|Při přepisu v odvozené třídě, uvolní předchozí zpráva rezervace.|  
|[remove_targets –](#remove_targets)|Odebere všechny odkazy cíl pro tento zdroj blok. To by měla být volána z destruktoru.|  
|[reserve_message](#reserve_message)|Při přepisu v odvozené třídě, vyhrazuje zprávu dříve nabízí to `source_block` objektu.|  
|[resume_propagation](#resume_propagation)|Při přepisu v odvozené třídě, obnoví šíření po vydala rezervace.|  
|[sync_send](#sync_send)|Synchronně fronty zpráv a spustí úlohu šíření, pokud to není již bylo provedeno.|  
|[unlink_target_notification](#unlink_target_notification)|Zpětné volání, které oznámí cíl byl odpojit z tohoto `source_block` objektu.|  
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Čeká se na všechny asynchronní šíření na dokončení. Tato konkrétní Šiřitel otočení čekání se používá v destruktory bloky zpráv k ověření, zda všechny asynchronní šíření čas na dokončení před zničení bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Bloky zpráv by měl být odvozen z tohoto bloku využívat výhod správy odkaz a synchronizace poskytuje tuto třídu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ISource](isource-class.md)  
  
 `source_block`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept"></a> Přijmout 

 Přijme zprávu, která byla nabízí to `source_block` objekt, přenos vlastnictví volajícímu.  
  
```
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `accept` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka Pokud parametr `_PTarget` je `NULL`.  
  
 `accept` Metoda je volána cíl při zprávu nabízený to `ISource` bloku. Ukazatel zpráva vrácená může být jiný než předaný do `propagate` metodu `ITarget` blokování, pokud se tento zdroj rozhodne vytvořit kopii zprávy.  
  
##  <a name="accept_message"></a> accept_message – 

 Při přepisu v odvozené třídě, přijme zprávu nabízený zdroj. Bloky zpráv by měly přepsat tuto metodu pro ověření `_MsgId` a vrátí zprávu.  
  
```
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 Identita objektu modulu runtime `message` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zprávu, která má volající teď vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 Převést vlastnictví, má být vrácen původní zprávu ukazatele. Na údržbu ve vlastnictví kopii datovou část zprávy musí být provedeny a vrátí.  
  
##  <a name="acquire_ref"></a> acquire_ref – 

 Získá počet odkazů v tomto `source_block` objekt, aby se zabránilo odstranění.  
  
```
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je propojena k tomuto zdroji během `link_target` metoda.  
  
##  <a name="async_send"></a> async_send – 

 Asynchronně fronty zpráv a spustí úlohu šíření, pokud to není již bylo provedeno  
  
```
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 Ukazatel na `message` objekt, který chcete odeslat asynchronně.  
  
##  <a name="consume"></a> Využívat 

 Využívá zprávu dříve nabízí to `source_block` objektu a úspěšně rezervován cíl, přenos vlastnictví volajícímu.  
  
```
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z vyhrazených `message` objektu.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `consume` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka Pokud parametr `_PTarget` je `NULL`.  
  
 Vyvolá metodu [bad_target](bad-target-class.md) výjimka Pokud parametr `_PTarget` nepředstavuje cíl, který volá `reserve`.  
  
 `consume` Metoda je podobná `accept`, ale musí být vždy uvedeny volání `reserve` vrácená `true`.  
  
##  <a name="consume_message"></a> consume_message – 

 Při přepisu v odvozené třídě, využívá zprávu, která byla dříve vyhrazena.  
  
```
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu spotřebovávanou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zprávu, která má volající teď vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako `accept`, ale je vždy před voláním `reserve`.  
  
##  <a name="enable_batched_processing"></a> enable_batched_processing – 

 Umožňuje zpracovat v dávce zpracování tohoto bloku.  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_source"></a> initialize_source – 

 Inicializuje `message_propagator` v rámci to `source_block`.  
  
```
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `_PScheduler`  
 Plánovač má být použit pro plánování úloh.  
  
 `_PScheduleGroup`  
 Skupina plán má být použit pro plánování úloh.  
  
##  <a name="link_target"></a> link_target – 

 Cílový blok odkazuje na tato `source_block` objektu.  
  
```
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na `ITarget` bloku propojit k tomuto `source_block` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka Pokud parametr `_PTarget` je `NULL`.  
  
##  <a name="link_target_notification"></a> link_target_notification – 

 Zpětné volání, které oznamuje, že nová cílová souvisel s to `source_block` objektu.  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```  
  
##  <a name="process_input_messages"></a> process_input_messages – 

 Zpracování vstupu zpráv. To je vhodné pro Šiřitel bloků, které jsou odvozeny od source_block  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
  
##  <a name="propagate_output_messages"></a> propagate_output_messages – 

 Rozšíří zprávy k cílům.  
  
```
virtual void propagate_output_messages();
```  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets – 

 Při přepisu v odvozené třídě, rozšíří danou zprávu, která se některé nebo všechny propojené cíle. Toto je hlavní šíření rutiny pro bloky zpráv.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel na zprávu, která má být rozšířeny.  
  
##  <a name="release"></a> Verze 

 Uvolní předchozí rezervace úspěšné zprávy.  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z vyhrazených `message` objektu.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `release` metoda.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka Pokud parametr `_PTarget` je `NULL`.  
  
 Vyvolá metodu [bad_target](bad-target-class.md) výjimka Pokud parametr `_PTarget` nepředstavuje cíl, který volá `reserve`.  
  
##  <a name="release_message"></a> release_message – 

 Při přepisu v odvozené třídě, uvolní předchozí zpráva rezervace.  
  
```
virtual void release_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu vydán.  
  
##  <a name="release_ref"></a> release_ref – 

 Uvolní počet odkazů v tomto `source_block` objektu.  
  
```
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na cílový blok, který je voláním této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je právě odpojení z tohoto zdroje. Chcete-li uvolnit všechny prostředky, které jsou vyhrazené pro cílový blok je povoleno zdrojového bloku.  
  
##  <a name="remove_targets"></a> remove_targets – 

 Odebere všechny odkazy cíl pro tento zdroj blok. To by měla být volána z destruktoru.  
  
```
void remove_targets();
```  
  
##  <a name="reserve"></a> Rezervovat 

 Rezervuje zprávu dříve nabízí to `source_block` objektu.  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `reserve` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla úspěšně vyhrazené, `false` jinak. Rezervace může selhat z mnoha důvodů, včetně: zpráva již byla vyhrazena nebo přijali jiný cíl, zdroj může odepřít rezervace a tak dále.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka Pokud parametr `_PTarget` je `NULL`.  
  
 Po zavolání metody `reserve`, pokud se aktivace podaří, musíte buď zavolat `consume` nebo `release` za účelem trvat nebo uvolňovat u sebe zprávy, v uvedeném pořadí.  
  
##  <a name="reserve_message"></a> reserve_message – 

 Při přepisu v odvozené třídě, vyhrazuje zprávu dříve nabízí to `source_block` objektu.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu je vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla úspěšně vyhrazené, `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Po `reserve` je volána, vrátí-li `true`, buď `consume` nebo `release` musí být volána buď trvat nebo uvolnění vlastnictví zprávy.  
  
##  <a name="resume_propagation"></a> resume_propagation – 

 Při přepisu v odvozené třídě, obnoví šíření po vydala rezervace.  
  
```
virtual void resume_propagation() = 0;
```  
  
##  <a name="ctor"></a> source_block 

 Vytvoří `source_block` objektu.  
  
```
source_block();
```  
  
##  <a name="dtor"></a> ~ source_block 

 Zničí `source_block` objektu.  
  
```
virtual ~source_block();
```  
  
##  <a name="sync_send"></a> sync_send – 

 Synchronně fronty zpráv a spustí úlohu šíření, pokud to není již bylo provedeno.  
  
```
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 Ukazatel na `message` objekt, který chcete odeslat synchronně.  
  
##  <a name="unlink_target"></a> unlink_target – 

 Zruší propojení cílový blok z tohoto `source_block` objektu.  
  
```
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na `ITarget` zrušení propojení z tohoto bloku `source_block` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka Pokud parametr `_PTarget` je `NULL`.  
  
##  <a name="unlink_target_notification"></a> unlink_target_notification – 

 Zpětné volání, které oznámí cíl byl odpojit z tohoto `source_block` objektu.  
  
```
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 `ITarget` Blok, který bylo zrušeno.  
  
##  <a name="unlink_targets"></a> unlink_targets – 

 Zruší všechny bloky cílový z tohoto propojení `source_block` objektu.  
  
```
virtual void unlink_targets();
```  
  
##  <a name="wait_for_outstanding_async_sends"></a> wait_for_outstanding_async_sends – 

 Čeká se na všechny asynchronní šíření na dokončení. Tato konkrétní Šiřitel otočení čekání se používá v destruktory bloky zpráv k ověření, zda všechny asynchronní šíření čas na dokončení před zničení bloku.  
  
```
void wait_for_outstanding_async_sends();
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [ISource – třída](isource-class.md)
