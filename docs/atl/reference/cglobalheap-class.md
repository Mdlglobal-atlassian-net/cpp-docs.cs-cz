---
title: Třída CGlobalHeap | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bef811807c90507184690d1a29d4debd00cc6fda
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363331"
---
# <a name="cglobalheap-class"></a>CGlobalHeap – třída
Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí globální haldy Win32.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CGlobalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CGlobalHeap::Allocate](#allocate)|Voláním této metody lze přidělit blok paměti.|  
|[CGlobalHeap::Free](#free)|Volejte tuto metodu k bezplatným blok paměti přidělené tomuto správci paměti.|  
|[CGlobalHeap::GetSize](#getsize)|Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tomuto správci paměti.|  
|[CGlobalHeap::Reallocate](#reallocate)|Volejte tuto metodu a znovu přidělte paměti přidělené tomuto správci paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `CGlobalHeap` implementuje pomocí funkcí globální haldy Win32 funkce přidělení paměti.  
  
> [!NOTE]
>  Funkce globální haldy jsou nižší než jiné funkce správy paměti a neposkytuje jako řadu funkcí. Proto měli používat nové aplikace [haldy funkce](http://msdn.microsoft.com/library/windows/desktop/aa366711). Tyto jsou k dispozici v [CWin32Heap](../../atl/reference/cwin32heap-class.md) třídy. Globální funkce jsou nadále používány DDE a funkce schránky.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IAtlMemMgr`  
  
 `CGlobalHeap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlmem.h  
  
##  <a name="allocate"></a>  CGlobalHeap::Allocate  
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
 Volání [CGlobalHeap::Free](#free) nebo [CGlobalHeap::Reallocate](#reallocate) k bezplatným je paměť přidělená touto metodou.  
  
 Implementovaná pomocí [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) s parametrem příznak **GMEM_FIXED**.  
  
##  <a name="free"></a>  CGlobalHeap::Free  
 Volejte tuto metodu k bezplatným blok paměti přidělené tomuto správci paměti.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na paměti dříve přidělené tomuto správci paměti. NULL není platná hodnota a neprovede žádnou akci.  
  
### <a name="remarks"></a>Poznámky  
 Implementovaná pomocí [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579).  
  
##  <a name="getsize"></a>  CGlobalHeap::GetSize  
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
 Implementovaná pomocí [GlobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593).  
  
##  <a name="reallocate"></a>  CGlobalHeap::Reallocate  
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
 Volání [CGlobalHeap::Free](#free) k bezplatným je paměť přidělená touto metodou.  
  
 Implementovaná pomocí [GlobalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CComHeap – třída](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap – třída](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap – třída](../../atl/reference/clocalheap-class.md)   
 [CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
