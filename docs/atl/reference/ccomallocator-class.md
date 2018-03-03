---
title: "Třída CComAllocator | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 370a52e87bcbb4849883ea03016cc462030ad028
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomallocator-class"></a>CComAllocator – třída
Tato třída poskytuje metody pro správu paměti pomocí rutiny paměti COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComAllocator
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComAllocator::Allocate](#allocate)|Volejte tuto metodu statické přidělit paměť.|  
|[CComAllocator::Free](#free)|Volejte tuto metodu statické uvolnit přidělené paměti.|  
|[CComAllocator::Reallocate](#reallocate)|Volejte tuto metodu statické a znovu přidělte paměť.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída se používá ve [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) k poskytnutí paměti COM přidělení rutiny. Třída protějšku [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), poskytuje stejné metody, pomocí rutiny CRT.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="allocate"></a>CComAllocator::Allocate  
 Volání této statické funkce přidělit paměť.  
  
```
static void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Počet bajtů přidělit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí neplatný ukazatel přidělené místo, nebo hodnota NULL, pokud není k dispozici dostatek paměti.  
  
### <a name="remarks"></a>Poznámky  
 Přidělí paměť. V tématu [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727) další podrobnosti.  
  
##  <a name="free"></a>CComAllocator::Free  
 Volání této statické funkce uvolnit přidělené paměti.  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na přidělenou paměť.  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělenou paměť. V tématu [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722) další podrobnosti.  
  
##  <a name="reallocate"></a>CComAllocator::Reallocate  
 Volání této statické funkce a znovu přidělte paměť.  
  
```
static void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na přidělenou paměť.  
  
 `nBytes`  
 Počet bajtů a znovu přidělte.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací neplatný ukazatel na přidělené místo, nebo hodnota NULL, pokud je nedostatek paměti  
  
### <a name="remarks"></a>Poznámky  
 Změní velikost je množství paměti přidělené. V tématu [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280) další podrobnosti.  
  
## <a name="see-also"></a>Viz také  
 [CComHeapPtr – třída](../../atl/reference/ccomheapptr-class.md)   
 [CCRTAllocator – třída](../../atl/reference/ccrtallocator-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
