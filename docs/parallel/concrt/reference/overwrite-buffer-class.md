---
title: Třída overwrite_buffer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- overwrite_buffer
- AGENTS/concurrency::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::has_value
- AGENTS/concurrency::overwrite_buffer::value
- AGENTS/concurrency::overwrite_buffer::accept_message
- AGENTS/concurrency::overwrite_buffer::consume_message
- AGENTS/concurrency::overwrite_buffer::link_target_notification
- AGENTS/concurrency::overwrite_buffer::propagate_message
- AGENTS/concurrency::overwrite_buffer::propagate_to_any_targets
- AGENTS/concurrency::overwrite_buffer::release_message
- AGENTS/concurrency::overwrite_buffer::reserve_message
- AGENTS/concurrency::overwrite_buffer::resume_propagation
- AGENTS/concurrency::overwrite_buffer::send_message
- AGENTS/concurrency::overwrite_buffer::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dccde651898bf5ff0986dc2e577a1d2ee5765e3f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="overwritebuffer-class"></a>Třída overwrite_buffer
`overwrite_buffer` Zasílání zpráv blok je více cíl, více zdroje, seřazených `propagator_block` umožňující ukládání do jedné zprávy najednou. Nové zprávy přepsat dříve udržovaných ty.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ datové části zprávy uložené a rozšíří ve vyrovnávací paměti.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[overwrite_buffer](#ctor)|Přetíženo. Vytvoří `overwrite_buffer` zasílání zpráv bloku.|  
|[~ overwrite_buffer – destruktor](#dtor)|Zničí `overwrite_buffer` zasílání zpráv bloku.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[has_value](#has_value)|Kontroluje, zda tato `overwrite_buffer` zasílání zpráv bloku ještě má hodnotu.|  
|[value](#value)|Získá odkaz na aktuální datovou část zprávy ukládají do `overwrite_buffer` zasílání zpráv bloku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Přijme zprávu, která byla nabízí to `overwrite_buffer` zasílání zpráv bloku vrácením volající kopii zprávy.|  
|[consume_message –](#consume_message)|Využívá dříve nabízené zprávy `overwrite_buffer` zasílání zpráv na úrovni bloku a rezervován cíl, vrácením volající kopii zprávy.|  
|[link_target_notification](#link_target_notification)|Zpětné volání, které oznamuje, že nová cílová souvisel s to `overwrite_buffer` zasílání zpráv bloku.|  
|[propagate_message](#propagate_message)|Asynchronně předá zprávu od `ISource` bloku k tomuto `overwrite_buffer` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Míst `message _PMessage` v tomto `overwrite_buffer` zasílání zpráv na úrovni bloku a nabízí ji na všechny propojené cíle.|  
|[release_message](#release_message)|Uvolní předchozí zpráva rezervace. (Přepisuje [source_block::release_message –](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezervuje zprávu dříve nabízí to `overwrite_buffer` zasílání zpráv bloku. (Přepisuje [source_block::reserve_message –](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Obnoví šíření po vydala rezervace. (Přepisuje [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|  
|[send_message –](#send_message)|Synchronně předá zprávu od `ISource` bloku k tomuto `overwrite_buffer` zasílání zpráv bloku. Je volána, pomocí `send` metoda, když volá blok zdroje.|  
|[supports_anonymous_source –](#supports_anonymous_source)|Přepsání `supports_anonymous_source` metoda indikující, že tento blok může přijmout zprávy nabízené zdroji, který není přidružený k němu. (Přepisuje [itarget::supports_anonymous_source –](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Poznámky  
 `overwrite_buffer` Zasílání zpráv bloku šíří se kopie jeho uložené zprávy pro každý z jeho cíle.  
  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `overwrite_buffer`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept_message"></a> accept_message – 

 Přijme zprávu, která byla nabízí to `overwrite_buffer` zasílání zpráv bloku vrácením volající kopii zprávy.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 `overwrite_buffer` Zasílání zpráv na úrovni bloku kopie vrátí zprávu, která se jeho cíle, nikoli přenos vlastnictví aktuálně udržovaných zprávy.  
  
##  <a name="consume_message"></a> consume_message – 

 Využívá dříve nabízené zprávy `overwrite_buffer` zasílání zpráv na úrovni bloku a rezervován cíl, vrácením volající kopii zprávy.  
  
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

 Kontroluje, zda tato `overwrite_buffer` zasílání zpráv bloku ještě má hodnotu.  
  
```
bool has_value() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud bloku byl přijat hodnotu, `false` jinak.  
  
##  <a name="link_target_notification"></a> link_target_notification – 

 Zpětné volání, které oznamuje, že nová cílová souvisel s to `overwrite_buffer` zasílání zpráv bloku.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na nově propojené cíl.  
  
##  <a name="dtor"></a> ~ overwrite_buffer 

 Zničí `overwrite_buffer` zasílání zpráv bloku.  
  
```
~overwrite_buffer();
```  
  
##  <a name="ctor"></a> overwrite_buffer 

 Vytvoří `overwrite_buffer` zasílání zpráv bloku.  
  
```
overwrite_buffer();

overwrite_buffer(
    filter_method const& _Filter);

overwrite_buffer(
    Scheduler& _PScheduler);

overwrite_buffer(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter`  
 Filtr funkce, která určuje, zda mají být přijímány nabízený zprávy.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `overwrite_buffer` je naplánováno zasílání zpráv bloku.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `overwrite_buffer` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Typ `filter_method` je functor podpisem `bool (T const &)` který lze vyvolat to `overwrite_buffer` zasílání zpráv blok k určení, zda by měl přijímat nabízený zprávy.  
  
##  <a name="propagate_message"></a> propagate_message – 

 Asynchronně předá zprávu od `ISource` bloku k tomuto `overwrite_buffer` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.  
  
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

 Míst `message _PMessage` v tomto `overwrite_buffer` zasílání zpráv na úrovni bloku a nabízí ji na všechny propojené cíle.  
  
```
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel `message` objekt které tento `overwrite_buffer` převzetí vlastnictví těchto.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepíše aktuální zprávu ve `overwrite_buffer` s nově přijaté zprávy `_PMessage`.  
  
##  <a name="send_message"></a> send_message – 

 Synchronně předá zprávu od `ISource` bloku k tomuto `overwrite_buffer` zasílání zpráv bloku. Je volána, pomocí `send` metoda, když volá blok zdroje.  
  
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
  
##  <a name="release_message"></a> release_message – 

 Uvolní předchozí zpráva rezervace.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu vydán.  
  
##  <a name="reserve_message"></a> reserve_message – 

 Rezervuje zprávu dříve nabízí to `overwrite_buffer` zasílání zpráv bloku.  
  
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
  
##  <a name="value"></a> Hodnota 

 Získá odkaz na aktuální datovou část zprávy ukládají do `overwrite_buffer` zasílání zpráv bloku.  
  
```
T value();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Datová část aktuálně uložené zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota uložená v `overwrite_buffer` ihned po návratu tato metoda se mohou změnit. Tato metoda bude čekat, dokud doručení zprávy, pokud žádná zpráva je uložen v `overwrite_buffer`.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Třída unbounded_buffer](unbounded-buffer-class.md)   
 [single_assignment – třída](single-assignment-class.md)
