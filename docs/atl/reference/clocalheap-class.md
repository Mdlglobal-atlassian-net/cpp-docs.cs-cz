---
title: Třída CLocalHeap
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
ms.openlocfilehash: 303e3b85ad11c309f862f59d6ec610701c4ef6db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326762"
---
# <a name="clocalheap-class"></a>Třída CLocalHeap

Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí win32 místní haldy funkce.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CLocalHeap::Přidělit](#allocate)|Volání této metody přidělit blok paměti.|
|[CLocalHeap::Zdarma](#free)|Volání této metody uvolnit blok paměti přidělené tohoto správce paměti.|
|[CLocalHeap::GetSize](#getsize)|Volání této metody získat přidělené velikosti bloku paměti přidělené tohoto správce paměti.|
|[CLocalHeap::Přerozdělit](#reallocate)|Volání této metody přerozdělit paměti přidělené tohoto správce paměti.|

## <a name="remarks"></a>Poznámky

`CLocalHeap`implementuje funkce přidělení paměti pomocí funkcí místní haldy Win32.

> [!NOTE]
> Funkce místní haldy jsou pomalejší než jiné funkce správy paměti a neposkytují tolik funkcí. Proto nové aplikace by měly používat [funkce haldy](/windows/win32/Memory/heap-functions). Ty jsou k dispozici ve třídě [CWin32Heap.](../../atl/reference/cwin32heap-class.md)

## <a name="example"></a>Příklad

Viz příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem.h

## <a name="clocalheapallocate"></a><a name="allocate"></a>CLocalHeap::Přidělit

Volání této metody přidělit blok paměti.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBajtu bajtů*<br/>
Požadovaný počet bajtů v novém bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na začátek bloku nově přidělené paměti.

### <a name="remarks"></a>Poznámky

Volání [CLocalHeap::Free](#free) nebo [CLocalHeap::Reallocate](#reallocate) uvolnit paměť přidělené touto metodou.

Implementováno pomocí [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) s parametrem příznaku LMEM_FIXED.

## <a name="clocalheapfree"></a><a name="free"></a>CLocalHeap::Zdarma

Volání této metody uvolnit blok paměti přidělené tohoto správce paměti.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na paměť dříve přidělené tímto správcem paměti. Null je platná hodnota a neprovede žádné neprovede akci.

### <a name="remarks"></a>Poznámky

Implementováno pomocí [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree).

## <a name="clocalheapgetsize"></a><a name="getsize"></a>CLocalHeap::GetSize

Volání této metody získat přidělené velikosti bloku paměti přidělené tohoto správce paměti.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na paměť dříve přidělené tímto správcem paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost bloku přidělené paměti v bajtech.

### <a name="remarks"></a>Poznámky

Implementováno pomocí [LocalSize](/windows/win32/api/winbase/nf-winbase-localsize).

## <a name="clocalheapreallocate"></a><a name="reallocate"></a>CLocalHeap::Přerozdělit

Volání této metody přerozdělit paměti přidělené tohoto správce paměti.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na paměť dříve přidělené tímto správcem paměti.

*nBajtu bajtů*<br/>
Požadovaný počet bajtů v novém bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na začátek bloku nově přidělené paměti.

### <a name="remarks"></a>Poznámky

Volání [CLocalHeap::Free](#free) uvolnit paměť přidělenou touto metodou.

Implementováno pomocí [LocalReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Třída CWin32HeAP](../../atl/reference/cwin32heap-class.md)<br/>
[Třída CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Třída CCRTHeAP](../../atl/reference/ccrtheap-class.md)<br/>
[Třída IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
