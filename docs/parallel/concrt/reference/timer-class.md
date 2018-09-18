---
title: Třída Timer | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
dev_langs:
- C++
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42d77386350dab3e8714b00f8e55143b2a486e79
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091657"
---
# <a name="timer-class"></a>Třída timer
A `timer` blok zpráv je jeden cíl `source_block` schopné odesílat zprávy k cíli po uplynutí zadaného časového období se nebo v určitých intervalech.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```  
  
#### <a name="parameters"></a>Parametry  
*T*<br/>
Typ datové části výstupní zprávy z tohoto bloku.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Časovač](#ctor)|Přetíženo. Vytvoří `timer` blok zpráv, který se aktivuje danou zprávu po uplynutí zadaného intervalu.|  
|[~timer Destructor](#dtor)|Odstraní `timer` blok zpráv.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Pozastavení](#pause)|Zastaví `timer` blok zpráv. Pokud se jedná s opakováním `timer` bloku pro zasílání zpráv, může být restartován následné `start()` volání. Pro neopakujícími časovače, tato akce nemá stejný účinek jako `stop` volání.|  
|[Spuštění](#start)|Spustí `timer` blok zpráv. Zadaný počet milisekund, po této je volána, se rozšíří zadanou hodnotu jako podřízený `message`.|  
|[Stop](#stop)|Zastaví `timer` blok zpráv.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Přijme zprávu, která byly nabízeny situace `timer` blok zpráv, přenos vlastnictví volajícímu.|  
|[consume_message](#consume_message)|Využívá dříve nabízená zpráva `timer` a vyhrazená v cíli, přenos vlastnictví volajícímu.|  
|[link_target_notification](#link_target_notification)|Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `timer` blok zpráv.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Pokusí se nabízejí zprávy vytvářené `timer` blok pro všechny propojené cíle.|  
|[release_message](#release_message)|Uvolní předchozí rezervace zprávy. (Přepíše [source_block::release_message –](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Vyhradí zprávu nabízely dříve v tomto `timer` blok zpráv. (Přepíše [source_block::reserve_message –](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Obnoví šíření po rezervaci byla uvolněna. (Přepíše [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Isource –](isource-class.md)  
  
 [source_block –](source-block-class.md)  
  
 `timer`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept_message"></a> accept_message 

 Přijme zprávu, která byly nabízeny situace `timer` blok zpráv, přenos vlastnictví volajícímu.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` volající má teď vlastnictví objektu.  
  
##  <a name="consume_message"></a> consume_message 

 Využívá dříve nabízená zpráva `timer` a vyhrazená v cíli, přenos vlastnictví volajícímu.  
  
```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` objektu spotřebovává.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` volající má teď vlastnictví objektu.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako `accept`, ale vždy předchází volání `reserve`.  
  
##  <a name="link_target_notification"></a> link_target_notification – 

 Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `timer` blok zpráv.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel na nově odkazovaný cíl.  
  
##  <a name="pause"></a> Pozastavení 

 Zastaví `timer` blok zpráv. Pokud se jedná s opakováním `timer` bloku pro zasílání zpráv, může být restartován následné `start()` volání. Pro neopakujícími časovače, tato akce nemá stejný účinek jako `stop` volání.  
  
```
void pause();
```  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 Pokusí se nabízejí zprávy vytvářené `timer` blok pro všechny propojené cíle.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```  
  
##  <a name="release_message"></a> release_message 

 Uvolní předchozí rezervace zprávy.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` objektu se vydávají.  
  
##  <a name="reserve_message"></a> reserve_message 

 Vyhradí zprávu nabízely dříve v tomto `timer` blok zpráv.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` objekt dochází k rezervaci.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla úspěšně vyhrazené, `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Po `reserve` je volána, pokud se vrátí `true`– buď `consume` nebo `release` využít nebo uvolnit vlastnictví zprávy musí být volána.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 Obnoví šíření po rezervaci byla uvolněna.  
  
```
virtual void resume_propagation();
```  
  
##  <a name="start"></a> Spuštění 

 Spustí `timer` blok zpráv. Zadaný počet milisekund, po této je volána, se rozšíří zadanou hodnotu jako podřízený `message`.  
  
```
void start();
```  
  
##  <a name="stop"></a> Stop 

 Zastaví `timer` blok zpráv.  
  
```
void stop();
```  
  
##  <a name="ctor"></a> Časovač 

 Vytvoří `timer` blok zpráv, který se aktivuje danou zprávu po uplynutí zadaného intervalu.  
  
```
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```  
  
### <a name="parameters"></a>Parametry  
*_Ms*<br/>
Počet milisekund, po které musí uplynout po volání start pro určenou zprávu na směru server-klient rozšířit.  
  
*value*<br/>
Hodnota, která bude rozšířena směru server-klient, když uplyne časovač.  
  
*_PTarget*<br/>
Cíl, do kterého bude šířit časovač její zprávy.  
  
*_Repeating*<br/>
Hodnota true určuje to, že se pravidelně aktivuje časovač každý `_Ms` milisekund.  
  
*_Scheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `timer` naplánovaný zasílání zpráv bloku je naplánováno.  
  
*_ScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `timer` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_Scheduler` nebo `_ScheduleGroup` parametry.  
  
##  <a name="dtor"></a> ~ timer 

 Odstraní `timer` blok zpráv.  
  
```
~timer();
```  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
