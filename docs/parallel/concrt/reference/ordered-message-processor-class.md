---
title: ordered_message_processor – třída | Microsoft Docs
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
ms.openlocfilehash: 27dfb6c1a64d3a4e9df24f3966ec89db1dfbe10c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="orderedmessageprocessor-class"></a>ordered_message_processor – třída
`ordered_message_processor` Je `message_processor` umožňuje bloky zpráv ke zpracování zpráv v pořadí, které byly přijaty.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class ordered_message_processor : public message_processor<T>;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ datové části zprávy zpracovávaných procesoru.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`type`|Typ aliasu pro `T`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[ordered_message_processor](#ctor)|Vytvoří `ordered_message_processor` objektu.|  
|[~ ordered_message_processor – destruktor](#dtor)|Zničí `ordered_message_processor` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[async_send](#async_send)|Asynchronně fronty zpráv a spustí úlohu zpracování, pokud to není již bylo provedeno. (Přepisuje [message_processor::async_send –](message-processor-class.md#async_send).)|  
|[Inicializace](#initialize)|Inicializuje `ordered_message_processor` objekt ke skupině odpovídající zpětného volání funkce, Plánovač a plán.|  
|[initialize_batched_processing](#initialize_batched_processing)|Inicializace zpracování dávkové zprávy|  
|[sync_send](#sync_send)|Synchronně fronty zpráv a spustí úlohu zpracování, pokud to není již bylo provedeno. (Přepisuje [message_processor::sync_send –](message-processor-class.md#sync_send).)|  
|[Počkej](#wait)|Specifické pro procesor otočení čekání, který používá v destruktorech bloky zpráv a ujistěte se, že všechny úlohy asynchronního zpracování mají čas na dokončení před zničení bloku. (Přepisuje [message_processor::wait –](message-processor-class.md#wait).)|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[process_incoming_message –](#process_incoming_message)|Zpracování funkce, která je volána asynchronně. To dequeues zprávy a zahájí zpracování je. (Přepisuje [message_processor::process_incoming_message –](message-processor-class.md#process_incoming_message).)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [message_processor](message-processor-class.md)  
  
 `ordered_message_processor`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="async_send"></a> async_send – 

 Asynchronně fronty zpráv a spustí úlohu zpracování, pokud to není již bylo provedeno.  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 Ukazatel na zprávu.  
  
##  <a name="initialize"></a> Inicializace 

 Inicializuje `ordered_message_processor` objekt ke skupině odpovídající zpětného volání funkce, Plánovač a plán.  
  
```
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```  
  
### <a name="parameters"></a>Parametry  
 `_PScheduler`  
 Ukazatel na Plánovač má být použit pro plánování šedé – úlohy.  
  
 `_PScheduleGroup`  
 Ukazatel na skupinu plánu, který má být použit pro plánování úloh šedé –.  
  
 `_Handler`  
 Obslužná rutina functor, vyvolá se během zpětného volání.  
  
##  <a name="initialize_batched_processing"></a> initialize_batched_processing – 

 Inicializace zpracování dávkové zprávy  
  
```
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```  
  
### <a name="parameters"></a>Parametry  
 `_Processor`  
 Procesor functor, vyvolá se během zpětného volání.  
  
 `_Propagator`  
 Šiřitel functor, vyvolá se během zpětného volání.  
  
##  <a name="ctor"></a> ordered_message_processor 

 Vytvoří `ordered_message_processor` objektu.  
  
```
ordered_message_processor();
```  
  
### <a name="remarks"></a>Poznámky  
 To `ordered_message_processor` synchronní nebo asynchronní obslužné rutiny, dokud nebude naplánovat `initialize` funkce je volána.  
  
##  <a name="dtor"></a> ~ ordered_message_processor 

 Zničí `ordered_message_processor` objektu.  
  
```
virtual ~ordered_message_processor();
```  
  
### <a name="remarks"></a>Poznámky  
 Čeká na všech zbývajících asynchronních operací před zničení procesoru.  
  
##  <a name="process_incoming_message"></a> process_incoming_message – 

 Zpracování funkce, která je volána asynchronně. To dequeues zprávy a zahájí zpracování je.  
  
```
virtual void process_incoming_message();
```  
  
##  <a name="sync_send"></a> sync_send – 

 Synchronně fronty zpráv a spustí úlohu zpracování, pokud to není již bylo provedeno.  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```  
  
### <a name="parameters"></a>Parametry  
 `_Msg`  
 Ukazatel na zprávu.  
  
##  <a name="wait"></a> Počkej 

 Specifické pro procesor otočení čekání, který používá v destruktorech bloky zpráv a ujistěte se, že všechny úlohy asynchronního zpracování mají čas na dokončení před zničení bloku.  
  
```
virtual void wait();
```  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
