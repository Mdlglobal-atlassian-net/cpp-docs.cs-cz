---
title: "rts_alloc – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
dev_langs: C++
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2e4870edc0b54a92307ddf88d58dd96ca3fd331e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="rtsalloc-class"></a>rts_alloc – třída
Rts_alloc – třída šablony popisuje [filtru](../standard-library/allocators-header.md) , obsahuje pole mezipaměti instancí a určuje, kterou instanci chcete použít pro přidělení a navrácení za běhu místo v době kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Cache>  
class rts_alloc
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Cache`|Typ instance služby cache obsažených v poli. To může být [cache_chunklist – třída](../standard-library/cache-chunklist-class.md), [cache_freelist –](../standard-library/cache-freelist-class.md), nebo [cache_suballoc –](../standard-library/cache-suballoc-class.md).|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída šablony obsahuje více bloku allocator instancí a určí, kterou instanci chcete použít pro přidělení nebo navrácení za běhu místo v době kompilace. Používá se s kompilátory, které nelze kompilovat obnovení vazby.  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[allocate](#allocate)|Přiděluje blok paměti.|  
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.|  
|[equals](#equals)|Porovná dva mezipamětí rovnosti.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="allocate"></a>rts_alloc::allocate  
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
 Členské funkce vrátí hodnotu `caches[_IDX].allocate(count)`, kde index `_IDX` je určena velikostí požadovaného bloku `count`, nebo pokud `count` je příliš velký, vrátí `operator new(count)`. `cache`, který představuje objekt mezipaměti.  
  
##  <a name="deallocate"></a>rts_alloc::deallocate  
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
 Volání členských funkcí `caches[_IDX].deallocate(ptr, count)`, kde index `_IDX` je určena velikostí požadovaného bloku `count`, nebo pokud `count` je příliš velký, vrátí `operator delete(ptr)`.  
  
##  <a name="equals"></a>rts_alloc::Equals  
 Porovná dva mezipamětí rovnosti.  
  
```
bool equals(const sync<_Cache>& _Other) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Cache`|Objekt mezipaměti přidružené k filtru.|  
|`_Other`|Objekt mezipaměti pro porovnání rovnosti.|  
  
### <a name="remarks"></a>Poznámky  
 `true`Pokud výsledek `caches[0].equals(other.caches[0])`, jinak hodnota `false`. `caches`představuje pole objektů mezipaměti.  
  
## <a name="see-also"></a>Viz také  
 [ALLOCATOR_DECL –](../standard-library/allocators-functions.md#allocator_decl)   
 [\<alokátorů >](../standard-library/allocators-header.md)



