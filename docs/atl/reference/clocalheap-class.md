---
title: CLocalHeap – třída
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
ms.openlocfilehash: a302ba4ea55c42ce214c8de4a24be843d6cb1b9f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496751"
---
# <a name="clocalheap-class"></a>CLocalHeap – třída

Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí lokální haldy Win32.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CLocalHeap:: allocate](#allocate)|Voláním této metody přidělíte blok paměti.|
|[CLocalHeap:: Free](#free)|Voláním této metody uvolníte blok paměti přidělený tímto správcem paměti.|
|[CLocalHeap:: GetSize](#getsize)|Voláním této metody získáte přidělenou velikost bloku paměti přiděleného tímto správcem paměti.|
|[CLocalHeap:: realokaci](#reallocate)|Zavolejte tuto metodu pro opětovné přidělení paměti přidělené tímto správcem paměti.|

## <a name="remarks"></a>Poznámky

`CLocalHeap`implementuje funkce přidělování paměti pomocí funkcí lokální haldy Win32.

> [!NOTE]
>  Funkce lokální haldy jsou pomalejší než jiné funkce správy paměti a neposkytují tolik funkcí. Proto by nové aplikace měly používat [funkce haldy](/windows/win32/Memory/heap-functions). Jsou k dispozici ve třídě [CWin32Heap](../../atl/reference/cwin32heap-class.md) .

## <a name="example"></a>Příklad

Podívejte se na příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem. h

##  <a name="allocate"></a>CLocalHeap:: allocate

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

Zavolejte [CLocalHeap:: Free](#free) nebo [CLocalHeap:: realokaci](#reallocate) pro uvolnění paměti přidělené touto metodou.

Implementováno pomocí [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) s parametrem příznaku LMEM_FIXED.

##  <a name="free"></a>CLocalHeap:: Free

Voláním této metody uvolníte blok paměti přidělený tímto správcem paměti.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť, která byla dříve přidělena tímto správcem paměti. Hodnota NULL je platná a neprovádí žádnou akci.

### <a name="remarks"></a>Poznámky

Implementováno pomocí [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree).

##  <a name="getsize"></a>CLocalHeap:: GetSize

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

Implementováno pomocí [LocalSize](/windows/win32/api/winbase/nf-winbase-localsize).

##  <a name="reallocate"></a>CLocalHeap:: realokaci

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

Volání [CLocalHeap:: Free](#free) uvolní paměť přidělené touto metodou.

Implementováno pomocí [LocalReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[CComHeap – třída](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap – třída](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap – třída](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
