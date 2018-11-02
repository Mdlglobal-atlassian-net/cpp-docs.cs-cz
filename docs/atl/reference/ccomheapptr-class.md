---
title: Ccomheapptr – třída
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: eaa21700f63ae07565dba4b8b3b5dabac69e0168
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553731"
---
# <a name="ccomheapptr-class"></a>Ccomheapptr – třída

Třída inteligentní ukazatel pro správu haldy ukazatele.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu ukládaly na haldě.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|Konstruktor|

## <a name="remarks"></a>Poznámky

`CComHeapPtr` je odvozen od `CHeapPtr`, ale používá [ccomallocator –](../../atl/reference/ccomallocator-class.md) přidělení paměti pomocí modelu COM, rutin. Zobrazit [cheapptr –](../../atl/reference/cheapptr-class.md) a [cheapptrbase –](../../atl/reference/cheapptrbase-class.md) pro metody, které jsou k dispozici.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cheapptrbase –](../../atl/reference/cheapptrbase-class.md)

[Cheapptr –](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="ccomheapptr"></a>  CComHeapPtr::CComHeapPtr

Konstruktor

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>Parametry

*pData*<br/>
Existující objekt `CComHeapPtr`.

### <a name="remarks"></a>Poznámky

Ukazatel haldy lze vytvořit volitelně pomocí existující `CComHeapPtr` objektu. Pokud ano, nové `CComHeapPtr` objekt zodpovědnost za správu nový ukazatel a prostředky.

## <a name="see-also"></a>Viz také

[CHeapPtr – třída](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase – třída](../../atl/reference/cheapptrbase-class.md)<br/>
[CComAllocator – třída](../../atl/reference/ccomallocator-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
