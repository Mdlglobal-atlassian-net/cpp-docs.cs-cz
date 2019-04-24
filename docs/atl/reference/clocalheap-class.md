---
title: Clocalheap – třída
ms.date: 11/04/2016
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
ms.openlocfilehash: 53288bea8a50f62437eab4dd81d5d816abf78f44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258829"
---
# <a name="clocalheap-class"></a>Clocalheap – třída

Tato třída implementuje [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí lokální haldy Win32.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CLocalHeap::Allocate](#allocate)|Volejte tuto metodu za účelem přidělení bloku paměti.|
|[CLocalHeap::Free](#free)|Volejte tuto metodu pro uvolnění bloku paměti přidělené tomuto správci paměti.|
|[CLocalHeap::GetSize](#getsize)|Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tímto správcem paměti.|
|[CLocalHeap::Reallocate](#reallocate)|Volejte tuto metodu, aby mohla znovu přidělit paměti přidělené tímto správcem paměti.|

## <a name="remarks"></a>Poznámky

`CLocalHeap` implementuje funkce přidělení paměti pomocí funkce lokální haldy Win32.

> [!NOTE]
>  Funkce lokální haldy jsou pomalejší než jiné funkce správy paměti a neposkytuje tolik funkcí. Proto měli používat nové aplikace [haldy funkce](/windows/desktop/Memory/heap-functions). Tyto jsou dostupné v [CWin32Heap](../../atl/reference/cwin32heap-class.md) třídy.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem.h

##  <a name="allocate"></a>  CLocalHeap::Allocate

Volejte tuto metodu za účelem přidělení bloku paměti.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Požadovaný počet bajtů v nového bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na začátek bloku nově přidělenou paměť.

### <a name="remarks"></a>Poznámky

Volání [CLocalHeap::Free](#free) nebo [CLocalHeap::Reallocate](#reallocate) k uvolnění paměti přidělené touto metodou.

Implementované pomocí [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc) s parametrem příznak LMEM_FIXED.

##  <a name="free"></a>  CLocalHeap::Free

Volejte tuto metodu pro uvolnění bloku paměti přidělené tomuto správci paměti.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť přidělenou dříve metodou tento správce paměti. Hodnota NULL je platnou hodnotu a nemá žádný účinek.

### <a name="remarks"></a>Poznámky

Implementované pomocí [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree).

##  <a name="getsize"></a>  CLocalHeap::GetSize

Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tímto správcem paměti.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť přidělenou dříve metodou tento správce paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost bloku přidělené paměti v bajtech.

### <a name="remarks"></a>Poznámky

Implementované pomocí [LocalSize](/windows/desktop/api/winbase/nf-winbase-localsize).

##  <a name="reallocate"></a>  CLocalHeap::Reallocate

Volejte tuto metodu, aby mohla znovu přidělit paměti přidělené tímto správcem paměti.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť přidělenou dříve metodou tento správce paměti.

*nBytes*<br/>
Požadovaný počet bajtů v nového bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na začátek bloku nově přidělenou paměť.

### <a name="remarks"></a>Poznámky

Volání [CLocalHeap::Free](#free) k uvolnění paměti přidělené touto metodou.

Implementované pomocí [LocalReAlloc](/windows/desktop/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[CComHeap – třída](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap – třída](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap – třída](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
