---
title: CComHeap – třída
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
ms.openlocfilehash: 1ded73047b895a44a22bdd5730886f7fc088c77a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497349"
---
# <a name="ccomheap-class"></a>CComHeap – třída

Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí přidělování paměti com.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComHeap:: allocate](#allocate)|Voláním této metody přidělíte blok paměti.|
|[CComHeap:: Free](#free)|Voláním této metody uvolníte blok paměti přidělený tímto správcem paměti.|
|[CComHeap:: GetSize](#getsize)|Voláním této metody získáte přidělenou velikost bloku paměti přiděleného tímto správcem paměti.|
|[CComHeap:: realokaci](#reallocate)|Zavolejte tuto metodu pro opětovné přidělení paměti přidělené tímto správcem paměti.|

## <a name="remarks"></a>Poznámky

`CComHeap`implementuje funkce přidělování paměti pomocí funkcí alokace COM, včetně [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree), [unalokace:: GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)a [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc). Maximální velikost paměti, která se dá přidělit, se rovná INT_MAX (2147483647) bajtů.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>Požadavky

**Hlaviček** ATLComMem.h

##  <a name="allocate"></a>CComHeap:: allocate

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

Zavolejte [CComHeap:: Free](#free) nebo [CComHeap:: realokaci](#reallocate) pro uvolnění paměti přidělené touto metodou.

Implementováno pomocí [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc).

##  <a name="free"></a>CComHeap:: Free

Voláním této metody uvolníte blok paměti přidělený tímto správcem paměti.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť, která byla dříve přidělena tímto správcem paměti. Hodnota NULL je platná a neprovádí žádnou akci.

### <a name="remarks"></a>Poznámky

Implementováno pomocí [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree).

##  <a name="getsize"></a>CComHeap:: GetSize

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

Implementováno pomocí [nepřidělení:: GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize).

##  <a name="reallocate"></a>CComHeap:: realokaci

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

Volání [CComHeap:: Free](#free) uvolní paměť přidělené touto metodou.

Implementováno pomocí [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>Viz také:

[Ukázka DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[CWin32Heap – třída](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap – třída](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap – třída](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
