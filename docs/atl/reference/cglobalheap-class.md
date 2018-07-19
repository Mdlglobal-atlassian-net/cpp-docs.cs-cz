---
title: Cglobalheap – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 1f3113cf4176c3f582a210e89e732d5e0d92b62d
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882829"
---
# <a name="cglobalheap-class"></a>Cglobalheap – třída
Tato třída implementuje [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md) pomocí funkce globální haldy Win32.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CGlobalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CGlobalHeap::Allocate](#allocate)|Volejte tuto metodu za účelem přidělení bloku paměti.|  
|[CGlobalHeap::Free](#free)|Volejte tuto metodu pro uvolnění bloku paměti přidělené tomuto správci paměti.|  
|[CGlobalHeap::GetSize](#getsize)|Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tímto správcem paměti.|  
|[CGlobalHeap::Reallocate](#reallocate)|Volejte tuto metodu, aby mohla znovu přidělit paměti přidělené tímto správcem paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `CGlobalHeap` implementuje funkce přidělení paměti pomocí funkce globální haldy Win32.  
  
> [!NOTE]
>  Funkce globální haldy jsou pomalejší než jiné funkce správy paměti a neposkytuje tolik funkcí. Proto měli používat nové aplikace [haldy funkce](http://msdn.microsoft.com/library/windows/desktop/aa366711). Tyto jsou dostupné v [CWin32Heap](../../atl/reference/cwin32heap-class.md) třídy. Globální funkce se stále používají DDE a funkce schránky.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IAtlMemMgr`  
  
 `CGlobalHeap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlmem.h  
  
##  <a name="allocate"></a>  CGlobalHeap::Allocate  
 Volejte tuto metodu za účelem přidělení bloku paměti.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nBytes*  
 Požadovaný počet bajtů v nového bloku paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na začátek bloku nově přidělenou paměť.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CGlobalHeap::Free](#free) nebo [CGlobalHeap::Reallocate](#reallocate) k uvolnění paměti přidělené touto metodou.  
  
 Implementované pomocí [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) s parametrem příznak GMEM_FIXED.  
  
##  <a name="free"></a>  CGlobalHeap::Free  
 Volejte tuto metodu pro uvolnění bloku paměti přidělené tomuto správci paměti.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Ukazatel na paměť přidělenou dříve metodou tento správce paměti. Hodnota NULL je platnou hodnotu a nemá žádný účinek.  
  
### <a name="remarks"></a>Poznámky  
 Implementované pomocí [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579).  
  
##  <a name="getsize"></a>  CGlobalHeap::GetSize  
 Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tímto správcem paměti.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Ukazatel na paměť přidělenou dříve metodou tento správce paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí velikost bloku přidělené paměti v bajtech.  
  
### <a name="remarks"></a>Poznámky  
 Implementované pomocí [GlobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593).  
  
##  <a name="reallocate"></a>  CGlobalHeap::Reallocate  
 Volejte tuto metodu, aby mohla znovu přidělit paměti přidělené tímto správcem paměti.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Ukazatel na paměť přidělenou dříve metodou tento správce paměti.  
  
 *nBytes*  
 Požadovaný počet bajtů v nového bloku paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na začátek bloku nově přidělenou paměť.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CGlobalHeap::Free](#free) k uvolnění paměti přidělené touto metodou.  
  
 Implementované pomocí [GlobalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)   
 [Ccomheap – třída](../../atl/reference/ccomheap-class.md)   
 [Cwin32heap – třída](../../atl/reference/cwin32heap-class.md)   
 [Clocalheap – třída](../../atl/reference/clocalheap-class.md)   
 [Ccrtheap – třída](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
