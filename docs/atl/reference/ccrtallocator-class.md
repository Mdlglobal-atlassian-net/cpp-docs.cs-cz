---
title: Třída CCRTAllocator
ms.date: 11/04/2016
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
ms.openlocfilehash: 2f6bae3818fa0f1639e0e3cee4e09121580da768
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327168"
---
# <a name="ccrtallocator-class"></a>Třída CCRTAllocator

Tato třída poskytuje metody pro správu paměti pomocí rutinpaměti CRT.

## <a name="syntax"></a>Syntaxe

```
class ATL::CCRTAllocator
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CCRTAllocator::Přidělit](#allocate)|(Statické) Volání této metody přidělit paměť.|
|[CCRTAllocator::Zdarma](#free)|(Statické) Volání této metody k uvolnění paměti.|
|[CCRTAllocator::Přerozdělit](#reallocate)|(Statické) Volání této metody přerozdělit paměti.|

## <a name="remarks"></a>Poznámky

Tato třída se používá [CHeapPtr](../../atl/reference/cheapptr-class.md) poskytnout rutiny přidělení paměti CRT. Třída protějšku [CComAllocator](../../atl/reference/ccomallocator-class.md)poskytuje stejné metody pomocí rutincom.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="ccrtallocatorallocate"></a><a name="allocate"></a>CCRTAllocator::Přidělit

Volání této statické funkce přidělit paměť.

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBajtu bajtů*<br/>
Počet bajtů, které mají být přiděleny.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel void přidělené místo nebo NULL, pokud není k dispozici dostatek paměti.

### <a name="remarks"></a>Poznámky

Přiděluje paměť. Další podrobnosti [najdete v mallocu.](../../c-runtime-library/reference/malloc.md)

## <a name="ccrtallocatorfree"></a><a name="free"></a>CCRTAllocator::Zdarma

Volání této statické funkce k uvolnění paměti.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na přidělenou paměť.

### <a name="remarks"></a>Poznámky

Uvolní přidělenou paměť. Další podrobnosti najdete [zdarma.](../../c-runtime-library/reference/free.md)

## <a name="ccrtallocatorreallocate"></a><a name="reallocate"></a>CCRTAllocator::Přerozdělit

Volání této statické funkce přerozdělit paměť.

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na přidělenou paměť.

*nBajtu bajtů*<br/>
Počet bajtů přerozdělit.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel void přidělené místo nebo NULL, pokud není dostatek paměti.

### <a name="remarks"></a>Poznámky

Změní velikost velikosti přidělené paměti. Další podrobnosti najdete v [tématu realloc.](../../c-runtime-library/reference/realloc.md)

## <a name="see-also"></a>Viz také

[Třída CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Třída CComAllocator](../../atl/reference/ccomallocator-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
