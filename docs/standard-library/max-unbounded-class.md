---
title: "max_unbounded – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
dev_langs: C++
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a06cc5f05812d662dc22fa7609680e3b5a45c97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="maxunbounded-class"></a>max_unbounded – třída
Popisuje [maximálního počtu třída](../standard-library/allocators-header.md) objekt, který neomezuje maximální délku [freelist](../standard-library/freelist-class.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class max_unbounded
```  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[přidělené](#allocated)|Zvětší počet bloků přidělené paměti.|  
|[zrušeno](#deallocated)|Snižuje počet přidělené bloky paměti.|  
|[Úplná](#full)|Vrátí hodnotu, která určuje, zda více bloky paměti by měla být přidán do seznamu volné.|  
|[vydání](#released)|Snižuje počet paměti bloků v seznamu volné.|  
|[Uložit](#saved)|Zvýší počet bloky paměti v seznamu volné.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<alokátorů >  
  
 **Namespace:** stdext –  
  
##  <a name="allocated"></a>max_unbounded::allocated  
 Zvětší počet bloků přidělené paměti.  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Nx`|Hodnota přírůstku.|  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen neprovede žádnou akci. Je volána po každém úspěšném volání pomocí `cache_freelist::allocate` operátor `new`. Argument `_Nx` je počet bloků paměti v bloku dat přidělené operátor `new`.  
  
##  <a name="deallocated"></a>max_unbounded::deallocated  
 Snižuje počet přidělené bloky paměti.  
  
```
void deallocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`_Nx`|Hodnota přírůstku.|  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce neprovede žádnou akci. Tato funkce člen je volána po každé pro volání `cache_freelist::deallocate` operátor `delete`. Argument `_Nx` je počet bloků paměti v bloku dat navrácena operátorem `delete`.  
  
##  <a name="full"></a>max_unbounded::full  
 Vrátí hodnotu, která určuje, zda více bloky paměti by měla být přidán do seznamu volné.  
  
```
bool full();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Členská funkce vždy vrátí hodnotu `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce volá `cache_freelist::deallocate`. Pokud se volání vrátí `true`, `deallocate` vloží bloku paměti v seznamu volné; Pokud vrátí hodnotu false, `deallocate` operátor volání `delete` se zrušit přidělení bloku.  
  
##  <a name="released"></a>max_unbounded::released  
 Snižuje počet paměti bloků v seznamu volné.  
  
```
void released();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen neprovede žádnou akci. `released` Je volána funkce člena třídy aktuální maximální `cache_freelist::allocate` vždy, když odebere blok paměti ze seznamu volné.  
  
##  <a name="saved"></a>max_unbounded::saved  
 Zvýší počet bloky paměti v seznamu volné.  
  
```
void saved();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen neprovede žádnou akci. Je volána metodou `cache_freelist::deallocate` vždy, když vloží blok paměti v seznamu volné.  
  
## <a name="see-also"></a>Viz také  
 [\<alokátorů >](../standard-library/allocators-header.md)



