---
title: "multitype_join – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
dev_langs: C++
helpviewer_keywords: multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b87dda35c2ea031424af3ab2aa8ebdccdb3750fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="multitypejoin-class"></a>multitype_join – třída
A `multitype_join` zasílání zpráv blok je více zdroje, jeden cílový blok zasílání zpráv, který kombinuje společně zprávy různých typů z každé její zdroje a nabízí řazené kolekce členů kombinované zpráv k jeho cílům.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<
    typename T,  
    join_type _Jtype = non_greedy  
>  
class multitype_join: public ISource<typename _Unwrap<T>::type>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 `tuple` Typ datové části zprávy připojený a rozšířit pomocí bloku.  
  
 `_Jtype`  
 Druh z `join` bloku toto je buď `greedy` nebo`non_greedy`  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`type`|Typ aliasu pro `T`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[multitype_join](#ctor)|Přetíženo. Vytvoří `multitype_join` zasílání zpráv bloku.|  
|[~ multitype_join – destruktor](#dtor)|Zničí `multitype_join` zasílání zpráv bloku.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[přijmout](#accept)|Přijme zprávu, která byla nabízí to `multitype_join` bloku, přenos vlastnictví volajícímu.|  
|[acquire_ref –](#acquire_ref)|Získá počet odkazů v tomto `multitype_join` zasílání zpráv bloku, aby se zabránilo odstranění.|  
|[využívat](#consume)|Využívá dříve nabízené zprávy `multitype_join` zasílání zpráv na úrovni bloku a úspěšně rezervován cíl, přenos vlastnictví volajícímu.|  
|[link_target –](#link_target)|Cílový blok odkazuje na tato `multitype_join` zasílání zpráv bloku.|  
|[verze](#release)|Uvolní předchozí rezervace úspěšné zprávy.|  
|[release_ref –](#release_ref)|Uvolní počet odkazů v tomto `multiple_join` zasílání zpráv bloku.|  
|[Rezervovat](#reserve)|Rezervuje zprávu dříve nabízí to `multitype_join` zasílání zpráv bloku.|  
|[unlink_target –](#unlink_target)|Zruší propojení cílový blok z tohoto `multitype_join` zasílání zpráv bloku.|  
|[unlink_targets –](#unlink_targets)|Zruší všechny cíle z tohoto propojení `multitype_join` zasílání zpráv bloku. (Přepisuje [isource::unlink_targets –](isource-class.md#unlink_targets).)|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [ISource](isource-class.md)  
  
 `multitype_join`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept"></a>přijmout 

 Přijme zprávu, která byla nabízí to `multitype_join` bloku, přenos vlastnictví volajícímu.  
  
```  
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `accept` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zprávu, která má volající teď vlastnictví.  
  
##  <a name="acquire_ref"></a>acquire_ref – 

 Získá počet odkazů v tomto `multitype_join` zasílání zpráv bloku, aby se zabránilo odstranění.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na cílový blok, který je voláním této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je propojena k tomuto zdroji během `link_target` metoda.  
  
##  <a name="consume"></a>využívat 

 Využívá dříve nabízené zprávy `multitype_join` zasílání zpráv na úrovni bloku a úspěšně rezervován cíl, přenos vlastnictví volajícímu.  
  
```  
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
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
  
##  <a name="link_target"></a>link_target – 

 Cílový blok odkazuje na tato `multitype_join` zasílání zpráv bloku.  
  
```  
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na `ITarget` bloku propojit k tomuto `multitype_join` zasílání zpráv bloku.  
  
##  <a name="ctor"></a>multitype_join 

 Vytvoří `multitype_join` zasílání zpráv bloku.  
  
```  
explicit multitype_join(
    T _Tuple);

 
multitype_join(
    Scheduler& _PScheduler,  
    T _Tuple);

 
multitype_join(
    ScheduleGroup& _PScheduleGroup,  
    T _Tuple);

 
multitype_join(
    multitype_join&& _Join);
```  
  
### <a name="parameters"></a>Parametry  
 `_Tuple`  
 A `tuple` zdrojů pro tento `multitype_join` zasílání zpráv bloku.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `multitype_join` je naplánováno zasílání zpráv bloku.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `multitype_join` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
 `_Join`  
 A `multitype_join` zasílání zpráv bloku zkopírovat z. Všimněte si, že je osamocený původní objekt, provedení tento konstruktor move.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Přesunutí konstrukce však není provedena v rámci zámku, což znamená, zda je uživatel a ujistěte se, že nejsou žádné úkoly šedé – pohybující se při přesunutí. Jinak hodnota množství RAS situace může nastat, což výjimky nebo nekonzistentním stavu.  
  
##  <a name="dtor"></a>~ multitype_join 

 Zničí `multitype_join` zasílání zpráv bloku.  
  
```  
~multitype_join();
```  
  
##  <a name="release"></a>verze 

 Uvolní předchozí rezervace úspěšné zprávy.  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z `message` objektu vydán.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `release` metoda.  
  
##  <a name="release_ref"></a>release_ref – 

 Uvolní počet odkazů v tomto `multiple_join` zasílání zpráv bloku.  
  
```  
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na cílový blok, který je voláním této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je právě odpojení z tohoto zdroje. Chcete-li uvolnit všechny prostředky, které jsou vyhrazené pro cílový blok je povoleno zdrojového bloku.  
  
##  <a name="reserve"></a>Rezervovat 

 Rezervuje zprávu dříve nabízí to `multitype_join` zasílání zpráv bloku.  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
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

 Zruší propojení cílový blok z tohoto `multitype_join` zasílání zpráv bloku.  
  
```  
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na `ITarget` zrušení propojení z tohoto bloku `multitype_join` zasílání zpráv bloku.  
  
##  <a name="unlink_targets"></a>unlink_targets – 

 Zruší všechny cíle z tohoto propojení `multitype_join` zasílání zpráv bloku.  
  
```  
virtual void unlink_targets();
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [Třída Choice](choice-class.md)   
 [join – třída](join-class.md)
