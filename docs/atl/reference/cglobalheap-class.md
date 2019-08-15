---
title: CGlobalHeap – třída
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
ms.openlocfilehash: 2b5aa09357ddcc77b6b10de58545bea86eff2488
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496754"
---
# <a name="cglobalheap-class"></a>CGlobalHeap – třída

Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí globálních funkcí haldy Win32.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CGlobalHeap:: allocate](#allocate)|Voláním této metody přidělíte blok paměti.|
|[CGlobalHeap:: Free](#free)|Voláním této metody uvolníte blok paměti přidělený tímto správcem paměti.|
|[CGlobalHeap:: GetSize](#getsize)|Voláním této metody získáte přidělenou velikost bloku paměti přiděleného tímto správcem paměti.|
|[CGlobalHeap:: realokaci](#reallocate)|Zavolejte tuto metodu pro opětovné přidělení paměti přidělené tímto správcem paměti.|

## <a name="remarks"></a>Poznámky

`CGlobalHeap`implementuje funkce přidělování paměti pomocí globálních funkcí haldy Win32.

> [!NOTE]
>  Globální funkce haldy jsou pomalejší než jiné funkce správy paměti a neposkytují tolik funkcí. Proto by nové aplikace měly používat [funkce haldy](/windows/win32/Memory/heap-functions). Jsou k dispozici ve třídě [CWin32Heap](../../atl/reference/cwin32heap-class.md) . Globální funkce jsou stále používány funkcí DDE a Clipboard.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem. h

##  <a name="allocate"></a>CGlobalHeap:: allocate

Voláním této metody přidělíte blok paměti.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Požadovaný počet bajtů v novém bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na začátek nově přiděleného bloku paměti.

### <a name="remarks"></a>Poznámky

Zavolejte [CGlobalHeap:: Free](#free) nebo [CGlobalHeap:: realokaci](#reallocate) pro uvolnění paměti přidělené touto metodou.

Implementováno pomocí [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) s parametrem příznaku GMEM_FIXED.

##  <a name="free"></a>CGlobalHeap:: Free

Voláním této metody uvolníte blok paměti přidělený tímto správcem paměti.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť, která byla dříve přidělena tímto správcem paměti. Hodnota NULL je platná a neprovádí žádnou akci.

### <a name="remarks"></a>Poznámky

Implementováno pomocí [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree).

##  <a name="getsize"></a>CGlobalHeap:: GetSize

Voláním této metody získáte přidělenou velikost bloku paměti přiděleného tímto správcem paměti.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť, která byla dříve přidělena tímto správcem paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí velikost přiděleného bloku paměti v bajtech.

### <a name="remarks"></a>Poznámky

Implementováno pomocí [GlobalSize](/windows/win32/api/winbase/nf-winbase-globalsize).

##  <a name="reallocate"></a>CGlobalHeap:: realokaci

Zavolejte tuto metodu pro opětovné přidělení paměti přidělené tímto správcem paměti.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť, která byla dříve přidělena tímto správcem paměti.

*nBytes*<br/>
Požadovaný počet bajtů v novém bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na začátek nově přiděleného bloku paměti.

### <a name="remarks"></a>Poznámky

Volání [CGlobalHeap:: Free](#free) uvolní paměť přidělené touto metodou.

Implementováno pomocí [GlobalRealloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[CComHeap – třída](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap – třída](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap – třída](../../atl/reference/clocalheap-class.md)<br/>
[CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
