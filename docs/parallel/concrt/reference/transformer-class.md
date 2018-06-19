---
title: Třída Transformer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac9ea43e1d3f6f369b93e92e91fa3606cf7d6af5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693777"
---
# <a name="transformer-class"></a>Třída transformer
A `transformer` zasílání zpráv blok je jeden cíl, více zdroje, seřazených `propagator_block` který může přijmout zprávy jednoho typu a je schopný ukládání bez vazby počet zpráv jiného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```   
  
#### <a name="parameters"></a>Parametry  
 `_Input`  
 Typ datové části zprávy přijímat vyrovnávací paměti.  
  
 `_Output`  
 Typ datové části zprávy uložené a rozšíří na ve vyrovnávací paměti.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Transformer](#ctor)|Přetíženo. Vytvoří `transformer` zasílání zpráv bloku.|  
|[~transformer Destructor](#dtor)|Zničí `transformer` zasílání zpráv bloku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Přijme zprávu, která byla nabízí to `transformer` bloku zasílání zpráv, přenos vlastnictví volajícímu.|  
|[consume_message –](#consume_message)|Využívá dříve nabízené zprávy `transformer` a vyhrazený pro cíl, přenos vlastnictví volajícímu.|  
|[link_target_notification](#link_target_notification)|Zpětné volání, které oznamuje, že nová cílová souvisel s to `transformer` zasílání zpráv bloku.|  
|[propagate_message](#propagate_message)|Asynchronně předá zprávu od `ISource` bloku k tomuto `transformer` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Provede funkci transformer na vstupní zprávy.|  
|[release_message](#release_message)|Uvolní předchozí zpráva rezervace. (Přepisuje [source_block::release_message –](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezervuje zprávu dříve nabízí to `transformer` zasílání zpráv bloku. (Přepisuje [source_block::reserve_message –](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Obnoví šíření po vydala rezervace. (Přepisuje [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|  
|[send_message –](#send_message)|Synchronně předá zprávu od `ISource` bloku k tomuto `transformer` zasílání zpráv bloku. Je volána, pomocí `send` metoda, když volá blok zdroje.|  
|[supports_anonymous_source –](#supports_anonymous_source)|Přepsání `supports_anonymous_source` metoda indikující, že tento blok může přijmout zprávy nabízené zdroji, který není přidružený k němu. (Přepisuje [itarget::supports_anonymous_source –](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `transformer`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept_message"></a> accept_message – 

 Přijme zprávu, která byla nabízí to `transformer` bloku zasílání zpráv, přenos vlastnictví volajícímu.  
  
```
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
##  <a name="consume_message"></a> consume_message – 

 Využívá dříve nabízené zprávy `transformer` a vyhrazený pro cíl, přenos vlastnictví volajícímu.  
  
```
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu spotřebovávanou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako `accept`, ale je vždy před voláním `reserve`.  
  
##  <a name="link_target_notification"></a> link_target_notification – 

 Zpětné volání, které oznamuje, že nová cílová souvisel s to `transformer` zasílání zpráv bloku.  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```  
  
##  <a name="propagate_message"></a> propagate_message – 

 Asynchronně předá zprávu od `ISource` bloku k tomuto `transformer` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel `message` objektu.  
  
 `_PSource`  
 Ukazatele na blok zdroje nabídky zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status](concurrency-namespace-enums.md) znamenat cíl rozhodli udělat se zprávou.  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets – 

 Provede funkci transformer na vstupní zprávy.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
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

 Rezervuje zprávu dříve nabízí to `transformer` zasílání zpráv bloku.  
  
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

 Synchronně předá zprávu od `ISource` bloku k tomuto `transformer` zasílání zpráv bloku. Je volána, pomocí `send` metoda, když volá blok zdroje.  
  
```
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
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
  
##  <a name="ctor"></a> Transformer 

 Vytvoří `transformer` zasílání zpráv bloku.  
  
```
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Func`  
 Funkce, která bude volána pro každou zprávu přijala.  
  
 `_PTarget`  
 Ukazatel na cílový blok pro propojení transformer.  
  
 `_Filter`  
 Filtr funkce, která určuje, zda mají být přijímány nabízený zprávy.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `transformer` je naplánováno zasílání zpráv bloku.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `transformer` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Typ `_Transform_method` je functor podpisem `_Output (_Input const &)` který lze vyvolat to `transformer` zasílání zpráv bloku ke zpracování zprávy.  
  
 Typ `filter_method` je functor podpisem `bool (_Input const &)` který lze vyvolat to `transformer` zasílání zpráv blok k určení, zda by měl přijímat nabízený zprávy.  
  
##  <a name="dtor"></a> ~ transformer 

 Zničí `transformer` zasílání zpráv bloku.  
  
```
~transformer();
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [call – třída](call-class.md)
