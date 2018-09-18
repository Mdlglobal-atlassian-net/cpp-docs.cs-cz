---
title: multitype_join – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eea798db304b27a77ae70766a7271cfa3f94981b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019408"
---
# <a name="multitypejoin-class"></a>multitype_join – třída
A `multitype_join` blok zpráv je více zdroje, jeden cílový blok zpráv, který spojuje dohromady zpráv různých typů ze všech zdrojů a nabízí se řazená kolekce členů kombinované zprávy do cíle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<
    typename T,  
    join_type _Jtype = non_greedy  
>  
class multitype_join: public ISource<typename _Unwrap<T>::type>;  
```  
  
#### <a name="parameters"></a>Parametry  
*T*<br/>
`tuple` Typ datové části zprávy připojený a následně bloku.  
  
*_Jtype*<br/>
Druh nástroje `join` bloku jedná buď `greedy` nebo `non_greedy`  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`type`|Alias typu pro `T`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[multitype_join](#ctor)|Přetíženo. Vytvoří `multitype_join` blok zpráv.|  
|[~multitype_join Destructor](#dtor)|Odstraní `multitype_join` blok zpráv.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Přijmout](#accept)|Přijme zprávu, která byly nabízeny situace `multitype_join` bloku, přenos vlastnictví volajícímu.|  
|[acquire_ref](#acquire_ref)|Získá počet odkazů na tomto `multitype_join` blok zpráv, abyste zabránili odstranění.|  
|[využívání](#consume)|Využívá dříve nabízená zpráva `multitype_join` bloku zpráv a úspěšně vyhrazen v cíli, přenos vlastnictví volajícímu.|  
|[link_target](#link_target)|K této propojuje cílový blok `multitype_join` blok zpráv.|  
|[Vydání verze](#release)|Uvolní předchozí vyhrazení úspěšné zprávy.|  
|[release_ref](#release_ref)|Počet odkazů v tomto vydání `multiple_join` blok zpráv.|  
|[Rezervovat](#reserve)|Vyhradí zprávu nabízely dříve v tomto `multitype_join` blok zpráv.|  
|[unlink_target](#unlink_target)|Cílový blok z tohoto nebude odpojen `multitype_join` blok zpráv.|  
|[unlink_targets](#unlink_targets)|Zruší všechny cíle z tohoto propojení `multitype_join` blok zpráv. (Přepíše [isource::unlink_targets –](isource-class.md#unlink_targets).)|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Isource –](isource-class.md)  
  
 `multitype_join`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept"></a> Přijmout 

 Přijme zprávu, která byly nabízeny situace `multitype_join` bloku, přenos vlastnictví volajícímu.  
  
```  
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.  
  
*_PTarget*<br/>
Ukazatel na cílový blok, který volá `accept` metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zprávu, která má volající nyní vlastnictví.  
  
##  <a name="acquire_ref"></a> acquire_ref – 

 Získá počet odkazů na tomto `multitype_join` blok zpráv, abyste zabránili odstranění.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel na cílový blok, který je volání této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který se odkazuje tento zdroj během `link_target` metody.  
  
##  <a name="consume"></a> využívání 

 Využívá dříve nabízená zpráva `multitype_join` bloku zpráv a úspěšně vyhrazen v cíli, přenos vlastnictví volajícímu.  
  
```  
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z vyhrazených `message` objektu.  
  
*_PTarget*<br/>
Ukazatel na cílový blok, který volá `consume` metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `message` volající má teď vlastnictví objektu.  
  
### <a name="remarks"></a>Poznámky  
 `consume` Metoda je podobná `accept`, ale musí vždy předcházet volání `reserve` vrácená `true`.  
  
##  <a name="link_target"></a> link_target – 

 K této propojuje cílový blok `multitype_join` blok zpráv.  
  
```  
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel `ITarget` bloku k propojení této `multitype_join` blok zpráv.  
  
##  <a name="ctor"></a> multitype_join – 

 Vytvoří `multitype_join` blok zpráv.  
  
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
*_Tuple*<br/>
A `tuple` zdrojů pro tuto `multitype_join` blok zpráv.  
  
*_PScheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `multitype_join` naplánovaný zasílání zpráv bloku.  
  
*_PScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `multitype_join` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.  
  
*_Spojit*<br/>
A `multitype_join` blok zpráv bude kopírováno. Všimněte si, že je osamocené na původní objekt, takže jde konstruktor move.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Přesun konstrukce neprovádí pod zámek, což znamená, že je až uživatele, aby se neobjeví žádné úlohy s nižšími nároky na cestě v době přesunutí. V opačném případě mnoha bude situace může nastat, což vede k výjimky nebo nekonzistentním stavu.  
  
##  <a name="dtor"></a> ~ multitype_join 

 Odstraní `multitype_join` blok zpráv.  
  
```  
~multitype_join();
```  
  
##  <a name="release"></a> Vydání verze 

 Uvolní předchozí vyhrazení úspěšné zprávy.  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` objektu se vydávají.  
  
*_PTarget*<br/>
Ukazatel na cílový blok, který volá `release` metody.  
  
##  <a name="release_ref"></a> release_ref – 

 Počet odkazů v tomto vydání `multiple_join` blok zpráv.  
  
```  
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel na cílový blok, který je volání této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je právě byl odpojen od tohoto zdroje. Zdrojový blok může uvolnit všechny prostředky, které jsou vyhrazené pro cílový blok.  
  
##  <a name="reserve"></a> Rezervovat 

 Vyhradí zprávu nabízely dříve v tomto `multitype_join` blok zpráv.  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` objekt dochází k rezervaci.  
  
*_PTarget*<br/>
Ukazatel na cílový blok, který volá `reserve` metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla úspěšně vyhrazené, `false` jinak. Rezervace může selhat z mnoha důvodů včetně: byla zpráva již vyhrazena nebo přijatý jiný cíl, zdroj může zamítnout rezervace a tak dále.  
  
### <a name="remarks"></a>Poznámky  
 Po zavolání `reserve`, pokud je úspěšná, musí buď volat `consume` nebo `release` aby bylo možné provést nebo vzdát vlastnictví zprávy, v uvedeném pořadí.  
  
##  <a name="unlink_target"></a> unlink_target – 

 Cílový blok z tohoto nebude odpojen `multitype_join` blok zpráv.  
  
```  
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel `ITarget` bloku se zrušit propojení z tohoto `multitype_join` blok zpráv.  
  
##  <a name="unlink_targets"></a> unlink_targets – 

 Zruší všechny cíle z tohoto propojení `multitype_join` blok zpráv.  
  
```  
virtual void unlink_targets();
```  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [choice – třída](choice-class.md)   
 [join – třída](join-class.md)
