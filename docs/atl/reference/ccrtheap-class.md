---
title: "Třída CCRTHeap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
dev_langs: C++
helpviewer_keywords: CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9864ce3522cf33927a3f6d3572e9d2e12187f5d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccrtheap-class"></a>CCRTHeap – třída
Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) používání haldy funkcí CRT.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CCRTHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CCRTHeap::Allocate](#allocate)|Voláním této metody lze přidělit blok paměti.|  
|[CCRTHeap::Free](#free)|Volejte tuto metodu k bezplatným blok paměti přidělené tomuto správci paměti.|  
|[CCRTHeap::GetSize](#getsize)|Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tomuto správci paměti.|  
|[CCRTHeap::Reallocate](#reallocate)|Volejte tuto metodu a znovu přidělte paměti přidělené tomuto správci paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `CCRTHeap`implementuje paměti pomocí CRT funkce přidělení haldy funkce, včetně [malloc –](../../c-runtime-library/reference/malloc.md), [volné](../../c-runtime-library/reference/free.md), [realloc –](../../c-runtime-library/reference/realloc.md), a [_msize –](../../c-runtime-library/reference/msize.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IAtlMemMgr`  
  
 `CCRTHeap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlmem.h  
  
##  <a name="allocate"></a>CCRTHeap::Allocate  
 Voláním této metody lze přidělit blok paměti.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Požadovaný počet bajtů v nového bloku paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na začátku bloku nově přidělených paměti.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CCRTHeap::Free](#free) nebo [CCRTHeap::Reallocate](#reallocate) k bezplatným je paměť přidělená touto metodou.  
  
 Implementovaná pomocí [malloc –](../../c-runtime-library/reference/malloc.md).  
  
##  <a name="free"></a>CCRTHeap::Free  
 Volejte tuto metodu k bezplatným blok paměti přidělené tomuto správci paměti.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na paměti dříve přidělené tomuto správci paměti. NULL není platná hodnota a neprovede žádnou akci.  
  
### <a name="remarks"></a>Poznámky  
 Implementovaná pomocí [volné](../../c-runtime-library/reference/free.md).  
  
##  <a name="getsize"></a>CCRTHeap::GetSize  
 Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tomuto správci paměti.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na paměti dříve přidělené tomuto správci paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí velikost bloku paměti přidělené v bajtech.  
  
### <a name="remarks"></a>Poznámky  
 Implementovaná pomocí [_msize –](../../c-runtime-library/reference/msize.md).  
  
##  <a name="reallocate"></a>CCRTHeap::Reallocate  
 Volejte tuto metodu a znovu přidělte paměti přidělené tomuto správci paměti.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na paměti dříve přidělené tomuto správci paměti.  
  
 `nBytes`  
 Požadovaný počet bajtů v nového bloku paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na začátku bloku nově přidělených paměti.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CCRTHeap::Free](#free) k bezplatným je paměť přidělená touto metodou. Implementovaná pomocí [realloc –](../../c-runtime-library/reference/realloc.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CComHeap – třída](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap – třída](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap – třída](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap – třída](../../atl/reference/cglobalheap-class.md)   
 [IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
