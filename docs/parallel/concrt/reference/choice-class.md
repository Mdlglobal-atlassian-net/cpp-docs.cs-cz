---
title: "Třída Choice | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
dev_langs: C++
helpviewer_keywords: choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0466b374869ac34c56f58c94111c1738980286a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="choice-class"></a>Třída choice
A `choice` zasílání zpráv blok je více zdroje, jeden cílový blok, který představuje tok řízení interakci s sadu zdrojů. Výběr bloku bude čekat na některém z více zdrojů pro vytvoření zprávy a rozšíří index zdroje, který vytváří zprávu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<
    class T  
>  
class choice: public ISource<size_t>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 A `tuple`– na základě typu představující datových částí vstupního zdroje.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`type`|Typ aliasu pro `T`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Volba](#ctor)|Přetíženo. Vytvoří `choice` zasílání zpráv bloku.|  
|[~ choice – destruktor](#dtor)|Zničí `choice` zasílání zpráv bloku.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[přijmout](#accept)|Přijme zprávu, která byla nabízí to `choice` bloku, přenos vlastnictví volajícímu.|  
|[acquire_ref –](#acquire_ref)|Získá počet odkazů v tomto `choice` zasílání zpráv bloku, aby se zabránilo odstranění.|  
|[využívat](#consume)|Využívá zprávu dříve nabízí to `choice` zasílání zpráv na úrovni bloku a úspěšně rezervován cíl, přenos vlastnictví volajícímu.|  
|[has_value –](#has_value)|Kontroluje, zda tato `choice` zasílání zpráv bloku byl inicializován s hodnotou ještě.|  
|[index](#index)|Vrátí index do `tuple` představující prvek ve vybrané `choice` zasílání zpráv bloku.|  
|[link_target –](#link_target)|Cílový blok odkazuje na tato `choice` zasílání zpráv bloku.|  
|[verze](#release)|Uvolní předchozí rezervace úspěšné zprávy.|  
|[release_ref –](#release_ref)|Uvolní počet odkazů v tomto `choice` zasílání zpráv bloku.|  
|[Rezervovat](#reserve)|Rezervuje zprávu dříve nabízí to `choice` zasílání zpráv bloku.|  
|[unlink_target –](#unlink_target)|Zruší propojení cílový blok z tohoto `choice` zasílání zpráv bloku.|  
|[unlink_targets –](#unlink_targets)|Zruší všechny cíle z tohoto propojení `choice` zasílání zpráv bloku. (Přepisuje [isource::unlink_targets –](isource-class.md#unlink_targets).)|  
|[Hodnota](#value)|Získá zprávu, jejíž index nebyla vybrána pomocí `choice` zasílání zpráv bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Výběr bloku zajišťuje využívat pouze jeden z příchozí zprávy.  
  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ISource](isource-class.md)  
  
 `choice`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept"></a>přijmout 

 Přijme zprávu, která byla nabízí to `choice` bloku, přenos vlastnictví volajícímu.  
  
```  
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `accept` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zprávu, která má volající teď vlastnictví.  
  
##  <a name="acquire_ref"></a>acquire_ref – 

 Získá počet odkazů v tomto `choice` zasílání zpráv bloku, aby se zabránilo odstranění.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na cílový blok, který je voláním této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je propojena k tomuto zdroji během `link_target` metoda.  
  
##  <a name="ctor"></a>Volba 

 Vytvoří `choice` zasílání zpráv bloku.  
  
```  
explicit choice(
    T _Tuple);

 
choice(
    Scheduler& _PScheduler,  
    T _Tuple);

 
choice(
    ScheduleGroup& _PScheduleGroup,  
    T _Tuple);

 
choice(
    choice&& _Choice);
```  
  
### <a name="parameters"></a>Parametry  
 `_Tuple`  
 A `tuple` zdrojů pro výběr.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `choice` je naplánováno zasílání zpráv bloku.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `choice` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
 `_Choice`  
 A `choice` zasílání zpráv bloku zkopírovat z. Všimněte si, že je osamocený původní objekt, provedení tento konstruktor move.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Přesunutí konstrukce však není provedena v rámci zámku, což znamená, zda je uživatel a ujistěte se, že nejsou žádné úkoly šedé – pohybující se při přesunutí. Jinak hodnota množství RAS situace může nastat, což výjimky nebo nekonzistentním stavu.  
  
##  <a name="dtor"></a>~ výběru 

 Zničí `choice` zasílání zpráv bloku.  
  
```  
~choice();
```  
  
##  <a name="consume"></a>využívat 

 Využívá zprávu dříve nabízí to `choice` zasílání zpráv na úrovni bloku a úspěšně rezervován cíl, přenos vlastnictví volajícímu.  
  
```  
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z vyhrazených `message` objektu.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `consume` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` objektu volající má nyní vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 `consume` Metoda je podobná `accept`, ale musí být vždy uvedeny volání `reserve` vrácená `true`.  
  
##  <a name="has_value"></a>has_value – 

 Kontroluje, zda tato `choice` zasílání zpráv bloku byl inicializován s hodnotou ještě.  
  
```  
bool has_value() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud bloku byl přijat hodnotu, `false` jinak.  
  
##  <a name="index"></a>index 

 Vrátí index do `tuple` představující prvek ve vybrané `choice` zasílání zpráv bloku.  
  
```  
size_t index();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Zpráva index.  
  
### <a name="remarks"></a>Poznámky  
 Datovou část zprávy lze extrahovat pomocí `get` metoda.  
  
##  <a name="link_target"></a>link_target – 

 Cílový blok odkazuje na tato `choice` zasílání zpráv bloku.  
  
```  
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na `ITarget` bloku propojit k tomuto `choice` zasílání zpráv bloku.  
  
##  <a name="release"></a>verze 

 Uvolní předchozí rezervace úspěšné zprávy.  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu vydán.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `release` metoda.  
  
##  <a name="release_ref"></a>release_ref – 

 Uvolní počet odkazů v tomto `choice` zasílání zpráv bloku.  
  
```  
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na cílový blok, který je voláním této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je právě odpojení z tohoto zdroje. Chcete-li uvolnit všechny prostředky, které jsou vyhrazené pro cílový blok je povoleno zdrojového bloku.  
  
##  <a name="reserve"></a>Rezervovat 

 Rezervuje zprávu dříve nabízí to `choice` zasílání zpráv bloku.  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu je vyhrazena.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `reserve` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud zpráva byla úspěšně vyhrazené, `false` jinak. Rezervace může selhat z mnoha důvodů, včetně: zpráva již byla vyhrazena nebo přijali jiný cíl, zdroj může odepřít rezervace a tak dále.  
  
### <a name="remarks"></a>Poznámky  
 Po zavolání metody `reserve`, pokud se aktivace podaří, musíte buď zavolat `consume` nebo `release` za účelem trvat nebo uvolňovat u sebe zprávy, v uvedeném pořadí.  
  
##  <a name="unlink_target"></a>unlink_target – 

 Zruší propojení cílový blok z tohoto `choice` zasílání zpráv bloku.  
  
```  
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na `ITarget` zrušení propojení z tohoto bloku `choice` zasílání zpráv bloku.  
  
##  <a name="unlink_targets"></a>unlink_targets – 

 Zruší všechny cíle z tohoto propojení `choice` zasílání zpráv bloku.  
  
```  
virtual void unlink_targets();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda není nutné volat z destruktoru, protože destruktor pro interní `single_assignment` bloku se zrušit propojení správně.  
  
##  <a name="value"></a>Hodnota 

 Získá zprávu, jejíž index nebyla vybrána pomocí `choice` zasílání zpráv bloku.  
  
```  
template <
    typename _Payload_type  
>  
_Payload_type const& value();
```  
  
### <a name="parameters"></a>Parametry  
 `_Payload_type`  
 Typ datové části zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Datová část zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Protože `choice` zasílání zpráv bloku může trvat vstupy s různé datové typy, je nutné zadat typ datové části v místě načtení. Můžete určit typ založené na výsledek `index` metoda.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [JOIN – třída](join-class.md)   
 [Třída single_assignment](single-assignment-class.md)
