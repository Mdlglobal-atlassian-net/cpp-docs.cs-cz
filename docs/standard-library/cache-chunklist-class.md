---
title: "cache_chunklist – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
dev_langs: C++
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f366e1a5d67aac945a366bbc81602b9bbb4002f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cachechunklist-class"></a>cache_chunklist – třída
Definuje [blokovat allocator](../standard-library/allocators-header.md) , přiděluje a zruší přidělení bloků paměti jedné velikosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <std::size_t Sz, std::size_t Nelts = 20>  
class cache_chunklist
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Sz`|Počet prvků v poli, která bude přidělena.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída šablona používá `operator new` přidělení bloků paměti raw, suballocating blokuje se přidělit úložiště pro blok paměti v případě potřeby; ukládá bloky deallocated paměti v samostatných volné seznamu pro každého bloku a používá `operator delete` se zrušit přidělení bloku, pokud žádná z jeho bloky paměti se používá.  
  
 Každý blok paměti obsahuje `Sz` bajtů použitelné paměti a ukazatel na dávky, která patří do. Obsahuje každého bloku `Nelts` bloky paměti, tři ukazatele, int a data, `operator new` a `operator delete` vyžadují.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[cache_chunklist –](#cache_chunklist)|Vytvoří objekt typu `cache_chunklist`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[přidělit](#allocate)|Přiděluje blok paměti.|  
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="allocate"></a>cache_chunklist::allocate  
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
  
##  <a name="cache_chunklist"></a>cache_chunklist::cache_chunklist  
 Vytvoří objekt typu `cache_chunklist`.  
  
```
cache_chunklist();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="deallocate"></a>cache_chunklist::deallocate  
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



