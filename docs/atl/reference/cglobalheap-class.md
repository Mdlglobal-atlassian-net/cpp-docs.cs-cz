---
title: Třída CGlobalHeap
ms.date: 11/04/2016
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
ms.openlocfilehash: d596fd51c1bf33f606c1f14c9e8dbd2f1926c7f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326943"
---
# <a name="cglobalheap-class"></a>Třída CGlobalHeap

Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí win32 globální haldy funkce.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CGlobalHeap::Přidělit](#allocate)|Volání této metody přidělit blok paměti.|
|[CGlobalHeap::Zdarma](#free)|Volání této metody uvolnit blok paměti přidělené tohoto správce paměti.|
|[CGlobalHeap::GetSize](#getsize)|Volání této metody získat přidělené velikosti bloku paměti přidělené tohoto správce paměti.|
|[CGlobalHeap::Přerozdělit](#reallocate)|Volání této metody přerozdělit paměti přidělené tohoto správce paměti.|

## <a name="remarks"></a>Poznámky

`CGlobalHeap`implementuje funkce přidělení paměti pomocí win32 globální haldy funkce.

> [!NOTE]
> Globální haldy funkce jsou pomalejší než jiné funkce správy paměti a neposkytují tolik funkcí. Proto nové aplikace by měly používat [funkce haldy](/windows/win32/Memory/heap-functions). Ty jsou k dispozici ve třídě [CWin32Heap.](../../atl/reference/cwin32heap-class.md) Globální funkce jsou stále používány DDE a funkce schránky.

## <a name="example"></a>Příklad

Viz příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem.h

## <a name="cglobalheapallocate"></a><a name="allocate"></a>CGlobalHeap::Přidělit

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

Volání [CGlobalHeap::Free](#free) nebo [CGlobalHeap::Reallocate](#reallocate) uvolnit paměť přidělené touto metodou.

Implementováno pomocí [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) s parametrem příznaku GMEM_FIXED.

## <a name="cglobalheapfree"></a><a name="free"></a>CGlobalHeap::Zdarma

Volání této metody uvolnit blok paměti přidělené tohoto správce paměti.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na paměť dříve přidělené tímto správcem paměti. Null je platná hodnota a neprovede žádné neprovede akci.

### <a name="remarks"></a>Poznámky

Implementováno pomocí [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree).

## <a name="cglobalheapgetsize"></a><a name="getsize"></a>CGlobalHeap::GetSize

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

Implementováno pomocí [GlobalSize](/windows/win32/api/winbase/nf-winbase-globalsize).

## <a name="cglobalheapreallocate"></a><a name="reallocate"></a>CGlobalHeap::Přerozdělit

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

Volání [CGlobalHeap::Free](#free) uvolnit paměť přidělené touto metodou.

Implementováno pomocí [GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Třída CWin32HeAP](../../atl/reference/cwin32heap-class.md)<br/>
[Třída CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Třída CCRTHeAP](../../atl/reference/ccrtheap-class.md)<br/>
[Třída IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
