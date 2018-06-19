---
title: Call – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47f72948621e9311f05af74f75d80cd35c1deddc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689698"
---
# <a name="call-class"></a>Třída call
A `call` zasílání zpráv blok je více zdroje, seřazené `target_block` , který spustí zadaná funkce při přijímání zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ datové části zprávy rozšíří do tohoto bloku.  
  
 `_FunctorType`  
 Podpis funkce, které může přijmout tento blok.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Volání](#ctor)|Přetíženo. Vytvoří `call` zasílání zpráv bloku.|  
|[~ call – destruktor](#dtor)|Zničí `call` zasílání zpráv bloku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[process_input_messages](#process_input_messages)|Provede volání funkce na vstupní zprávy.|  
|[process_message –](#process_message)|Zpracuje zprávu, která byla přijata to `call` zasílání zpráv bloku.|  
|[propagate_message](#propagate_message)|Asynchronně předá zprávu od `ISource` bloku k tomuto `call` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.|  
|[send_message –](#send_message)|Synchronně předá zprávu od `ISource` bloku k tomuto `call` zasílání zpráv bloku. Je volána, pomocí `send` metoda, když volá blok zdroje.|  
|[supports_anonymous_source –](#supports_anonymous_source)|Přepsání `supports_anonymous_source` metoda indikující, že tento blok může přijmout zprávy nabízené zdroji, který není přidružený k němu. (Přepisuje [itarget::supports_anonymous_source –](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ITarget](itarget-class.md)  
  
 [target_block](target-block-class.md)  
  
 `call`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> Volání 

 Vytvoří `call` zasílání zpráv bloku.  
  
```
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Func`  
 Funkce, která bude volána pro každou zprávu přijala.  
  
 `_Filter`  
 Filtr funkce, která určuje, zda mají být přijímány nabízený zprávy.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `call` je naplánováno zasílání zpráv bloku.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `call` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Typ `_Call_method` je functor podpisem `void (T const &)` který lze vyvolat to `call` zasílání zpráv bloku ke zpracování zprávy.  
  
 Typ `filter_method` je functor podpisem `bool (T const &)` který lze vyvolat to `call` zasílání zpráv blok k určení, zda by měl přijímat nabízený zprávy.  
  
##  <a name="dtor"></a> ~ volání 

 Zničí `call` zasílání zpráv bloku.  
  
```
~call();
```  
  
##  <a name="process_input_messages"></a> process_input_messages – 

 Provede volání funkce na vstupní zprávy.  
  
```
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
  
##  <a name="process_message"></a> process_message – 

 Zpracuje zprávu, která byla přijata to `call` zasílání zpráv bloku.  
  
```
virtual void process_message(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel na zprávu, která má být zpracována.  
  
##  <a name="propagate_message"></a> propagate_message – 

 Asynchronně předá zprávu od `ISource` bloku k tomuto `call` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.  
  
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
  
##  <a name="send_message"></a> send_message – 

 Synchronně předá zprávu od `ISource` bloku k tomuto `call` zasílání zpráv bloku. Je volána, pomocí `send` metoda, když volá blok zdroje.  
  
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
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source – 

 Přepsání `supports_anonymous_source` metoda indikující, že tento blok může přijmout zprávy nabízené zdroji, který není přidružený k němu.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` protože blok není odložit nabízené zprávy.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [transformer – třída](transformer-class.md)
