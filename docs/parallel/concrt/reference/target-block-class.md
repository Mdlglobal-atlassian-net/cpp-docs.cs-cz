---
title: "target_block – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
dev_langs: C++
helpviewer_keywords: target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ad7ae07933a0b74e88ae3acdcc787569e9c855f7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="targetblock-class"></a>target_block – třída
`target_block` Třída je abstraktní základní třída, která poskytuje funkce správy základní odkaz a kontrola chyb pro cíl pouze blokuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_SourceLinkRegistry`  
 Odkaz registru který se má použít pro uložení zdroje odkazy.  
  
 `_MessageProcessorType`  
 Typ procesoru pro zpracování zprávy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`source_iterator`|Typ iterator pro `source_link_manager` pro tento `target_block` objektu.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[target_block](#ctor)|Vytvoří `target_block` objektu.|  
|[~ target_block – destruktor](#dtor)|Zničí `target_block` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[rozšíření](#propagate)|Asynchronně předá zprávu z bloku zdroj tento cílový blok.|  
|[Odeslat](#send)|Synchronně předá zprávu z bloku zdroj tento cílový blok.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[async_send –](#async_send)|Asynchronně odešle zprávu pro zpracování.|  
|[decline_incoming_messages –](#decline_incoming_messages)|Označuje do bloku, musí být odmítnuta nové zprávy.|  
|[enable_batched_processing –](#enable_batched_processing)|Umožňuje zpracovat v dávce zpracování tohoto bloku.|  
|[initialize_target –](#initialize_target)|Inicializuje základní objekt. Konkrétně `message_processor` objekt musí být inicializován.|  
|[link_source –](#link_source)|Blok zadaný zdroj odkazuje na tato `target_block` objektu.|  
|[process_input_messages –](#process_input_messages)|Zpracuje zprávy, které jsou přijaty jako vstupy.|  
|[process_message –](#process_message)|Při přepisu v odvozené třídě, zpracuje zprávu, která byla přijata to `target_block` objektu.|  
|[propagate_message –](#propagate_message)|Při přepisu v odvozené třídě, tato metoda asynchronně předá zprávu od `ISource` bloku k tomuto `target_block` objektu. Je volána, pomocí `propagate` metoda, když volá blok zdroje.|  
|[register_filter –](#register_filter)|Zaregistruje metodu filtru, která bude volána pro každý přijatá zpráva.|  
|[remove_sources –](#remove_sources)|Zruší všechny zdroje propojení po čekání na dokončení operací nezpracovaných asynchronní odesílání.|  
|[send_message –](#send_message)|Při přepisu v odvozené třídě, tato metoda synchronně předá zprávu od `ISource` bloku k tomuto `target_block` objektu. Je volána, pomocí `send` metoda, když volá blok zdroje.|  
|[sync_send –](#sync_send)|Synchronně odešlete zprávu pro zpracování.|  
|[unlink_source –](#unlink_source)|Zruší propojení blok zadaného zdroje. z tohoto `target_block` objektu.|  
|[unlink_sources –](#unlink_sources)|Zruší všechny bloky zdroje z tohoto propojení `target_block` objektu. (Přepisuje [itarget::unlink_sources –](itarget-class.md#unlink_sources).)|  
|[wait_for_async_sends –](#wait_for_async_sends)|Čeká se na všechny asynchronní šíření na dokončení.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ITarget](itarget-class.md)  
  
 `target_block`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="async_send"></a>async_send – 

 Asynchronně odešle zprávu pro zpracování.  
  
```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel na odesláním zprávy.  
  
##  <a name="decline_incoming_messages"></a>decline_incoming_messages – 

 Označuje do bloku, musí být odmítnuta nové zprávy.  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána destruktor zajistit nové zprávy jsou odmítnuta, když probíhá odstraňování.  
  
##  <a name="enable_batched_processing"></a>enable_batched_processing – 

 Umožňuje zpracovat v dávce zpracování tohoto bloku.  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_target"></a>initialize_target – 

 Inicializuje základní objekt. Konkrétně `message_processor` objekt musí být inicializován.  
  
```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `_PScheduler`  
 Plánovač má být použit pro plánování úloh.  
  
 `_PScheduleGroup`  
 Skupina plán má být použit pro plánování úloh.  
  
##  <a name="link_source"></a>link_source – 

 Blok zadaný zdroj odkazuje na tato `target_block` objektu.  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 Ukazatel `ISource` blok, který má být propojena.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci nelze volat přímo na `target_block` objektu. Bloky by měly být připojené pomocí `link_target` metodu `ISource` bloků, které bude vyvolán `link_source` metoda na odpovídající cíli.  
  
##  <a name="process_input_messages"></a>process_input_messages – 

 Zpracuje zprávy, které jsou přijaty jako vstupy.  
  
```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
  
##  <a name="process_message"></a>process_message – 

 Při přepisu v odvozené třídě, zpracuje zprávu, která byla přijata to `target_block` objektu.  
  
```
virtual void process_message(message<_Source_type> *);
```  
  
##  <a name="propagate"></a>rozšíření 

 Asynchronně předá zprávu z bloku zdroj tento cílový blok.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel `message` objektu.  
  
 `_PSource`  
 Ukazatele na blok zdroje nabídky zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status](concurrency-namespace-enums.md) znamenat cíl rozhodli udělat se zprávou.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_argument](../../../standard-library/invalid-argument-class.md) Pokud buď `_PMessage` nebo `_PSource` parametr `NULL`.  
  
##  <a name="propagate_message"></a>propagate_message – 

 Při přepisu v odvozené třídě, tato metoda asynchronně předá zprávu od `ISource` bloku k tomuto `target_block` objektu. Je volána, pomocí `propagate` metoda, když volá blok zdroje.  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel `message` objektu.  
  
 `_PSource`  
 Ukazatele na blok zdroje nabídky zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status](concurrency-namespace-enums.md) znamenat cíl rozhodli udělat se zprávou.  
  
##  <a name="register_filter"></a>register_filter – 

 Zaregistruje metodu filtru, která bude volána pro každý přijatá zpráva.  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter`  
 Metoda filtru.  
  
##  <a name="remove_sources"></a>remove_sources – 

 Zruší všechny zdroje propojení po čekání na dokončení operací nezpracovaných asynchronní odesílání.  
  
```
void remove_sources();
```  
  
### <a name="remarks"></a>Poznámky  
 Všechny cílové bloky by měly volat tuto rutinu v jejich destruktor odebrat zdroje.  
  
##  <a name="send"></a>Odeslat 

 Synchronně předá zprávu z bloku zdroj tento cílový blok.  
  
```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel `message` objektu.  
  
 `_PSource`  
 Ukazatele na blok zdroje nabídky zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status](concurrency-namespace-enums.md) znamenat cíl rozhodli udělat se zprávou.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_argument](../../../standard-library/invalid-argument-class.md) Pokud buď `_PMessage` nebo `_PSource` parametr `NULL`.  
  
 Pomocí `send` metoda mimo zpráva spuštění a potřebný k šíření zprávy v síti je nebezpečné a může vést k zablokování.  
  
 Když `send` vrátí zprávu buď již byla přijata a přenést do cílový blok, nebo byla zamítnuta cíle.  
  
##  <a name="send_message"></a>send_message – 

 Při přepisu v odvozené třídě, tato metoda synchronně předá zprávu od `ISource` bloku k tomuto `target_block` objektu. Je volána, pomocí `send` metoda, když volá blok zdroje.  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status](concurrency-namespace-enums.md) znamenat cíl rozhodli udělat se zprávou.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, tento blok vrátí `declined` přepsána odvozenou třídou.  
  
##  <a name="sync_send"></a>sync_send – 

 Synchronně odešlete zprávu pro zpracování.  
  
```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
 Ukazatel na odesláním zprávy.  
  
##  <a name="ctor"></a>target_block 

 Vytvoří `target_block` objektu.  
  
```
target_block();
```  
  
##  <a name="dtor"></a>~ target_block 

 Zničí `target_block` objektu.  
  
```
virtual ~target_block();
```  
  
##  <a name="unlink_source"></a>unlink_source – 

 Zruší propojení blok zadaného zdroje. z tohoto `target_block` objektu.  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 Ukazatel `ISource` blok, který se má odpojit.  
  
##  <a name="unlink_sources"></a>unlink_sources – 

 Zruší všechny bloky zdroje z tohoto propojení `target_block` objektu.  
  
```
virtual void unlink_sources();
```  
  
##  <a name="wait_for_async_sends"></a>wait_for_async_sends – 

 Čeká se na všechny asynchronní šíření na dokončení.  
  
```
void wait_for_async_sends();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se používá ve destruktory bloku zpráv zajistit, že všechny asynchronní operace mít dost času na dokončení před zničení bloku.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [ITarget – třída](itarget-class.md)
