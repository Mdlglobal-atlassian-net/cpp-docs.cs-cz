---
title: "Třída unbounded_buffer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
dev_langs:
- C++
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ecddf2327e3b2e29dd3c9a857227c03d9e880ef4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
`unbounded_buffer` Zasílání zpráv blok je více cíl, více zdroje, seřazených `propagator_block` umožňující ukládání bez vazby počet zpráv.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<  
   class             _Type  
>  
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Type`  
 Typ datové části zprávy uložené a rozšíří ve vyrovnávací paměti.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[unbounded_buffer](#ctor)|Přetíženo. Vytvoří `unbounded_buffer` zasílání zpráv bloku.|  
|[~unbounded_buffer Destructor](#dtor)|Zničí `unbounded_buffer` zasílání zpráv bloku.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Dequeue –](#dequeue)|Odebere položku z `unbounded_buffer` zasílání zpráv bloku.|  
|[Zařazování](#enqueue)|Přidá položku, kterou chcete `unbounded_buffer` zasílání zpráv bloku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[accept_message](#accept_message)|Přijme zprávu, která byla nabízí to `unbounded_buffer` bloku zasílání zpráv, přenos vlastnictví volajícímu.|  
|[consume_message](#consume_message)|Využívá dříve nabízené zprávy `unbounded_buffer` zasílání zpráv na úrovni bloku a rezervován cíl, přenos vlastnictví volajícímu.|  
|[link_target_notification](#link_target_notification)|Zpětné volání, které oznamuje, že nová cílová souvisel s to `unbounded_buffer` zasílání zpráv bloku.|  
|[process_input_messages](#process_input_messages)|Míst `message` `_PMessage` v tomto `unbounded_buffer` zasílání zpráv blokování a pokusí se ji na všechny propojené cíle nabízejí.|  
|[propagate_message](#propagate_message)|Asynchronně předá zprávu od `ISource` bloku k tomuto `unbounded_buffer` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.|  
|[propagate_output_messages](#propagate_output_messages)|Míst `message` `_PMessage` v tomto `unbounded_buffer` zasílání zpráv blokování a pokusí se ji na všechny propojené cíle nabízejí. (Přepisuje [source_block::propagate_output_messages –](source-block-class.md#propagate_output_messages).)|  
|[release_message](#release_message)|Uvolní předchozí zpráva rezervace. (Přepisuje [source_block::release_message –](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Rezervuje zprávu dříve nabízí to `unbounded_buffer` zasílání zpráv bloku. (Přepisuje [source_block::reserve_message –](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Obnoví šíření po vydala rezervace. (Přepisuje [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|  
|[send_message –](#send_message)|Synchronně předá zprávu od `ISource` bloku k tomuto `unbounded_buffer` zasílání zpráv bloku. Je volána, pomocí `send` metoda, když volá blok zdroje.|  
|[supports_anonymous_source](#supports_anonymous_source)|Přepsání `supports_anonymous_source` metoda indikující, že tento blok může přijmout zprávy nabízené zdroji, který není přidružený k němu. (Přepisuje [itarget::supports_anonymous_source –](itarget-class.md#supports_anonymous_source).)|  

 Další informace najdete v tématu [asynchronní bloky zpráv](../asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `unbounded_buffer`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept_message"></a> accept_message – 

 Přijme zprávu, která byla nabízí to `unbounded_buffer` bloku zasílání zpráv, přenos vlastnictví volajícímu.  
  
```  
virtual message<_Type> * accept_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
##  <a name="consume_message"></a> consume_message – 

 Využívá dříve nabízené zprávy `unbounded_buffer` zasílání zpráv na úrovni bloku a rezervován cíl, přenos vlastnictví volajícímu.  
  
```  
virtual message<_Type> * consume_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu spotřebovávanou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako `accept`, ale je vždy před voláním `reserve`.  
  
##  <a name="dequeue">Dequeue –</a> 

 Odebere položku z `unbounded_buffer` zasílání zpráv bloku.  
  
```  
_Type dequeue();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Datová část zprávy odebrán z `unbounded_buffer`.  
  
##  <a name="enqueue">Zařazování</a> 

 Přidá položku, kterou chcete `unbounded_buffer` zasílání zpráv bloku.  
  
```  
bool enqueue(  
   _Type const&                 _Item  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Item`  
 Položka k přidání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud položka byla přijata, `false` jinak.  
  
##  <a name="link_target_notification"></a> link_target_notification – 

 Zpětné volání, které oznamuje, že nová cílová souvisel s to `unbounded_buffer` zasílání zpráv bloku.  
  
```  
virtual void link_target_notification(  
   _Inout_ ITarget<_Type> *                 _PTarget  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na nově propojené cíl.  
  
##  <a name="propagate_message"></a> propagate_message – 

 Asynchronně předá zprávu od `ISource` bloku k tomuto `unbounded_buffer` zasílání zpráv bloku. Je volána, pomocí `propagate` metoda, když volá blok zdroje.  
  
```  
virtual message_status propagate_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel `message` objektu.  
  
 `_PSource`  
 Ukazatele na blok zdroje nabídky zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status](concurrency-namespace-enums.md#message_status) znamenat cíl rozhodli udělat se zprávou.  
  
##  <a name="propagate_output_messages"></a> propagate_output_messages 

 Míst `message` `_PMessage` v tomto `unbounded_buffer` zasílání zpráv blokování a pokusí se ji na všechny propojené cíle nabízejí.  
  
```  
virtual void propagate_output_messages();  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud už před následujícímu v další zprávu `unbounded_buffer`, šíření na propojené cíle nedojde, dokud všechny starší zprávy přijaty nebo využívat. První je úspěšně propojená cíle `accept` nebo `consume` zpráva trvá vlastnictví a žádné jiné cílové pak můžete získat zprávy.  
  
##  <a name="process_input_messages"></a> process_input_messages – 

 Míst `message` `_PMessage` v tomto `unbounded_buffer` zasílání zpráv blokování a pokusí se ji na všechny propojené cíle nabízejí.  
  
```  
virtual void process_input_messages(  
   _Inout_ message<_Type> *                 _PMessage  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
  
##  <a name="release_message"></a> release_message – 

 Uvolní předchozí zpráva rezervace.  
  
```  
virtual void release_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu vydán.  
  
##  <a name="reserve_message"></a> reserve_message – 

 Rezervuje zprávu dříve nabízí to `unbounded_buffer` zasílání zpráv bloku.  
  
```  
virtual bool reserve_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu je vyhrazena.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla úspěšně vyhrazené, `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Po `reserve` je volána, vrátí-li `true`, buď `consume` nebo `release` musí být volána buď trvat nebo uvolnění vlastnictví zprávy.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 Obnoví šíření po vydala rezervace.  
  
```  
virtual void resume_propagation();  
```  
  
##  <a name="send_message">send_message –</a> 

 Synchronně předá zprávu od `ISource` bloku k tomuto `unbounded_buffer` zasílání zpráv bloku. Je volána, pomocí `send` metoda, když volá blok zdroje.  
  
```  
virtual message_status send_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel `message` objektu.  
  
 `_PSource`  
 Ukazatele na blok zdroje nabídky zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status](concurrency-namespace-enums.md#message_status) znamenat cíl rozhodli udělat se zprávou.  
  
##  <a name="supports_anonymous_source"></a> supports_anonymous_source – 

 Přepsání `supports_anonymous_source` metoda indikující, že tento blok může přijmout zprávy nabízené zdroji, který není přidružený k němu.  
  
```  
virtual bool supports_anonymous_source();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` protože blok není odložit nabízené zprávy.  
  
##  <a name="ctor">unbounded_buffer</a> 

 Vytvoří `unbounded_buffer` zasílání zpráv bloku.  
  
```  
unbounded_buffer();  
  
unbounded_buffer(  
   filter_method const&                 _Filter  
);  
  
unbounded_buffer(  
   Scheduler&                 _PScheduler  
);  
  
unbounded_buffer(  
   Scheduler&                 _PScheduler,  
   filter_method const&                 _Filter  
);  
  
unbounded_buffer(  
   ScheduleGroup&                 _PScheduleGroup  
);  
  
unbounded_buffer(  
   ScheduleGroup&                 _PScheduleGroup,  
   filter_method const&                 _Filter  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter`  
 Filtr funkce, která určuje, zda mají být přijímány nabízený zprávy.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `unbounded_buffer` je naplánováno zasílání zpráv bloku.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `unbounded_buffer` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Typ `filter_method` je functor podpisem `bool (_Type const &)` který lze vyvolat to `unbounded_buffer` zasílání zpráv blok k určení, zda by měl přijímat nabízený zprávy.  
  
##  <a name="dtor"></a> ~ unbounded_buffer 

 Zničí `unbounded_buffer` zasílání zpráv bloku.  
  
```  
~unbounded_buffer();  
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Třída overwrite_buffer](overwrite-buffer-class.md)   
 [single_assignment – třída](single-assignment-class.md)


