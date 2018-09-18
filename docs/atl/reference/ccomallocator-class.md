---
title: Ccomallocator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f867d3a7ca81d190ee363c7539e56a62004eb377
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088940"
---
# <a name="ccomallocator-class"></a>Ccomallocator – třída

Tato třída poskytuje metody pro správu paměti používá rutiny COM paměti.

## <a name="syntax"></a>Syntaxe

```
class CComAllocator
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComAllocator::Allocate](#allocate)|Volejte tuto statickou metodu přidělení paměti.|
|[CComAllocator::Free](#free)|Volání této statické metody pro uvolnění paměti přidělené.|
|[CComAllocator::Reallocate](#reallocate)|Volání této statické metody, aby mohla znovu přidělit paměti.|

## <a name="remarks"></a>Poznámky

Tato třída používá [ccomheapptr –](../../atl/reference/ccomheapptr-class.md) k poskytnutí paměti modelu COM, rutin přidělení. Třída protějšek [ccrtallocator –](../../atl/reference/ccrtallocator-class.md), poskytuje stejné metody, pomocí rutiny CRT.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="allocate"></a>  CComAllocator::Allocate

Voláním této funkce statické přidělení paměti.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Počet bajtů k přidělení.

### <a name="return-value"></a>Návratová hodnota

Vrací neplatný ukazatel do přiděleného místa nebo hodnota NULL, pokud není k dispozici dostatek paměti.

### <a name="remarks"></a>Poznámky

Přidělí paměť. Zobrazit [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) další podrobnosti.

##  <a name="free"></a>  CComAllocator::Free

Voláním této funkce statických zdarma přidělené paměti.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel do přidělené paměti.

### <a name="remarks"></a>Poznámky

Uvolní přidělené paměti. Zobrazit [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree) další podrobnosti.

##  <a name="reallocate"></a>  CComAllocator::Reallocate

Voláním této funkce statické přidělení paměti.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel do přidělené paměti.

*nBytes*<br/>
Počet bajtů, které mají přidělit jinému uživateli.

### <a name="return-value"></a>Návratová hodnota

Vrací neplatný ukazatel do přiděleného místa nebo hodnota NULL, pokud je nedostatek paměti

### <a name="remarks"></a>Poznámky

Změní velikost přidělené paměti. Zobrazit [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc) další podrobnosti.

## <a name="see-also"></a>Viz také

[CComHeapPtr – třída](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator – třída](../../atl/reference/ccrtallocator-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
