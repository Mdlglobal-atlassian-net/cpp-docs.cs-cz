---
title: "single_link_registry – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
dev_langs: C++
helpviewer_keywords: single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 11e02e4adb2e2bdb79f275537047199f434a57c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="singlelinkregistry-class"></a>single_link_registry – třída
`single_link_registry` Objekt `network_link_registry` , spravuje pouze jeden blok zdroje nebo cíle.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_Block`  
 Datový blok typ ukládají do `single_link_registry` objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[single_link_registry](#ctor)|Vytvoří `single_link_registry` objektu.|  
|[~ single_link_registry – destruktor](#dtor)|Zničí `single_link_registry` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[add](#add)|Přidá odkaz `single_link_registry` objektu. (Přepisuje [network_link_registry::Add –](network-link-registry-class.md#add).)|  
|[začít](#begin)|Vrátí iterovat prvním elementem v `single_link_registry` objektu. (Přepisuje [network_link_registry::BEGIN –](network-link-registry-class.md#begin).)|  
|[obsahuje](#contains)|Hledání `single_link_registry` objekt pro zadaný blok. (Přepisuje [network_link_registry::contains –](network-link-registry-class.md#contains).)|  
|[počet](#count)|Spočítá počet položek v `single_link_registry` objektu. (Přepisuje [network_link_registry::Count –](network-link-registry-class.md#count).)|  
|[remove](#remove)|Odebere odkaz z `single_link_registry` objektu. (Přepisuje [network_link_registry::Remove –](network-link-registry-class.md#remove).)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [network_link_registry](network-link-registry-class.md)  
  
 `single_link_registry`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="add"></a>Přidat 

 Přidá odkaz `single_link_registry` objektu.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok, který se má přidat.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_link_target](invalid-link-target-class.md) výjimka, pokud již existuje vazba v této registru.  
  
##  <a name="begin"></a>začít 

 Vrátí iterovat prvním elementem v `single_link_registry` objektu.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor adresování prvním elementem v `single_link_registry` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je indikován stav end `NULL` odkaz.  
  
##  <a name="contains"></a>obsahuje 

 Hledání `single_link_registry` objekt pro zadaný blok.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok, který má být vyhledán v `single_link_registry` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud byl nalezen na odkaz, `false` jinak.  
  
##  <a name="count"></a>počet 

 Spočítá počet položek v `single_link_registry` objektu.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v `single_link_registry` objektu.  
  
##  <a name="remove"></a>odebrat 

 Odebere odkaz z `single_link_registry` objektu.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok odebrány, pokud nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud byl nalezen, odebrat, odkaz `false` jinak.  
  
##  <a name="ctor"></a>single_link_registry 

 Vytvoří `single_link_registry` objektu.  
  
```
single_link_registry();
```  
  
##  <a name="dtor"></a>~ single_link_registry 

 Zničí `single_link_registry` objektu.  
  
```
virtual ~single_link_registry();
```  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_operation](invalid-operation-class.md) výjimka, pokud je volána, než je odebrán odkaz.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [multi_link_registry – třída](multi-link-registry-class.md)
