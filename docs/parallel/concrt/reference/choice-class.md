---
title: Třída Choice | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8bc30d3fe394dd9940e716be69a7c10360da59f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028620"
---
# <a name="choice-class"></a>Třída choice
A `choice` blok zpráv je více zdroje, jeden cílový blok, který představuje tok řízení interakce sadu zdrojů. Výběr bloku počká na některou z několika zdrojů do výsledné zprávu a rozšíří index zdroj, který vytvořil zprávu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<
    class T  
>  
class choice: public ISource<size_t>;  
```  
  
#### <a name="parameters"></a>Parametry  
*T*<br/>
A `tuple`– základní typ představující datové části ze vstupních zdrojů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`type`|Alias typu pro `T`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[podle výběru](#ctor)|Přetíženo. Vytvoří `choice` blok zpráv.|  
|[~ choice – destruktor](#dtor)|Odstraní `choice` blok zpráv.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Přijmout](#accept)|Přijme zprávu, která byly nabízeny situace `choice` bloku, přenos vlastnictví volajícímu.|  
|[acquire_ref](#acquire_ref)|Získá počet odkazů na tomto `choice` blok zpráv, abyste zabránili odstranění.|  
|[využívání](#consume)|Využívá zprávu nabízely dříve v tomto `choice` bloku zpráv a úspěšně vyhrazen v cíli, přenos vlastnictví volajícímu.|  
|[has_value](#has_value)|Zkontroluje, jestli to `choice` blok zpráv byl inicializován s hodnotou ještě.|  
|[index](#index)|Vrátí index do `tuple` představující prvek zvolila `choice` blok zpráv.|  
|[link_target](#link_target)|K této propojuje cílový blok `choice` blok zpráv.|  
|[Vydání verze](#release)|Uvolní předchozí vyhrazení úspěšné zprávy.|  
|[release_ref](#release_ref)|Počet odkazů v tomto vydání `choice` blok zpráv.|  
|[Rezervovat](#reserve)|Vyhradí zprávu nabízely dříve v tomto `choice` blok zpráv.|  
|[unlink_target](#unlink_target)|Cílový blok z tohoto nebude odpojen `choice` blok zpráv.|  
|[unlink_targets](#unlink_targets)|Zruší všechny cíle z tohoto propojení `choice` blok zpráv. (Přepíše [isource::unlink_targets –](isource-class.md#unlink_targets).)|  
|[value](#value)|Získá zprávu, jejíž index se zvolila `choice` blok zpráv.|  
  
## <a name="remarks"></a>Poznámky  
 Výběr bloku zajišťuje využívat jenom jeden z příchozí zprávy.  
  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Isource –](isource-class.md)  
  
 `choice`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept"></a> Přijmout 

 Přijme zprávu, která byly nabízeny situace `choice` bloku, přenos vlastnictví volajícímu.  
  
```  
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.  
  
*_PTarget*<br/>
Ukazatel na cílový blok, který volá `accept` metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zprávu, která má volající nyní vlastnictví.  
  
##  <a name="acquire_ref"></a> acquire_ref – 

 Získá počet odkazů na tomto `choice` blok zpráv, abyste zabránili odstranění.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel na cílový blok, který je volání této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který se odkazuje tento zdroj během `link_target` metody.  
  
##  <a name="ctor"></a> podle výběru 

 Vytvoří `choice` blok zpráv.  
  
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
*_Tuple*<br/>
A `tuple` zdrojů pro výběr.  
  
*_PScheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `choice` naplánovaný zasílání zpráv bloku.  
  
*_PScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `choice` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.  
  
*_Choice*<br/>
A `choice` blok zpráv bude kopírováno. Všimněte si, že je osamocené na původní objekt, takže jde konstruktor move.  
  
### <a name="remarks"></a>Poznámky  
 Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.  
  
 Přesun konstrukce neprovádí pod zámek, což znamená, že je až uživatele, aby se neobjeví žádné úlohy s nižšími nároky na cestě v době přesunutí. V opačném případě mnoha bude situace může nastat, což vede k výjimky nebo nekonzistentním stavu.  
  
##  <a name="dtor"></a> ~ podle výběru 

 Odstraní `choice` blok zpráv.  
  
```  
~choice();
```  
  
##  <a name="consume"></a> využívání 

 Využívá zprávu nabízely dříve v tomto `choice` bloku zpráv a úspěšně vyhrazen v cíli, přenos vlastnictví volajícímu.  
  
```  
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
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
  
##  <a name="has_value"></a> has_value – 

 Zkontroluje, jestli to `choice` blok zpráv byl inicializován s hodnotou ještě.  
  
```  
bool has_value() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud blok obsahuje přijala se hodnota, `false` jinak.  
  
##  <a name="index"></a> Index 

 Vrátí index do `tuple` představující prvek zvolila `choice` blok zpráv.  
  
```  
size_t index();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Datovou část zprávy může být extrahována pomocí `get` metody.  
  
##  <a name="link_target"></a> link_target – 

 K této propojuje cílový blok `choice` blok zpráv.  
  
```  
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel `ITarget` bloku k propojení této `choice` blok zpráv.  
  
##  <a name="release"></a> Vydání verze 

 Uvolní předchozí vyhrazení úspěšné zprávy.  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_MsgId*<br/>
`runtime_object_identity` z `message` objektu se vydávají.  
  
*_PTarget*<br/>
Ukazatel na cílový blok, který volá `release` metody.  
  
##  <a name="release_ref"></a> release_ref – 

 Počet odkazů v tomto vydání `choice` blok zpráv.  
  
```  
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel na cílový blok, který je volání této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je právě byl odpojen od tohoto zdroje. Zdrojový blok může uvolnit všechny prostředky, které jsou vyhrazené pro cílový blok.  
  
##  <a name="reserve"></a> Rezervovat 

 Vyhradí zprávu nabízely dříve v tomto `choice` blok zpráv.  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
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

 Cílový blok z tohoto nebude odpojen `choice` blok zpráv.  
  
```  
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
*_PTarget*<br/>
Ukazatel `ITarget` bloku se zrušit propojení z tohoto `choice` blok zpráv.  
  
##  <a name="unlink_targets"></a> unlink_targets – 

 Zruší všechny cíle z tohoto propojení `choice` blok zpráv.  
  
```  
virtual void unlink_targets();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda není nutné volat z destruktoru, protože destruktor pro vnitřní `single_assignment` bloku zrušíte propojení správně.  
  
##  <a name="value"></a> Hodnota 

 Získá zprávu, jejíž index se zvolila `choice` blok zpráv.  
  
```  
template <
    typename _Payload_type  
>  
_Payload_type const& value();
```  
  
### <a name="parameters"></a>Parametry  
*_Payload_type*<br/>
Typ datové části zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Datová část zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Protože `choice` blok zpráv může přijímat vstupy s různé datové typy, je nutné zadat typ datové části Přejme během načítání. Můžete určit typ na základě výsledku z `index` metody.  
  
## <a name="see-also"></a>Viz také  
 [souběžnost Namespace](concurrency-namespace.md)   
 [JOIN – třída](join-class.md)   
 [single_assignment – třída](single-assignment-class.md)
