---
title: "multi_link_registry – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
dev_langs: C++
helpviewer_keywords: multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5d95a98d56ea666ed823f3caef2190dea1591cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="multilinkregistry-class"></a>multi_link_registry – třída
`multi_link_registry` Objekt `network_link_registry` , spravuje více bloků zdroje nebo více bloků cíl.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>Parametry  
 `_Block`  
 Datový blok typ ukládají do `multi_link_registry` objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[multi_link_registry](#ctor)|Vytvoří `multi_link_registry` objektu.|  
|[~ multi_link_registry – destruktor](#dtor)|Zničí `multi_link_registry` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[add](#add)|Přidá odkaz `multi_link_registry` objektu. (Přepisuje [network_link_registry::Add –](network-link-registry-class.md#add).)|  
|[začít](#begin)|Vrátí iterovat prvním elementem v `multi_link_registry` objektu. (Přepisuje [network_link_registry::BEGIN –](network-link-registry-class.md#begin).)|  
|[obsahuje](#contains)|Hledání `multi_link_registry` objekt pro zadaný blok. (Přepisuje [network_link_registry::contains –](network-link-registry-class.md#contains).)|  
|[počet](#count)|Spočítá počet položek v `multi_link_registry` objektu. (Přepisuje [network_link_registry::Count –](network-link-registry-class.md#count).)|  
|[remove](#remove)|Odebere odkaz z `multi_link_registry` objektu. (Přepisuje [network_link_registry::Remove –](network-link-registry-class.md#remove).)|  
|[set_bound –](#set_bound)|Nastaví horní mez počtu odkazy `multi_link_registry` objekt mohou být uloženy.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [network_link_registry](network-link-registry-class.md)  
  
 `multi_link_registry`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="add"></a>Přidat 

 Přidá odkaz `multi_link_registry` objektu.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok, který se má přidat.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_link_target](invalid-link-target-class.md) výjimka Pokud odkaz již existuje v registru, nebo pokud hranice již byl nastaven s `set_bound` funkce a odkaz má v mezičase odebrán.  
  
##  <a name="begin"></a>začít 

 Vrátí iterovat prvním elementem v `multi_link_registry` objektu.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor adresování prvním elementem v `multi_link_registry` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je indikován stav end `NULL` odkaz.  
  
##  <a name="contains"></a>obsahuje 

 Hledání `multi_link_registry` objekt pro zadaný blok.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok, který má být vyhledán v `multi_link_registry` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud byl nalezen zadaný blok, `false` jinak.  
  
##  <a name="count"></a>počet 

 Spočítá počet položek v `multi_link_registry` objektu.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v `multi_link_registry` objektu.  
  
##  <a name="ctor"></a>multi_link_registry 

 Vytvoří `multi_link_registry` objektu.  
  
```
multi_link_registry();
```  
  
##  <a name="dtor"></a>~ multi_link_registry 

 Zničí `multi_link_registry` objektu.  
  
```
virtual ~multi_link_registry();
```  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metoda [invalid_operation](invalid-operation-class.md) výjimka, pokud je volána před se odeberou všechny odkazy.  
  
##  <a name="remove"></a>odebrat 

 Odebere odkaz z `multi_link_registry` objektu.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok odebrány, pokud nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud byl nalezen, odebrat, odkaz `false` jinak.  
  
##  <a name="set_bound"></a>set_bound – 

 Nastaví horní mez počtu odkazy `multi_link_registry` objekt mohou být uloženy.  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>Parametry  
 `_MaxLinks`  
 Maximální počet odkazů, která `multi_link_registry` objekt mohou být uloženy.  
  
### <a name="remarks"></a>Poznámky  
 Po nastavení hranice se odpojuje položku způsobí, že `multi_link_registry` objekt, který chcete zadat neměnné stavu kde další volání `add` vyvolá výjimku `invalid_link_target` výjimka.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [single_link_registry – třída](single-link-registry-class.md)
