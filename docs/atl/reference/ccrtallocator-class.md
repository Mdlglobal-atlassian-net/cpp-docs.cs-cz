---
title: "Třída CCRTAllocator | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
dev_langs: C++
helpviewer_keywords: CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 35d71154ccbfc5f2d3147c55aaedff8cf85a06de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccrtallocator-class"></a>CCRTAllocator – třída
Tato třída poskytuje metody pro správu paměti pomocí rutiny CRT paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class ATL::CCRTAllocator
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CCRTAllocator::Allocate](#allocate)|(Statické) Voláním této metody lze přidělit paměť.|  
|[CCRTAllocator::Free](#free)|(Statické) Volejte tuto metodu za účelem uvolnění paměti.|  
|[CCRTAllocator::Reallocate](#reallocate)|(Statické) Volejte tuto metodu a znovu přidělte paměť.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída se používá ve [CHeapPtr](../../atl/reference/cheapptr-class.md) k poskytnutí paměti CRT přidělení rutiny. Třída protějšku [CComAllocator](../../atl/reference/ccomallocator-class.md), poskytuje stejné metody, pomocí rutiny COM.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
##  <a name="allocate"></a>CCRTAllocator::Allocate  
 Volání této statické funkce přidělit paměť.  
  
```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Počet bajtů přidělit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí neplatný ukazatel přidělené místo, nebo hodnota NULL, pokud není k dispozici dostatek paměti.  
  
### <a name="remarks"></a>Poznámky  
 Přidělí paměť. V tématu [malloc –](../../c-runtime-library/reference/malloc.md) další podrobnosti.  
  
##  <a name="free"></a>CCRTAllocator::Free  
 Volání této statické funkce na uvolnění paměti.  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na přidělenou paměť.  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělenou paměť. V tématu [volné](../../c-runtime-library/reference/free.md) další podrobnosti.  
  
##  <a name="reallocate"></a>CCRTAllocator::Reallocate  
 Volání této statické funkce a znovu přidělte paměť.  
  
```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na přidělenou paměť.  
  
 `nBytes`  
 Počet bajtů a znovu přidělte.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí neplatný ukazatel přidělené místo, nebo hodnota NULL, pokud je nedostatek paměti.  
  
### <a name="remarks"></a>Poznámky  
 Změní velikost je množství paměti přidělené. V tématu [realloc –](../../c-runtime-library/reference/realloc.md) další podrobnosti.  
  
## <a name="see-also"></a>Viz také  
 [CHeapPtr – třída](../../atl/reference/cheapptr-class.md)   
 [CComAllocator – třída](../../atl/reference/ccomallocator-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
