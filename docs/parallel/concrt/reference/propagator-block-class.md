---
title: propagator_block – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
dev_langs:
- C++
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb908bf108bb3ddff375506225b9be97b2898ca5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="propagatorblock-class"></a>propagator_block – třída
`propagator_block` Třída je abstraktní základní třídu pro bloky zpráv, které jsou zdrojovém i cílovém. Kombinuje funkci i `source_block` a `target_block` třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
 public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_TargetLinkRegistry`  
 Odkaz registru který se má použít pro uložení cílové odkazy.  
  
 `_SourceLinkRegistry`  
 Odkaz registru který se má použít pro uložení zdroje odkazy.  
  
 `_MessageProcessorType`  
 Typ procesoru pro zpracování zprávy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`source_iterator`|Typ iterator pro `source_link_manager` pro tento `propagator_block`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[propagator_block](#ctor)|Vytvoří `propagator_block` objektu.|  
|[~propagator_block Destructor](#dtor)|Zničí `propagator_block` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[propagate](#propagate)|Asynchronně předá zprávu z bloku zdroj tento cílový blok.|  
|[Odeslat](#send)|Synchronně zahájí zprávu, která tento blok. Voláno rozhraním `ISource` bloku. Po dokončení této funkce bude mít zpráva již rozšíří do bloku.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[decline_incoming_messages –](#decline_incoming_messages)|Označuje do bloku, musí být odmítnuta nové zprávy.|  
|[initialize_source_and_target –](#initialize_source_and_target)|Inicializuje základní objekt. Konkrétně `message_processor` objekt musí být inicializován.|  
|[link_source –](#link_source)|Blok zadaný zdroj odkazuje na tato `propagator_block` objektu.|  
|[process_input_messages](#process_input_messages)|Zpracování vstupu zpráv. To je vhodné pro Šiřitel bloků, které jsou odvozeny od source_block (přepíše [source_block::process_input_messages –](source-block-class.md#process_input_messages).)|  
|[propagate_message](#propagate_message)|Při přepisu v odvozené třídě, tato metoda asynchronně předá zprávu od `ISource` bloku k tomuto `propagator_block` objektu. Je volána, pomocí `propagate` metoda, když volá blok zdroje.|  
|[register_filter –](#register_filter)|Zaregistruje metodu filtru, která bude volána pro všechny přijaté zprávy.|  
|[remove_network_links](#remove_network_links)|Odebere všechny zdrojové a cílové sítě odkazy z tohoto `propagator_block` objektu.|  
|[send_message –](#send_message)|Při přepisu v odvozené třídě, tato metoda synchronně předá zprávu od `ISource` bloku k tomuto `propagator_block` objektu. Je volána, pomocí `send` metoda, když volá blok zdroje.|  
|[unlink_source](#unlink_source)|Zruší propojení blok zadaného zdroje. z tohoto `propagator_block` objektu.|  
|[unlink_sources –](#unlink_sources)|Zruší všechny bloky zdroje z tohoto propojení `propagator_block` objektu. (Přepisuje [itarget::unlink_sources –](itarget-class.md#unlink_sources).)|  
  
## <a name="remarks"></a>Poznámky  
 Aby se zabránilo vícenásobná dědičnost `propagator_block` třída dědí z `source_block` – třída a `ITarget` abstraktní třídy. Většina funkcí v `target_block` třídy se replikují sem.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 `propagator_block`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="decline_incoming_messages"></a> decline_incoming_messages – 

 Označuje do bloku, musí být odmítnuta nové zprávy.  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána destruktor zajistit nové zprávy jsou odmítnuta, když probíhá odstraňování.  
  
##  <a name="initialize_source_and_target"></a> initialize_source_and_target – 

 Inicializuje základní objekt. Konkrétně `message_processor` objekt musí být inicializován.  
  
```
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `_PScheduler`  
 Plánovač má být použit pro plánování úloh.  
  
 `_PScheduleGroup`  
 Skupina plán má být použit pro plánování úloh.  
  
##  <a name="link_source"></a> link_source – 

 Blok zadaný zdroj odkazuje na tato `propagator_block` objektu.  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 Ukazatel `ISource` blok, který má být propojena.  
  
##  <a name="process_input_messages"></a> process_input_messages – 

 Zpracování vstupu zpráv. To je vhodné pro Šiřitel bloků, které jsou odvozeny od source_block  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametry  
 `_PMessage`  
  
##  <a name="propagate"></a> rozšíření 

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
 `propagate` Metoda je volána, cílový blok podle blok propojený zdroj. Se zařadí do fronty asynchronní úlohu pro zpracování zprávy, pokud už jedna není ve frontě nebo provádění.  
  
 Vyvolá metoda [invalid_argument](../../../standard-library/invalid-argument-class.md) Pokud buď `_PMessage` nebo `_PSource` parametr `NULL`.  
  
##  <a name="propagate_message"></a> propagate_message – 

 Při přepisu v odvozené třídě, tato metoda asynchronně předá zprávu od `ISource` bloku k tomuto `propagator_block` objektu. Je volána, pomocí `propagate` metoda, když volá blok zdroje.  
  
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
  
##  <a name="ctor"></a> propagator_block 

 Vytvoří `propagator_block` objektu.  
  
```
propagator_block();
```  
  
##  <a name="dtor"></a> ~ propagator_block 

 Zničí `propagator_block` objektu.  
  
```
virtual ~propagator_block();
```  
  
##  <a name="register_filter"></a> register_filter – 

 Zaregistruje metodu filtru, která bude volána pro všechny přijaté zprávy.  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter`  
 Metoda filtru.  
  
##  <a name="remove_network_links"></a> remove_network_links – 

 Odebere všechny zdrojové a cílové sítě odkazy z tohoto `propagator_block` objektu.  
  
```
void remove_network_links();
```  
  
##  <a name="send"></a> Odeslat 

 Synchronně zahájí zprávu, která tento blok. Voláno rozhraním `ISource` bloku. Po dokončení této funkce bude mít zpráva již rozšíří do bloku.  
  
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
 Tato metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) Pokud buď `_PMessage` nebo `_PSource` parametr `NULL`.  
  
##  <a name="send_message"></a> send_message – 

 Při přepisu v odvozené třídě, tato metoda synchronně předá zprávu od `ISource` bloku k tomuto `propagator_block` objektu. Je volána, pomocí `send` metoda, když volá blok zdroje.  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [message_status](concurrency-namespace-enums.md) znamenat cíl rozhodli udělat se zprávou.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, tento blok vrátí `declined` přepsána odvozenou třídou.  
  
##  <a name="unlink_source"></a> unlink_source – 

 Zruší propojení blok zadaného zdroje. z tohoto `propagator_block` objektu.  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 Ukazatel `ISource` blok, který se má odpojit.  
  
##  <a name="unlink_sources"></a> unlink_sources – 

 Zruší všechny bloky zdroje z tohoto propojení `propagator_block` objektu.  
  
```
virtual void unlink_sources();
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [source_block – třída](source-block-class.md)   
 [ITarget – třída](itarget-class.md)
