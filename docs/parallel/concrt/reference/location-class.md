---
title: Location – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
dev_langs:
- C++
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdfb555375df4b9f791db25fa2dee47222f79063
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688021"
---
# <a name="location-class"></a>location – třída
Abstrakci fyzické umístění na hardwaru.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class location;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Umístění](#ctor)|Přetíženo. Vytvoří `location` objektu.|  
|[~ location – destruktor](#dtor)|Zničí `location` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Aktuální](#current)|Vrátí `location` objekt reprezentující nejvíce místní volající vlákno je prováděna.|  
|[from_numa_node](#from_numa_node)|Vrátí `location` objekt, který představuje daný uzel NUMA.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Určuje, zda dva `location` představovat jiné umístění.|  
|[operátor =](#operator_eq)|Přiřadí obsah jiné `location` k tomuto objektu.|  
|[operator==](#operator_eq_eq)|Určuje, zda dva `location` představovat stejné umístění.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `location`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> ~ umístění 

 Zničí `location` objektu.  
  
```
~location();
```  
  
##  <a name="current"></a> Aktuální 

 Vrátí `location` objekt reprezentující nejvíce místní volající vlákno je prováděna.  
  
```
static location __cdecl current();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Umístění představující nejvíce místní volající vlákno je prováděna.  
  
##  <a name="from_numa_node"></a> from_numa_node – 

 Vrátí `location` objekt, který představuje daný uzel NUMA.  
  
```
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```  
  
### <a name="parameters"></a>Parametry  
 `_NumaNodeNumber`  
 Číslo uzlu NUMA, které má vytvořit umístění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Umístění představující určeného uzlu NUMA `_NumaNodeNumber` parametr.  
  
##  <a name="ctor"></a> Umístění 

 Vytvoří `location` objektu.  
  
```
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `_Src`  
 `_LocationType`  
 `_Id`  
 `_BindingId`  
 `_PBinding`  
  
### <a name="remarks"></a>Poznámky  
 Výchozí sestavený umístění představuje systém jako celek.  
  
##  <a name="operator_neq"></a> Operator! = 

 Určuje, zda dva `location` představovat jiné umístění.  
  
```
bool operator!= (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se liší, těmito dvěma umístěními `false` jinak.  
  
##  <a name="operator_eq"></a> operátor = 

 Přiřadí obsah jiné `location` k tomuto objektu.  
  
```
location& operator= (const location& _Rhs);
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
 Zdroj `location` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq_eq"></a> Operator == 

 Určuje, zda dva `location` představovat stejné umístění.  
  
```
bool operator== (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud jsou stejné, těmito dvěma umístěními a `false` jinak.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
