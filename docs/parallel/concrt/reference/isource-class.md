---
title: ISource – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
dev_langs:
- C++
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27b1aa57a8c90c2f996aab3b8ee47797f15edd5b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692568"
---
# <a name="isource-class"></a>ISource – třída
`ISource` Třída je rozhraní pro všechny zdrojové bloky. Zdroj bloky rozšířit zprávy a pokuste se `ITarget` bloky.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class ISource;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ datové části v rámci zprávy vyprodukované zdrojového bloku.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`source_type`|Typ aliasu pro `T`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[~ ISource – destruktor](#dtor)|Zničí `ISource` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Přijmout](#accept)|Při přepisu v odvozené třídě, přijme zprávu, která byla nabízí to `ISource` bloku, přenos vlastnictví volajícímu.|  
|[acquire_ref](#acquire_ref)|Při přepisu v odvozené třídě, získá počet odkazů v tomto `ISource` bloku, aby se zabránilo odstranění.|  
|[Využívat](#consume)|Při přepisu v odvozené třídě, využívá zprávu dříve nabízí to `ISource` blokovat a úspěšně rezervován cíl, přenos vlastnictví volajícímu.|  
|[link_target](#link_target)|Při přepisu v odvozené třídě, odkazuje na tato cílový blok `ISource` bloku.|  
|[Verze](#release)|Při přepisu v odvozené třídě, uvolní předchozí rezervace úspěšné zprávy.|  
|[release_ref](#release_ref)|Při přepisu v odvozené třídě, uvolní počet odkazů v tomto `ISource` bloku.|  
|[Rezervovat](#reserve)|Při přepisu v odvozené třídě, vyhrazuje zprávu dříve nabízí to `ISource` bloku.|  
|[unlink_target](#unlink_target)|Při přepisu v odvozené třídě, zruší propojení cílový blok z tohoto `ISource` blokování, pokud nalezen dříve propojení.|  
|[unlink_targets](#unlink_targets)|Při přepisu v odvozené třídě, zruší propojení všech bloků cílový z tohoto `ISource` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ISource`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="accept"></a> Přijmout 

 Při přepisu v odvozené třídě, přijme zprávu, která byla nabízí to `ISource` bloku, přenos vlastnictví volajícímu.  
  
```
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `accept` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na zprávu, která má volající teď vlastnictví.  
  
### <a name="remarks"></a>Poznámky  
 `accept` Metoda je volána cíl při zprávu nabízený to `ISource` bloku. Ukazatel zpráva vrácená může být jiný než předaný do `propagate` metodu `ITarget` blokování, pokud se tento zdroj rozhodne vytvořit kopii zprávy.  
  
##  <a name="acquire_ref"></a> acquire_ref – 

 Při přepisu v odvozené třídě, získá počet odkazů v tomto `ISource` bloku, aby se zabránilo odstranění.  
  
```
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na cílový blok, který je voláním této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je propojena k tomuto zdroji během `link_target` metoda.  
  
##  <a name="consume"></a> Využívat 

 Při přepisu v odvozené třídě, využívá zprávu dříve nabízí to `ISource` blokovat a úspěšně rezervován cíl, přenos vlastnictví volajícímu.  
  
```
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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
  
##  <a name="dtor"></a> ~ ISource 

 Zničí `ISource` objektu.  
  
```
virtual ~ISource();
```  
  
##  <a name="link_target"></a> link_target – 

 Při přepisu v odvozené třídě, odkazuje na tato cílový blok `ISource` bloku.  
  
```
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na cílový blok propojovaném tomuto `ISource` bloku.  
  
##  <a name="release"></a> Verze 

 Při přepisu v odvozené třídě, uvolní předchozí rezervace úspěšné zprávy.  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` z vyhrazených `message` objektu.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `release` metoda.  
  
##  <a name="release_ref"></a> release_ref – 

 Při přepisu v odvozené třídě, uvolní počet odkazů v tomto `ISource` bloku.  
  
```
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na cílový blok, který je voláním této metody.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána `ITarget` objekt, který je právě odpojení z tohoto zdroje. Chcete-li uvolnit všechny prostředky, které jsou vyhrazené pro cílový blok je povoleno zdrojového bloku.  
  
##  <a name="reserve"></a> Rezervovat 

 Při přepisu v odvozené třídě, vyhrazuje zprávu dříve nabízí to `ISource` bloku.  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_MsgId`  
 `runtime_object_identity` Nabízených `message` objektu.  
  
 `_PTarget`  
 Ukazatel na cílový blok, který volá `reserve` metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla úspěšně vyhrazené, `false` jinak. Rezervace může selhat z mnoha důvodů, včetně: zpráva již byla vyhrazena nebo přijali jiný cíl, zdroj může odepřít rezervace a tak dále.  
  
### <a name="remarks"></a>Poznámky  
 Po zavolání metody `reserve`, pokud se aktivace podaří, musíte buď zavolat `consume` nebo `release` za účelem trvat nebo uvolňovat u sebe zprávy, v uvedeném pořadí.  
  
##  <a name="unlink_target"></a> unlink_target – 

 Při přepisu v odvozené třídě, zruší propojení cílový blok z tohoto `ISource` blokování, pokud nalezen dříve propojení.  
  
```
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Ukazatel na cílový blok Probíhá odpojení z tohoto `ISource` bloku.  
  
##  <a name="unlink_targets"></a> unlink_targets – 

 Při přepisu v odvozené třídě, zruší propojení všech bloků cílový z tohoto `ISource` bloku.  
  
```
virtual void unlink_targets() = 0;
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [ITarget – třída](itarget-class.md)
