---
title: Ccomheap – třída
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
ms.openlocfilehash: 1a8618bd5146f2906f18cfbaa33894d34598776a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259375"
---
# <a name="ccomheap-class"></a>Ccomheap – třída

Tato třída implementuje [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md) pomocí funkcí přidělení paměti COM.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComHeap::Allocate](#allocate)|Volejte tuto metodu za účelem přidělení bloku paměti.|
|[CComHeap::Free](#free)|Volejte tuto metodu pro uvolnění bloku paměti přidělené tomuto správci paměti.|
|[CComHeap::GetSize](#getsize)|Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tímto správcem paměti.|
|[CComHeap::Reallocate](#reallocate)|Volejte tuto metodu, aby mohla znovu přidělit paměti přidělené tímto správcem paměti.|

## <a name="remarks"></a>Poznámky

`CComHeap` implementuje funkce přidělení paměti pomocí funkce přidělení modelu COM, včetně [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree), [IMalloc::GetSize](/windows/desktop/api/objidlbase/nf-objidlbase-imalloc-getsize)a [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc). Maximální množství paměti, které mohou být přiděleny rovná INT_MAX (2147483647) bajtů.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [iatlmemmgr –](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ATLComMem.h

##  <a name="allocate"></a>  CComHeap::Allocate

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

Volání [CComHeap::Free](#free) nebo [CComHeap::Reallocate](#reallocate) k uvolnění paměti přidělené touto metodou.

Implementované pomocí [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc).

##  <a name="free"></a>  CComHeap::Free

Volejte tuto metodu pro uvolnění bloku paměti přidělené tomuto správci paměti.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na paměť přidělenou dříve metodou tento správce paměti. Hodnota NULL je platnou hodnotu a nemá žádný účinek.

### <a name="remarks"></a>Poznámky

Implementované pomocí [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree).

##  <a name="getsize"></a>  CComHeap::GetSize

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

Implementované pomocí [IMalloc::GetSize](/windows/desktop/api/objidlbase/nf-objidlbase-imalloc-getsize).

##  <a name="reallocate"></a>  CComHeap::Reallocate

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

Volání [CComHeap::Free](#free) k uvolnění paměti přidělené touto metodou.

Implementované pomocí [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>Viz také:

[Příklad DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[CWin32Heap – třída](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap – třída](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap – třída](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap – třída](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
