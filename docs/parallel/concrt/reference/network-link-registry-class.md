---
title: network_link_registry – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
dev_langs:
- C++
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dab0ad6aff391eb89ac59198fb8c173ecb362bbd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="networklinkregistry-class"></a>network_link_registry – třída
`network_link_registry` Abstraktní základní třída spravuje propojení mezi zdrojovými a cílovými bloky.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _Block>
class network_link_registry;
```  
  
#### <a name="parameters"></a>Parametry  
 `_Block`  
 Datový blok typ ukládají do `network_link_registry`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`const_pointer`|Typ, který poskytuje odkazy `const` element v `network_link_registry` objektu.|  
|`const_reference`|Typ, který obsahuje odkaz na `const` element uložené v `network_link_registry` objekt pro čtení a provádění const operací.|  
|`iterator`|Typ, který poskytuje iterace, které můžou číst nebo upravovat libovolný element v `network_link_registry` objektu.|  
|`type`|Typ, který reprezentuje typ bloku uložené v `network_link_registry` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[add](#add)|Při přepisu v odvozené třídě, přidá odkaz `network_link_registry` objektu.|  
|[Začátek](#begin)|Při přepsání v odvozené třídě vrátí iterovat na prvním elementem v `network_link_registry` objektu.|  
|[Obsahuje](#contains)|Při přepisu v odvozené třídě, vyhledá `network_link_registry` objekt pro zadaný blok.|  
|[Počet](#count)|Při přepsání v odvozené třídě vrátí počet položek v `network_link_registry` objektu.|  
|[remove](#remove)|Při přepisu v odvozené třídě Odstraní zadaný blok z `network_link_registry` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `network link registry` Není bezpečná pro souběžný přístup.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `network_link_registry`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="add"></a> Přidat 

 Při přepisu v odvozené třídě, přidá odkaz `network_link_registry` objektu.  
  
```
virtual void add(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok, který se má přidat.  
  
##  <a name="begin"></a> Začátek 

 Při přepsání v odvozené třídě vrátí iterovat na prvním elementem v `network_link_registry` objektu.  
  
```
virtual iterator begin() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor adresování prvním elementem v `network_link_registry` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je indikován stav end iteraci `NULL` odkaz.  
  
##  <a name="contains"></a> Obsahuje 

 Při přepisu v odvozené třídě, vyhledá `network_link_registry` objekt pro zadaný blok.  
  
```
virtual bool contains(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok, který má být vyhledán ve `network_link_registry` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud byla nalezena bloku, `false` jinak.  
  
##  <a name="count"></a> Počet 

 Při přepsání v odvozené třídě vrátí počet položek v `network_link_registry` objektu.  
  
```
virtual size_t count() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v `network_link_registry` objektu.  
  
##  <a name="remove"></a> Odebrat 

 Při přepisu v odvozené třídě Odstraní zadaný blok z `network_link_registry` objektu.  
  
```
virtual bool remove(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok odebrány, pokud nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud byl nalezen, odebrat, odkaz `false` jinak.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [single_link_registry – třída](single-link-registry-class.md)   
 [multi_link_registry – třída](multi-link-registry-class.md)
