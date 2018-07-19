---
title: Ccrtheap – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68c99d1ef7b28a9325d59db2144be11fa63cc99f
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883044"
---
# <a name="ccrtheap-class"></a>Ccrtheap – třída
Tato třída implementuje [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí haldy CRT.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CCRTHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CCRTHeap::Allocate](#allocate)|Volejte tuto metodu za účelem přidělení bloku paměti.|  
|[CCRTHeap::Free](#free)|Volejte tuto metodu pro uvolnění bloku paměti přidělené tomuto správci paměti.|  
|[CCRTHeap::GetSize](#getsize)|Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tímto správcem paměti.|  
|[CCRTHeap::Reallocate](#reallocate)|Volejte tuto metodu, aby mohla znovu přidělit paměti přidělené tímto správcem paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `CCRTHeap` implementuje paměti pomocí CRT funkcí přidělení haldy funkcí, včetně [malloc](../../c-runtime-library/reference/malloc.md), [bezplatné](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md), a [_msize –](../../c-runtime-library/reference/msize.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IAtlMemMgr`  
  
 `CCRTHeap`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlmem.h  
  
##  <a name="allocate"></a>  CCRTHeap::Allocate  
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
 Volání [CCRTHeap::Free](#free) nebo [CCRTHeap::Reallocate](#reallocate) k uvolnění paměti přidělené touto metodou.  
  
 Implementované pomocí [malloc](../../c-runtime-library/reference/malloc.md).  
  
##  <a name="free"></a>  CCRTHeap::Free  
 Volejte tuto metodu pro uvolnění bloku paměti přidělené tomuto správci paměti.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Ukazatel na paměť přidělenou dříve metodou tento správce paměti. Hodnota NULL je platnou hodnotu a nemá žádný účinek.  
  
### <a name="remarks"></a>Poznámky  
 Implementované pomocí [bezplatné](../../c-runtime-library/reference/free.md).  
  
##  <a name="getsize"></a>  CCRTHeap::GetSize  
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
 Implementované pomocí [_msize –](../../c-runtime-library/reference/msize.md).  
  
##  <a name="reallocate"></a>  CCRTHeap::Reallocate  
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
 Volání [CCRTHeap::Free](#free) k uvolnění paměti přidělené touto metodou. Implementované pomocí [realloc](../../c-runtime-library/reference/realloc.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)   
 [Ccomheap – třída](../../atl/reference/ccomheap-class.md)   
 [Cwin32heap – třída](../../atl/reference/cwin32heap-class.md)   
 [Clocalheap – třída](../../atl/reference/clocalheap-class.md)   
 [Cglobalheap – třída](../../atl/reference/cglobalheap-class.md)   
 [IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
