---
title: "cache_freelist – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
dev_langs: C++
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c971a4aebcd0f0a7c0baa59a445059f681f7e8af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cachefreelist-class"></a>cache_freelist – třída
Definuje [blokovat allocator](../standard-library/allocators-header.md) , přiděluje a zruší přidělení bloků paměti jedné velikosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <std::size_t Sz, class Max>  
class cache_freelist
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Sz`|Počet prvků v poli, která bude přidělena.|  
|`Max`|Maximální třída představující maximální velikost seznamu volné. To může být [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), nebo [max_variable_size](../standard-library/max-variable-size-class.md).|  
  
## <a name="remarks"></a>Poznámky  
 Cache_freelist – třída šablony udržuje seznam bloky paměti o velikosti volného `Sz`. Při zaplnění seznamu volné používá `operator delete` se zrušit přidělení paměti blokuje. Volné seznam je prázdný používá `operator new` přidělit nový bloky paměti. Maximální velikost seznamu volné je určen podle třídy maximální třída předaná `Max` parametr.  
  
 Každý blok paměti obsahuje `Sz` bajtů použitelné paměti a data, `operator new` a `operator delete` vyžadují.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[cache_freelist –](#cache_freelist)|Vytvoří objekt typu `cache_freelist`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[allocate](#allocate)|Přiděluje blok paměti.|  
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="allocate"></a>cache_freelist::allocate  
 Přiděluje blok paměti.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`count`|Počet prvků v poli, která bude přidělena.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na objekt přidělená.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cache_freelist"></a>cache_freelist::cache_freelist  
 Vytvoří objekt typu `cache_freelist`.  
  
```
cache_freelist();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="deallocate"></a>cache_freelist::deallocate  
 Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.  
  
```
void deallocate(void* ptr, std::size_t count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`ptr`|Ukazatel na první objekt, který má být navrácena z úložiště.|  
|`count`|Počet objektů, které chcete být navrácena z úložiště.|  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [\<alokátorů >](../standard-library/allocators-header.md)



