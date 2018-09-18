---
title: Call – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 585a490ec64152a1268b7707971ea94e69bf9fbf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109714"
---
# <a name="call-class"></a>Třída call
A `call` blok zpráv je zdroj více seřazené `target_block` zadanou funkci, která vyvolá při přijímání zprávy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Parametry  
*T*<br/>
Typ datové části zprávy šířeny do tohoto bloku.  
  
*_FunctorType*<br/>
Signatura funkce, které může přijmout tento blok.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Volání](#ctor)|Přetíženo. Vytvoří `call` blok zpráv.|  
|[~ call – destruktor](#dtor)|Odstraní `call` blok zpráv.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[process_input_messages](#process_input_messages)|Provede volání funkce na vstupní zprávy.|  
|[process_message –](#process_message)|Zpracuje zprávu, která byla přijata situace `call` blok zpráv.|  
|[propagate_message](#propagate_message)|Asynchronně předává zprávy ze `ISource` bloku k tomuto `call` blok zpráv. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.|  
|[send_message](#send_message)|Synchronně předává zprávy ze `ISource` bloku k tomuto `call` blok zpráv. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.|  
|[supports_anonymous_source –](#supports_anonymous_source)|Přepsání `supports_anonymous_source` indikace, že tento blok můžete přijímat zprávy, které jsou nabízeny zdrojem, který není spojený. (Přepíše [itarget::supports_anonymous_source –](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Itarget –](itarget-class.md)  
  
 [target_block –](target-block-class.md)  
  
 `call`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="ctor"></a> Volání 

 Vytvoří `call` blok zpráv.  
  
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
*_Func*<br/>
Funkce, která bude volána pro každé přijaté zprávy.  
  
*_Filtrovat*<br/>
Funkce filtru, která určuje, zda by měl být přijat nabízené zprávy.  
  
*_PScheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `call` naplánovaný zasílání zpráv bloku.  
  
*_PScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `call` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Typ `_Call_method` je funktor s podpisem `void (T const &)` která je vyvolána situace `call` blok zpráv ke zpracování zprávy.  
  
 Typ `filter_method` je funktor s podpisem `bool (T const &)` která je vyvolána situace `call` blok zpráv k určení, zda by měla přijímat nabízená zpráva.  
  
##  <a name="dtor"></a> ~ volání 

 Odstraní `call` blok zpráv.  
  
```
~call();
```  
  
##  <a name="process_input_messages"></a> process_input_messages – 

 Provede volání funkce na vstupní zprávy.  
  
```
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.  
  
##  <a name="process_message"></a> process_message – 

 Zpracuje zprávu, která byla přijata situace `call` blok zpráv.  
  
```
virtual void process_message(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.  
  
##  <a name="propagate_message"></a> propagate_message 

 Asynchronně předává zprávy ze `ISource` bloku k tomuto `call` blok zpráv. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.  
  
```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
*_PMessage*<br/>
Ukazatel `message` objektu.  
  
*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.  
  
##  <a name="send_message"></a> send_message 

 Synchronně předává zprávy ze `ISource` bloku k tomuto `call` blok zpráv. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.  
  
```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
*_PMessage*<br/>
Ukazatel `message` objektu.  
  
*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.  
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source – 

 Přepsání `supports_anonymous_source` indikace, že tento blok můžete přijímat zprávy, které jsou nabízeny zdrojem, který není spojený.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` protože bloku není odložit nabízené zprávy.  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [transformer – třída](transformer-class.md)
