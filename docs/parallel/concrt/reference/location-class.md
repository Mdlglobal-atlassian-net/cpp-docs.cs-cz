---
title: Location – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: a7d441aff74faede9ecbc41f03fe52cd05528e06
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104761"
---
# <a name="location-class"></a>location – třída
Abstrakce fyzického umístění na hardwaru.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class location;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[umístění](#ctor)|Přetíženo. Vytvoří `location` objektu.|  
|[~ location – destruktor](#dtor)|Odstraní `location` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[aktuální](#current)|Vrátí `location` objekt představující nejspecifičtější místo provádění volajícího vlákna.|  
|[from_numa_node](#from_numa_node)|Vrátí `location` objekt, který představuje daný uzel NUMA.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Určuje, zda dva `location` objekty představují jiné umístění.|  
|[operátor =](#operator_eq)|Přiřadí obsah jiného `location` do tohoto objektu.|  
|[operator==](#operator_eq_eq)|Určuje, zda dva `location` objekty představují stejné umístění.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `location`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> ~ umístění 

 Odstraní `location` objektu.  
  
```
~location();
```  
  
##  <a name="current"></a> aktuální 

 Vrátí `location` objekt představující nejspecifičtější místo provádění volajícího vlákna.  
  
```
static location __cdecl current();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Umístění představující nejspecifičtější místo provádí volajícího vlákna.  
  
##  <a name="from_numa_node"></a> from_numa_node – 

 Vrátí `location` objekt, který představuje daný uzel NUMA.  
  
```
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```  
  
### <a name="parameters"></a>Parametry  
*_NumaNodeNumber*<br/>
Číslo uzlu NUMA pro umístění pro sestavení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Umístění představující uzel NUMA určený `_NumaNodeNumber` parametru.  
  
##  <a name="ctor"></a> umístění 

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
*_Src*<br/>

*_LocationType*<br/>

*ID _ovládacího*<br/>

*_BindingId*<br/>

*_PBinding*<br/>
(Volitelné) Ukazatel na vazbu.

### <a name="remarks"></a>Poznámky  
 Výchozí vyrobený umístění představuje systém jako celek.  
  
##  <a name="operator_neq"></a> Operator! = 

 Určuje, zda dva `location` objekty představují jiné umístění.  
  
```
bool operator!= (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
*_Rhs*<br/>
Operand `location`.
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud se liší, dvěma umístěními `false` jinak.  
  
##  <a name="operator_eq"></a> operátor = 

 Přiřadí obsah jiného `location` do tohoto objektu.  
  
```
location& operator= (const location& _Rhs);
```  
  
### <a name="parameters"></a>Parametry  
*_Rhs*<br/>
Zdroj `location` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="operator_eq_eq"></a> Operator == 

 Určuje, zda dva `location` objekty představují stejné umístění.  
  
```
bool operator== (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
*_Rhs*<br/>
Operand `location`.
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud jsou identické, dvěma umístěními a `false` jinak.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
