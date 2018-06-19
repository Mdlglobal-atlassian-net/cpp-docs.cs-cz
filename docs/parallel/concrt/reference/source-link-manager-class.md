---
title: source_link_manager – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
dev_langs:
- C++
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8e17626fc870242c97a9ad66a77e5e3b77b1ed1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691284"
---
# <a name="sourcelinkmanager-class"></a>source_link_manager – třída
`source_link_manager` Objekt spravuje zasílání zpráv bloku sítě odkazy na `ISource` bloky.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _LinkRegistry>
class source_link_manager;
```  
  
#### <a name="parameters"></a>Parametry  
 `_LinkRegistry`  
 Odkaz registru sítě.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`const_pointer`|Typ, který poskytuje odkazy `const` element v `source_link_manager` objektu.|  
|`const_reference`|Typ, který obsahuje odkaz na `const` element uložené v `source_link_manager` objekt pro čtení a provádění const operací.|  
|`iterator`|Typ, který poskytuje iterace, které můžou číst nebo upravovat libovolný element v `source_link_manager` objektu.|  
|`type`|Typ odkazu registru řízen pomocí `source_link_manager` objektu.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[source_link_manager](#ctor)|Vytvoří `source_link_manager` objektu.|  
|[~source_link_manager Destructor](#dtor)|Zničí `source_link_manager` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[add](#add)|Přidá odkaz na zdroj `source_link_manager` objektu.|  
|[Začátek](#begin)|Vrátí iterovat prvním elementem v `source_link_manager` objektu.|  
|[Obsahuje](#contains)|Hledání `network_link_registry` v rámci to `source_link_manager` objekt pro zadaný blok.|  
|[Počet](#count)|Spočítá počet propojené bloky v `source_link_manager` objektu.|  
|[Referenční dokumentace](#reference)|Získá odkaz na `source_link_manager` objektu.|  
|[register_target_block](#register_target_block)|Zaregistruje cílový blok, který obsahuje tento `source_link_manager` objektu.|  
|[Verze](#release)|Uvolní odkaz na `source_link_manager` objektu.|  
|[remove](#remove)|Odebere odkaz z `source_link_manager` objektu.|  
|[set_bound](#set_bound)|Nastaví maximální počet odkazů zdroj, který jde přidat do tohoto `source_link_manager` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 V současné době jsou bloky zdroj odkaz počítají. Toto je obálku na `network_link_registry` objekt, který umožňuje souběžný přístup k odkazy a poskytuje schopnost referenční odkazy prostřednictvím zpětných volání. Zpráva bloky ( `target_block`s nebo `propagator_block`s) by měla tato třída slouží pro jejich zdroje odkazy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `source_link_manager`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="add"></a> Přidat 

 Přidá odkaz na zdroj `source_link_manager` objektu.  
  
```
void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok, který se má přidat.  
  
##  <a name="begin"></a> Začátek 

 Vrátí iterovat prvním elementem v `source_link_manager` objektu.  
  
```
iterator begin();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor adresování prvním elementem v `source_link_manager` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je indikován stav end iteraci `NULL` odkaz.  
  
##  <a name="contains"></a> Obsahuje 

 Hledání `network_link_registry` v rámci to `source_link_manager` objekt pro zadaný blok.  
  
```
bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok, který má být vyhledán v `source_link_manager` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud byl nalezen zadaný blok, `false` jinak.  
  
##  <a name="count"></a> Počet 

 Spočítá počet propojené bloky v `source_link_manager` objektu.  
  
```
size_t count();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bloků s propojené v `source_link_manager` objektu.  
  
##  <a name="reference"></a> Referenční dokumentace 

 Získá odkaz na `source_link_manager` objektu.  
  
```
void reference();
```  
  
##  <a name="register_target_block"></a> register_target_block – 

 Zaregistruje cílový blok, který obsahuje tento `source_link_manager` objektu.  
  
```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parametry  
 `_PTarget`  
 Cílový blok, která uchovává to `source_link_manager` objektu.  
  
##  <a name="release"></a> Verze 

 Uvolní odkaz na `source_link_manager` objektu.  
  
```
void release();
```  
  
##  <a name="remove"></a> Odebrat 

 Odebere odkaz z `source_link_manager` objektu.  
  
```
bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parametry  
 `_Link`  
 Ukazatel na blok odebrány, pokud nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud byl nalezen, odebrat, odkaz `false` jinak.  
  
##  <a name="set_bound"></a> set_bound – 

 Nastaví maximální počet odkazů zdroj, který jde přidat do tohoto `source_link_manager` objektu.  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>Parametry  
 `_MaxLinks`  
 Maximální počet odkazů.  
  
##  <a name="ctor"></a> source_link_manager 

 Vytvoří `source_link_manager` objektu.  
  
```
source_link_manager();
```  
  
##  <a name="dtor"></a> ~ source_link_manager 

 Zničí `source_link_manager` objektu.  
  
```
~source_link_manager();
```  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [single_link_registry – třída](single-link-registry-class.md)   
 [multi_link_registry – třída](multi-link-registry-class.md)
