---
title: CComAllocator – třída
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
ms.openlocfilehash: de302c7a58bf1b15e63e7cd391621ed9558e5a70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497587"
---
# <a name="ccomallocator-class"></a>CComAllocator – třída

Tato třída poskytuje metody pro správu paměti pomocí rutin paměti modelu COM.

## <a name="syntax"></a>Syntaxe

```
class CComAllocator
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComAllocator:: allocate](#allocate)|Zavolejte tuto statickou metodu pro přidělení paměti.|
|[CComAllocator:: Free](#free)|Zavolejte tuto statickou metodu pro uvolnění přidělené paměti.|
|[CComAllocator:: realokaci](#reallocate)|Zavolejte tuto statickou metodu pro opětovné přidělení paměti.|

## <a name="remarks"></a>Poznámky

Tuto třídu používá [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) k poskytování rutin přidělení paměti com. Třída protějšek [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)poskytuje stejné metody, které používají rutiny CRT.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="allocate"></a>CComAllocator:: allocate

Zavolejte tuto statickou funkci pro přidělení paměti.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Počet bajtů, které mají být přiděleny.

### <a name="return-value"></a>Návratová hodnota

Vrátí void ukazatel na přidělený prostor nebo hodnotu NULL, pokud není k dispozici dostatek paměti.

### <a name="remarks"></a>Poznámky

Přidělí paměť. Další podrobnosti najdete v tématu [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) .

##  <a name="free"></a>CComAllocator:: Free

Zavolejte tuto statickou funkci pro uvolnění přidělené paměti.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na přidělenou paměť.

### <a name="remarks"></a>Poznámky

Uvolní přidělenou paměť. Další podrobnosti najdete v tématu [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) .

##  <a name="reallocate"></a>CComAllocator:: realokaci

Zavolejte tuto statickou funkci pro opětovné přidělení paměti.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel na přidělenou paměť.

*nBytes*<br/>
Počet bajtů, které se mají znovu přidělit

### <a name="return-value"></a>Návratová hodnota

Vrátí void ukazatel na přidělený prostor nebo hodnotu NULL, pokud není dostatek paměti.

### <a name="remarks"></a>Poznámky

Změní velikost přidělené paměti. Další podrobnosti najdete v tématu [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc) .

## <a name="see-also"></a>Viz také:

[CComHeapPtr – třída](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator – třída](../../atl/reference/ccrtallocator-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
