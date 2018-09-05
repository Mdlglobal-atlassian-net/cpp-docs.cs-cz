---
title: Ccomheap – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf09696f6a13c11fbb37fa6e89ccb9b1241cadd0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751540"
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

*nBytes*  
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

*p*  
Ukazatel na paměť přidělenou dříve metodou tento správce paměti. Hodnota NULL je platnou hodnotu a nemá žádný účinek.

### <a name="remarks"></a>Poznámky

Implementované pomocí [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree).

##  <a name="getsize"></a>  CComHeap::GetSize

Volejte tuto metodu za účelem získání přidělená velikost bloku paměti přidělené tímto správcem paměti.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*  
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

*p*  
Ukazatel na paměť přidělenou dříve metodou tento správce paměti.

*nBytes*  
Požadovaný počet bajtů v nového bloku paměti.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na začátek bloku nově přidělenou paměť.

### <a name="remarks"></a>Poznámky

Volání [CComHeap::Free](#free) k uvolnění paměti přidělené touto metodou.

Implementované pomocí [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>Viz také

[Příklad DynamicConsumer](../../visual-cpp-samples.md)   
[Přehled tříd](../../atl/atl-class-overview.md)   
[Cwin32heap – třída](../../atl/reference/cwin32heap-class.md)   
[Clocalheap – třída](../../atl/reference/clocalheap-class.md)   
[Cglobalheap – třída](../../atl/reference/cglobalheap-class.md)   
[Ccrtheap – třída](../../atl/reference/ccrtheap-class.md)   
[IAtlMemMgr – třída](../../atl/reference/iatlmemmgr-class.md)
