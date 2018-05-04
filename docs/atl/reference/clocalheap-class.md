---
title: Třída CLocalHeap | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 299c672d65d7568539473dfc284833c2583a2220
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="clocalheap-class"></a>CLocalHeap – třída
Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí lokální haldy Win32.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CLocalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CLocalHeap::Allocate](#allocate)|Voláním této metody lze přidělit blok paměti.|  
|[CLocalHeap::Free](#free)|Volejte tuto metodu k bezplatným blok paměti přidělené tomuto správci paměti.|  
|[CLocalHeap::GetSize](#getsize)|Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tomuto správci paměti.|  
|[CLocalHeap::Reallocate](#reallocate)|Volejte tuto metodu a znovu přidělte paměti přidělené tomuto správci paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `CLocalHeap` implementuje pomocí funkcí lokální haldy Win32 funkce přidělení paměti.  
  
> [!NOTE]
>  Funkce lokální haldy jsou nižší než jiné funkce správy paměti a neposkytuje jako řadu funkcí. Proto měli používat nové aplikace [haldy funkce](http://msdn.microsoft.com/library/windows/desktop/aa366711). Tyto jsou k dispozici v [CWin32Heap](../../atl/reference/cwin32heap-class.md) třídy.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IAtlMemMgr`  
  
 `CLocalHeap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlmem.h  
  
##  <a name="allocate"></a>  CLocalHeap::Allocate  
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
 Volání [CLocalHeap::Free](#free) nebo [CLocalHeap::Reallocate](#reallocate) k bezplatným je paměť přidělená touto metodou.  
  
 Implementovaná pomocí [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723) s parametrem příznak **LMEM_FIXED**.  
  
##  <a name="free"></a>  CLocalHeap::Free  
 Volejte tuto metodu k bezplatným blok paměti přidělené tomuto správci paměti.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel na paměti dříve přidělené tomuto správci paměti. NULL není platná hodnota a neprovede žádnou akci.  
  
### <a name="remarks"></a>Poznámky  
 Implementovaná pomocí [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730).  
  
##  <a name="getsize"></a>  CLocalHeap::GetSize  
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
 Implementovaná pomocí [LocalSize](http://msdn.microsoft.com/library/windows/desktop/aa366745).  
  
##  <a name="reallocate"></a>  CLocalHeap::Reallocate  
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
 Volání [CLocalHeap::Free](#free) k bezplatným je paměť přidělená touto metodou.  
  
 Implementovaná pomocí [LocalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366742).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CComHeap – třída](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap – třída](../../atl/reference/cwin32heap-class.md)   
 [CGlobalHeap – třída](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
