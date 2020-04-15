---
title: Třída CComHeap
ms.date: 11/04/2016
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
ms.openlocfilehash: a38d1147e718870c03af84ec1487e226805b956e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327825"
---
# <a name="ccomheap-class"></a>Třída CComHeap

Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí přidělení paměti COM.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComHeap::Přidělit](#allocate)|Volání této metody přidělit blok paměti.|
|[CComHeap::Zdarma](#free)|Volání této metody uvolnit blok paměti přidělené tohoto správce paměti.|
|[CComHeap::GetSize](#getsize)|Volání této metody získat přidělené velikosti bloku paměti přidělené tohoto správce paměti.|
|[CComHeap::Přerozdělit](#reallocate)|Volání této metody přerozdělit paměti přidělené tohoto správce paměti.|

## <a name="remarks"></a>Poznámky

`CComHeap`implementuje funkce přidělení paměti pomocí alokačních funkcí COM, včetně [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree), [IMalloc::GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)a [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc). Maximální velikost paměti, která může být přidělena, se rovná INT_MAX (2147483647) bajtů.

## <a name="example"></a>Příklad

Viz příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ATLComMem.h

## <a name="ccomheapallocate"></a><a name="allocate"></a>CComHeap::Přidělit

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

Volání [CComHeap::Free](#free) nebo [CComHeap::Reallocate](#reallocate) uvolnit paměť přidělené touto metodou.

Implementováno pomocí [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc).

## <a name="ccomheapfree"></a><a name="free"></a>CComHeap::Zdarma

Volání této metody uvolnit blok paměti přidělené tohoto správce paměti.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na paměť dříve přidělené tímto správcem paměti. Null je platná hodnota a neprovede žádné neprovede akci.

### <a name="remarks"></a>Poznámky

Implementováno pomocí [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree).

## <a name="ccomheapgetsize"></a><a name="getsize"></a>CComHeap::GetSize

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

Implementováno pomocí [IMalloc::GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize).

## <a name="ccomheapreallocate"></a><a name="reallocate"></a>CComHeap::Přerozdělit

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

Volání [CComHeap::Free](#free) uvolnit paměť přidělenou touto metodou.

Implementováno pomocí [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>Viz také

[Ukázka dynamického spotřebitele](../../overview/visual-cpp-samples.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CWin32HeAP](../../atl/reference/cwin32heap-class.md)<br/>
[Třída CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Třída CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Třída CCRTHeAP](../../atl/reference/ccrtheap-class.md)<br/>
[Třída IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
