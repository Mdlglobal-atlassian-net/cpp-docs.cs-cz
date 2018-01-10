---
title: "ITarget – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
dev_langs: C++
helpviewer_keywords: ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b67bf07ed7f1621ceb9a9428a03244ee5661707
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="itarget-class"></a>ITarget – třída
`ITarget` Třída je rozhraní pro všechny cílové bloky. Cíl bloky využívat zprávy jim podle nabízejí `ISource` bloky.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class ITarget;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ datové části v rámci zprávy přijímat cílový blok.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`filter_method`|Podpis libovolné metody, která používá blok, který vrátí `bool` hodnotu, která určí, zda nabízený zprávu musí přijmout.|  
|`type`|Typ aliasu pro `T`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[~ Itarget – destruktor](#dtor)|Zničí `ITarget` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[rozšíření](#propagate)|Při přepisu v odvozené třídě, asynchronně předá zprávu z bloku zdroj tento cílový blok.|  
|[Odeslat](#send)|Při přepisu v odvozené třídě, synchronně předá zprávu do cílový blok.|  
|[supports_anonymous_source –](#supports_anonymous_source)|Při přepisu v odvozené třídě vrátí hodnotu PRAVDA nebo NEPRAVDA v závislosti na tom, jestli bloku zpráv přijímá zprávy nabízí zdrojem, který není přidružený k němu. Pokud vrátí hodnotu přepsaného metoda `true`, cíl nemohou odložit zprávu nabízený jako spotřeba odložených zprávy později vyžaduje zdroji identifikaci v jeho sourse odkaz registru.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[link_source –](#link_source)|Při přepisu v odvozené třídě, odkazuje na tato blok zadaný zdrojový `ITarget` bloku.|  
|[unlink_source –](#unlink_source)|Při přepisu v odvozené třídě, zruší propojení blok zadaného zdroje. z tohoto `ITarget` bloku.|  
|[unlink_sources –](#unlink_sources)|Při přepisu v odvozené třídě, zruší propojení všech bloků zdroje z tohoto `ITarget` bloku.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ITarget`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a>~ ITarget 

 Zničí `ITarget` objektu.  
  
```
virtual ~ITarget();
```  
  
##  <a name="link_source"></a>link_source – 

 Při přepisu v odvozené třídě, odkazuje na tato blok zadaný zdrojový `ITarget` bloku.  
  
```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 `ISource` Blokovat propojovaném tomuto `ITarget` bloku.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci nelze volat přímo na `ITarget` bloku. Bloky by měly být připojené pomocí `link_target` metodu `ISource` bloků, které bude vyvolán `link_source` metoda na odpovídající cíli.  
  
##  <a name="propagate"></a>rozšíření 

 Při přepisu v odvozené třídě, asynchronně předá zprávu z bloku zdroj tento cílový blok.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
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
  
##  <a name="send"></a>Odeslat 

 Při přepisu v odvozené třídě, synchronně předá zprávu do cílový blok.  
  
```
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
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
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source – 

 Při přepisu v odvozené třídě vrátí hodnotu PRAVDA nebo NEPRAVDA v závislosti na tom, jestli bloku zpráv přijímá zprávy nabízí zdrojem, který není přidružený k němu. Pokud vrátí hodnotu přepsaného metoda `true`, cíl nemohou odložit zprávu nabízený jako spotřeba odložených zprávy později vyžaduje zdroji identifikaci v jeho sourse odkaz registru.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud bloku může přijmout zprávy ze zdroje, který není přidružený k němu `false` jinak.  
  
##  <a name="unlink_source"></a>unlink_source – 

 Při přepisu v odvozené třídě, zruší propojení blok zadaného zdroje. z tohoto `ITarget` bloku.  
  
```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_PSource`  
 `ISource` Blokovat Probíhá odpojení z tohoto `ITarget` bloku.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci nelze volat přímo na `ITarget` bloku. Bloky by měl být odpojeno pomocí `unlink_target` nebo `unlink_targets` metody na `ISource` bloků, které bude vyvolán `unlink_source` metoda na odpovídající cíli.  
  
##  <a name="unlink_sources"></a>unlink_sources – 

 Při přepisu v odvozené třídě, zruší propojení všech bloků zdroje z tohoto `ITarget` bloku.  
  
```
virtual void unlink_sources() = 0;
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [ISource – třída](isource-class.md)
