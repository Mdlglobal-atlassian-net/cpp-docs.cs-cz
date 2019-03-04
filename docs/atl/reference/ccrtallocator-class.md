---
title: Ccrtallocator – třída
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
ms.openlocfilehash: c08d594e1c0f4d532f46961e266bf6ced98c51b2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287359"
---
# <a name="ccrtallocator-class"></a>Ccrtallocator – třída

Tato třída poskytuje metody pro správu paměti používá rutiny paměti CRT.

## <a name="syntax"></a>Syntaxe

```
class ATL::CCRTAllocator
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CCRTAllocator::Allocate](#allocate)|(Statické) Volejte tuto metodu za účelem přidělení paměti.|
|[CCRTAllocator::Free](#free)|(Statické) Volejte tuto metodu za účelem uvolnění paměti.|
|[CCRTAllocator::Reallocate](#reallocate)|(Statické) Voláním této metody lze znovu přidělit paměti.|

## <a name="remarks"></a>Poznámky

Tato třída používá [cheapptr –](../../atl/reference/cheapptr-class.md) k poskytnutí paměti CRT rutiny přidělení. Třída protějšek [ccomallocator –](../../atl/reference/ccomallocator-class.md), poskytuje stejné metody, pomocí modelu COM, rutin.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

##  <a name="allocate"></a>  CCRTAllocator::Allocate

Voláním této funkce statické přidělení paměti.

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Počet bajtů k přidělení.

### <a name="return-value"></a>Návratová hodnota

Vrací neplatný ukazatel do přiděleného místa nebo hodnota NULL, pokud není k dispozici dostatek paměti.

### <a name="remarks"></a>Poznámky

Přidělí paměť. Zobrazit [malloc](../../c-runtime-library/reference/malloc.md) další podrobnosti.

##  <a name="free"></a>  CCRTAllocator::Free

Voláním této funkce statických k uvolnění paměti.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel do přidělené paměti.

### <a name="remarks"></a>Poznámky

Uvolní přidělené paměti. Zobrazit [bezplatné](../../c-runtime-library/reference/free.md) další podrobnosti.

##  <a name="reallocate"></a>  CCRTAllocator::Reallocate

Voláním této funkce statické přidělení paměti.

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel do přidělené paměti.

*nBytes*<br/>
Počet bajtů, které mají přidělit jinému uživateli.

### <a name="return-value"></a>Návratová hodnota

Vrací neplatný ukazatel do přiděleného místa nebo hodnota NULL, pokud není dostatek paměti.

### <a name="remarks"></a>Poznámky

Změní velikost přidělené paměti. Zobrazit [realloc](../../c-runtime-library/reference/realloc.md) další podrobnosti.

## <a name="see-also"></a>Viz také:

[CHeapPtr – třída](../../atl/reference/cheapptr-class.md)<br/>
[CComAllocator – třída](../../atl/reference/ccomallocator-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
