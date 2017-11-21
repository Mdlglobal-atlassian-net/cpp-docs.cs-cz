---
title: "cache_suballoc – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
dev_langs: C++
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f835efbe84b05359a9a835f3afbdccf5839fc31c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cachesuballoc-class"></a>cache_suballoc – třída
Definuje [blokovat allocator](../standard-library/allocators-header.md) , přiděluje a zruší přidělení bloků paměti jedné velikosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <std::size_t Sz, size_t Nelts = 20>  
class cache_suballoc
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Sz`|Počet prvků v poli, která bude přidělena.|  
  
## <a name="remarks"></a>Poznámky  
 Cache_suballoc – třída šablony ukládá bloky deallocated paměti v bezplatné seznam s bez vazby délka pomocí `freelist<sizeof(Type), max_unbounded>`a suballocates bloky paměti z větší bloku, kterým je přiřazen `operator new` při volné seznam je prázdný.  
  
 Obsahuje každého bloku `Sz * Nelts` bajtů použitelné paměti a data, `operator new` a `operator delete` vyžadují. Přidělené bloky se nikdy uvolněno.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[cache_suballoc –](#cache_suballoc)|Vytvoří objekt typu `cache_suballoc`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[přidělit](#allocate)|Přiděluje blok paměti.|  
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="allocate"></a>cache_suballoc::allocate  
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
  
##  <a name="cache_suballoc"></a>cache_suballoc::cache_suballoc  
 Vytvoří objekt typu `cache_suballoc`.  
  
```
cache_suballoc();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="deallocate"></a>cache_suballoc::deallocate  
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



