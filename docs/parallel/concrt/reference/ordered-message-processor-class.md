---
title: ordered_message_processor – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
dev_langs:
- C++
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa27c46db5d23c78d9f433b41f27161f0bc41736
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028568"
---
# <a name="orderedmessageprocessor-class"></a>ordered_message_processor – třída
`ordered_message_processor` Je `message_processor` , která umožňuje blokům zpráv zpracovávat zprávy v pořadí, v jakém byly přijaty.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class ordered_message_processor : public message_processor<T>;
```  
  
#### <a name="parameters"></a>Parametry  
*T*<br/>
Typ datové části zprávy zpracovává procesoru.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`type`|Alias typu pro `T`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[ordered_message_processor](#ctor)|Vytvoří `ordered_message_processor` objektu.|  
|[~ ordered_message_processor – destruktor](#dtor)|Odstraní `ordered_message_processor` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[async_send](#async_send)|Asynchronně vloží do fronty zpráv a spustí úlohu zpracování, pokud to není již bylo provedeno. (Přepíše [message_processor::async_send –](message-processor-class.md#async_send).)|  
|[Inicializace](#initialize)|Inicializuje `ordered_message_processor` objekt skupinou odpovídající zpětného volání funkce, Plánovač a plán.|  
|[initialize_batched_processing](#initialize_batched_processing)|Inicializovat zpracování dávkové zprávy|  
|[sync_send](#sync_send)|Synchronně zařadí do fronty zpráv a spustí úlohu zpracování, pokud to není již bylo provedeno. (Přepíše [message_processor::sync_send –](message-processor-class.md#sync_send).)|  
|[Počkej](#wait)|Specifické pro procesor otočný čekání používané destruktory blokům zpráv, abyste měli jistotu, že všechny úlohy asynchronního zpracování dostatek času k dokončení a zničení bloku. (Přepíše [message_processor::wait –](message-processor-class.md#wait).)|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[process_incoming_message –](#process_incoming_message)|Zpracování funkce, která je volána asynchronně. Dequeues zprávy a zahájí zpracování je. (Přepíše [message_processor::process_incoming_message –](message-processor-class.md#process_incoming_message).)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [message_processor](message-processor-class.md)  
  
 `ordered_message_processor`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="async_send"></a> async_send – 

 Asynchronně vloží do fronty zpráv a spustí úlohu zpracování, pokud to není již bylo provedeno.  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
*_Msg*<br/>
Ukazatel na zprávu.  
  
##  <a name="initialize"></a> Inicializace 

 Inicializuje `ordered_message_processor` objekt skupinou odpovídající zpětného volání funkce, Plánovač a plán.  
  
```
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```  
  
### <a name="parameters"></a>Parametry  
*_PScheduler*<br/>
Ukazatel na Plánovač má být použit pro plánování úloh nižšími nároky.  
  
*_PScheduleGroup*<br/>
Ukazatel na skupinu plánu použitého pro plánování úloh nižšími nároky.  
  
*_Handler*<br/>
Obslužná rutina funktor vyvolána během zpětného volání.  
  
##  <a name="initialize_batched_processing"></a> initialize_batched_processing – 

 Inicializovat zpracování dávkové zprávy  
  
```
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```  
  
### <a name="parameters"></a>Parametry  
*_Processor*<br/>
Procesor funktor vyvolána během zpětného volání.  
  
*_Propagator*<br/>
Funktor Šiřitel vyvolána během zpětného volání.  
  
##  <a name="ctor"></a> ordered_message_processor – 

 Vytvoří `ordered_message_processor` objektu.  
  
```
ordered_message_processor();
```  
  
### <a name="remarks"></a>Poznámky  
 To `ordered_message_processor` synchronní nebo asynchronní obslužné rutiny, dokud nebude naplánovat `initialize` funkce je volána.  
  
##  <a name="dtor"></a> ~ ordered_message_processor – 

 Odstraní `ordered_message_processor` objektu.  
  
```
virtual ~ordered_message_processor();
```  
  
### <a name="remarks"></a>Poznámky  
 Čeká na všechny nevyřízené asynchronní operace před zničení procesoru.  
  
##  <a name="process_incoming_message"></a> process_incoming_message – 

 Zpracování funkce, která je volána asynchronně. Dequeues zprávy a zahájí zpracování je.  
  
```
virtual void process_incoming_message();
```  
  
##  <a name="sync_send"></a> sync_send – 

 Synchronně zařadí do fronty zpráv a spustí úlohu zpracování, pokud to není již bylo provedeno.  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
*_Msg*<br/>
Ukazatel na zprávu.  
  
##  <a name="wait"></a> Počkej 

 Specifické pro procesor otočný čekání používané destruktory blokům zpráv, abyste měli jistotu, že všechny úlohy asynchronního zpracování dostatek času k dokončení a zničení bloku.  
  
```
virtual void wait();
```  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
