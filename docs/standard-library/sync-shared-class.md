---
title: "sync_shared – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
dev_langs: C++
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c84b340c82e735b3bcc62609ff1db10791f154e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="syncshared-class"></a>sync_shared – třída
Popisuje [filtr synchronizace](../standard-library/allocators-header.md) používající mutex k řízení přístupu k mezipaměti objekt, který sdílí všechny alokátorů.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Cache>  
class sync_shared
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Cache`|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist –](../standard-library/cache-chunklist-class.md), [cache_freelist –](../standard-library/cache-freelist-class.md), nebo [cache_suballoc –](../standard-library/cache-suballoc-class.md).|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[přidělit](#allocate)|Přiděluje blok paměti.|  
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.|  
|[rovná se](#equals)|Porovná dva mezipamětí rovnosti.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="allocate"></a>sync_shared::allocate  
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
 Členská funkce zamkne mutex, volání `cache.allocate(count)`, odemkne mutex a vrátí výsledek starší volání `cache.allocate(count)`. `cache`představuje aktuální objekt mezipaměti.  
  
##  <a name="deallocate"></a>sync_shared::deallocate  
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
 Tato funkce člen zamkne mutex, volání `cache.deallocate(ptr, count)`, kde `cache` představuje objekt mezipaměti a poté odemkne mutex.  
  
##  <a name="equals"></a>sync_shared::Equals  
 Porovná dva mezipamětí rovnosti.  
  
```
bool equals(const sync_shared<Cache>& Other) const;
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Cache`|Typ mezipaměti přidružené k filtru synchronizace.|  
|`Other`|Mezipaměť pro porovnání rovnosti.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud výsledek `cache.equals(Other.cache)`, kde `cache` představuje objekt mezipaměti, je `true`, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [\<alokátorů >](../standard-library/allocators-header.md)


