---
title: "sync_per_thread – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f5ddaee26ba4a28a50920a4b71f91e284356b40d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="syncperthread-class"></a>sync_per_thread – třída
Popisuje [filtr synchronizace](../standard-library/allocators-header.md) poskytuje objekt samostatné mezipaměti každé vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Cache>  
class sync_per_thread
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Cache`|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist –](../standard-library/cache-chunklist-class.md), [cache_freelist –](../standard-library/cache-freelist-class.md), nebo [cache_suballoc –](../standard-library/cache-suballoc-class.md).|  
  
## <a name="remarks"></a>Poznámky  
 Alokátorů, které používají `sync_per_thread` můžete porovnat stejná, i když bloky přidělené v jedno vlákno nemůže být navrácena z jiného vlákna. Když pomocí jedné z těchto alokátorů bloky paměti přidělené v jedno vlákno by neměl být dostupná pro jiná vlákna. V praxi, to znamená, že kontejner, který používá jednu z těchto alokátorů by měly být dostupné pouze podle jednoho vlákna.  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[allocate](#allocate)|Přiděluje blok paměti.|  
|[Zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.|  
|[equals](#equals)|Porovná dva mezipamětí rovnosti.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="allocate"></a>  sync_per_thread::allocate  
 Přiděluje blok paměti.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`count`|Počet prvků v poli, která bude přidělena.|  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce vrátí výsledek volání `cache::allocate(count)` na objekt mezipaměti, které patří do aktuální vlákno. Pokud byl přidělen žádný objekt mezipaměti pro aktuální vlákno, nejprve přiděluje jeden.  
  
##  <a name="deallocate"></a>  sync_per_thread::deallocate  
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
 Volání členských funkcí `deallocate` na objekt mezipaměti, které patří do aktuální vlákno. Pokud byl přidělen žádný objekt mezipaměti pro aktuální vlákno, nejprve přiděluje jeden.  
  
##  <a name="equals"></a>  sync_per_thread::Equals  
 Porovná dva mezipamětí rovnosti.  
  
```
bool equals(const sync<Cache>& Other) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Cache`|Objekt mezipaměti filtru synchronizace.|  
|`Other`|Objekt mezipaměti pro porovnání rovnosti.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `false` Pokud byl přidělen žádný objekt mezipaměti pro tento objekt nebo pro `Other` v aktuální vlákno. V opačném případě vrátí výsledek použití `operator==` na dva objekty mezipaměti.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [\<allocators>](../standard-library/allocators-header.md)



