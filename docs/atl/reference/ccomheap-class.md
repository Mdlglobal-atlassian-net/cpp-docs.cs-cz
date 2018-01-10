---
title: "Třída CComHeap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
dev_langs: C++
helpviewer_keywords: CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3cf86ebe45cdb0a70af6eebaaed90690e83e8db7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomheap-class"></a>CComHeap – třída
Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkce přidělení paměti COM.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComHeap::Allocate](#allocate)|Voláním této metody lze přidělit blok paměti.|  
|[CComHeap::Free](#free)|Volejte tuto metodu k bezplatným blok paměti přidělené tomuto správci paměti.|  
|[CComHeap::GetSize](#getsize)|Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tomuto správci paměti.|  
|[CComHeap::Reallocate](#reallocate)|Volejte tuto metodu a znovu přidělte paměti přidělené tomuto správci paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `CComHeap`implementuje funkce přidělení paměti pomocí funkcí přidělení COM, včetně [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226)a [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280). Maximální množství paměti, kterou lze přidělit rovná **INT_MAX** (2147483647) bajtů.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IAtlMemMgr`  
  
 `CComHeap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ATLComMem.h  
  
##  <a name="allocate"></a>CComHeap::Allocate  
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
 Volání [CComHeap::Free](#free) nebo [CComHeap::Reallocate](#reallocate) k bezplatným je paměť přidělená touto metodou.  
  
 Implementovaná pomocí [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727).  
  
##  <a name="free"></a>CComHeap::Free  
 Volejte tuto metodu k bezplatným blok paměti přidělené tomuto správci paměti.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na paměti dříve přidělené tomuto správci paměti. NULL není platná hodnota a neprovede žádnou akci.  
  
### <a name="remarks"></a>Poznámky  
 Implementovaná pomocí [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722).  
  
##  <a name="getsize"></a>CComHeap::GetSize  
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
 Implementovaná pomocí [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226).  
  
##  <a name="reallocate"></a>CComHeap::Reallocate  
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
 Volání [CComHeap::Free](#free) k bezplatným je paměť přidělená touto metodou.  
  
 Implementovaná pomocí [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280).  
  
## <a name="see-also"></a>Viz také  
 [Příklad DynamicConsumer](../../visual-cpp-samples.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CWin32Heap – třída](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap – třída](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap – třída](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
