---
title: Třída Timer | Microsoft Docs
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
ms.openlocfilehash: 8372e32b408b97a6ac652b0ff2ff5cc19de69b54
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693221"
---
# <a name="timer-class"></a>Třída timer
A `timer` zasílání zpráv blok je jeden cíl `source_block` může odeslat zprávu k cíli po uplynutí zadané časové období má nebo v určitých intervalech.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ datové části zprávy výstup tohoto bloku.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Časovač](#ctor)|Přetíženo. Vytvoří `timer` zasílání zpráv blok, který bude platit danou zprávou po určité době.|  
|[~timer Destructor](#dtor)|Zničí `timer` zasílání zpráv bloku.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Pozastavení](#pause)|Zastaví `timer` zasílání zpráv bloku. Pokud je s opakováním `timer` zasílání zpráv na úrovni bloku, může být restartován následné `start()` volání. Pro bez opakování časovače, výsledkem je stejné jako `stop` volání.|  
|[Spuštění](#start)|Spustí `timer` zasílání zpráv bloku. Zadaný počet milisekund, po této je volána, se rozšíří zadanou hodnotu jako podřízené `message`.|  
|[Stop](#stop)|Zastaví `timer` zasílání zpráv bloku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Přijme zprávu, která byla nabízí to `timer` bloku zasílání zpráv, přenos vlastnictví volajícímu.|  
|[consume_message –](#consume_message)|Využívá dříve nabízené zprávy `timer` a vyhrazený pro cíl, přenos vlastnictví volajícímu.|  
|[link_target_notification](#link_target_notification)|Zpětné volání, které oznamuje, že nová cílová souvisel s to `timer` zasílání zpráv bloku.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Pokusí se nabízejí zprávu, kterou zobrazí `timer` blok k všechny propojené cíle.|  
|[release_message](#release_message)|Uvolní předchozí zpráva rezervace. (Přepisuje [source_block::release_message –](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezervuje zprávu dříve nabízí to `timer` zasílání zpráv bloku. (Přepisuje [source_block::reserve_message –](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Obnoví šíření po vydala rezervace. (Přepisuje [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ISource](isource-class.md)  
  
 [source_block](source-block-class.md)  
  
 `timer`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept_message"></a> accept_message – 

 Přijme zprávu, která byla nabízí to `timer` bloku zasílání zpráv, přenos vlastnictví volajícímu.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
##  <a name="consume_message"></a> consume_message – 

 Využívá dříve nabízené zprávy `timer` a vyhrazený pro cíl, přenos vlastnictví volajícímu.  
  
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
  
##  <a name="link_target_notification"></a> link_target_notification – 

 Zpětné volání, které oznamuje, že nová cílová souvisel s to `timer` zasílání zpráv bloku.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na nově propojené cíl.  
  
##  <a name="pause"></a> Pozastavení 

 Zastaví `timer` zasílání zpráv bloku. Pokud je s opakováním `timer` zasílání zpráv na úrovni bloku, může být restartován následné `start()` volání. Pro bez opakování časovače, výsledkem je stejné jako `stop` volání.  
  
```
void pause();
```  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets – 

 Pokusí se nabízejí zprávu, kterou zobrazí `timer` blok k všechny propojené cíle.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
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

 Rezervuje zprávu dříve nabízí to `timer` zasílání zpráv bloku.  
  
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
  
##  <a name="start"></a> Spuštění 

 Spustí `timer` zasílání zpráv bloku. Zadaný počet milisekund, po této je volána, se rozšíří zadanou hodnotu jako podřízené `message`.  
  
```
void start();
```  
  
##  <a name="stop"></a> Stop 

 Zastaví `timer` zasílání zpráv bloku.  
  
```
void stop();
```  
  
##  <a name="ctor"></a> Časovač 

 Vytvoří `timer` zasílání zpráv blok, který bude platit danou zprávou po určité době.  
  
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
 `_Ms`  
 Počet milisekund, po které musí uplynout po zavolání spustit pro zadaný zpráva, která má být rozšířeny po proudu.  
  
 `value`  
 Hodnota, která se rozšíří po proudu, když uplyne časovač.  
  
 `_PTarget`  
 Cíl, do které časovač rozšíří jeho zprávu.  
  
 `_Repeating`  
 V případě hodnoty true označuje, že časovač se aktivují pravidelně každých `_Ms` milisekundách.  
  
 `_Scheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `timer` je naplánováno zasílání zpráv bloku je naplánováno.  
  
 `_ScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `timer` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_Scheduler` nebo `_ScheduleGroup` parametry.  
  
##  <a name="dtor"></a> ~ timer 

 Zničí `timer` zasílání zpráv bloku.  
  
```
~timer();
```  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
