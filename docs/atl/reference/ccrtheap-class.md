---
title: Třída CCRTHeAP
ms.date: 11/04/2016
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
ms.openlocfilehash: caf5508079332689c2fff42f130951375dc35512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327166"
---
# <a name="ccrtheap-class"></a>Třída CCRTHeAP

Tato třída implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) pomocí funkce haldy CRT.

## <a name="syntax"></a>Syntaxe

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CCRTHeAP::Přidělit](#allocate)|Volání této metody přidělit blok paměti.|
|[CCRTHeAP::Zdarma](#free)|Volání této metody uvolnit blok paměti přidělené tohoto správce paměti.|
|[CCRTHeAP::GetSize](#getsize)|Volání této metody získat přidělené velikosti bloku paměti přidělené tohoto správce paměti.|
|[CCRTHeAP::Přerozdělit](#reallocate)|Volání této metody přerozdělit paměti přidělené tohoto správce paměti.|

## <a name="remarks"></a>Poznámky

`CCRTHeap`implementuje funkce přidělení paměti pomocí funkcí haldy CRT, včetně [malloc](../../c-runtime-library/reference/malloc.md), [free](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md)a [_msize](../../c-runtime-library/reference/msize.md).

## <a name="example"></a>Příklad

Viz příklad pro [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlmem.h

## <a name="ccrtheapallocate"></a><a name="allocate"></a>CCRTHeAP::Přidělit

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

Volání [CCRTHeap::Free](#free) nebo [CCRTHeap::Reallocate](#reallocate) uvolnit paměť přidělené touto metodou.

Implementováno pomocí [malloc](../../c-runtime-library/reference/malloc.md).

## <a name="ccrtheapfree"></a><a name="free"></a>CCRTHeAP::Zdarma

Volání této metody uvolnit blok paměti přidělené tohoto správce paměti.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel na paměť dříve přidělené tímto správcem paměti. Null je platná hodnota a neprovede žádné neprovede akci.

### <a name="remarks"></a>Poznámky

Realizováno pomocí [volného](../../c-runtime-library/reference/free.md).

## <a name="ccrtheapgetsize"></a><a name="getsize"></a>CCRTHeAP::GetSize

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

Implementováno pomocí [_msize](../../c-runtime-library/reference/msize.md).

## <a name="ccrtheapreallocate"></a><a name="reallocate"></a>CCRTHeAP::Přerozdělit

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

Volání [CCRTHeap::Free](#free) uvolnit paměť přidělenou touto metodou. Implementováno pomocí [relokace](../../c-runtime-library/reference/realloc.md).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třída CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Třída CWin32HeAP](../../atl/reference/cwin32heap-class.md)<br/>
[Třída CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Třída CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Třída IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
