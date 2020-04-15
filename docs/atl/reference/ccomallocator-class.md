---
title: Třída CComAllocator
ms.date: 11/04/2016
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
ms.openlocfilehash: 165cdb8b0b16a4872214f4556c26ee141e6a4d89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321144"
---
# <a name="ccomallocator-class"></a>Třída CComAllocator

Tato třída poskytuje metody pro správu paměti pomocí rutinpaměti COM.

## <a name="syntax"></a>Syntaxe

```
class CComAllocator
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComAllocator::Přidělit](#allocate)|Volání této statické metody přidělit paměť.|
|[CComAllocator::Zdarma](#free)|Volání této statické metody k uvolnění přidělené paměti.|
|[CComAllocator::Přerozdělit](#reallocate)|Volání této statické metody přerozdělit paměť.|

## <a name="remarks"></a>Poznámky

Tato třída je používána [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) k poskytování rutin přidělení paměti COM. Třída protějšku [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)poskytuje stejné metody pomocí rutin CRT.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomallocatorallocate"></a><a name="allocate"></a>CComAllocator::Přidělit

Volání této statické funkce přidělit paměť.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBajtu bajtů*<br/>
Počet bajtů, které mají být přiděleny.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel void přidělené místo nebo NULL, pokud není k dispozici dostatek paměti.

### <a name="remarks"></a>Poznámky

Přiděluje paměť. Další podrobnosti najdete [v tématu CoTaskMemAlloc.](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)

## <a name="ccomallocatorfree"></a><a name="free"></a>CComAllocator::Zdarma

Volání této statické funkce k uvolnění přidělené paměti.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na přidělenou paměť.

### <a name="remarks"></a>Poznámky

Uvolní přidělenou paměť. Viz [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) pro více informací.

## <a name="ccomallocatorreallocate"></a><a name="reallocate"></a>CComAllocator::Přerozdělit

Volání této statické funkce přerozdělit paměť.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na přidělenou paměť.

*nBajtu bajtů*<br/>
Počet bajtů přerozdělit.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel void přidělené místo nebo NULL, pokud není dostatek paměti

### <a name="remarks"></a>Poznámky

Změní velikost velikosti přidělené paměti. Další podrobnosti najdete [v tématu CoTaskMemRealloc.](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

## <a name="see-also"></a>Viz také

[Třída CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Třída CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
