---
title: Třída CComHeapPtr
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: 78cadfff9a278cf080393ab919f3891b201c91aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327766"
---
# <a name="ccomheapptr-class"></a>Třída CComHeapPtr

Inteligentní třída ukazatele pro správu ukazatelů haldy.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu, který má být uložen na haldě.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|Konstruktor|

## <a name="remarks"></a>Poznámky

`CComHeapPtr`odvozuje `CHeapPtr`z , ale používá [CComAllocator](../../atl/reference/ccomallocator-class.md) k přidělení paměti pomocí rutiny COM. Viz [CHeapPtr](../../atl/reference/cheapptr-class.md) a [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) pro metody k dispozici.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomheapptrccomheapptr"></a><a name="ccomheapptr"></a>CComHeapPtr::CComHeapPtr

Konstruktor

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>Parametry

*Pdata*<br/>
Existující objekt `CComHeapPtr`.

### <a name="remarks"></a>Poznámky

Ukazatel haldy lze volitelně vytvořit `CComHeapPtr` pomocí existujícího objektu. Pokud ano, `CComHeapPtr` nový objekt přebírá odpovědnost za správu nového ukazatele a prostředků.

## <a name="see-also"></a>Viz také

[Třída CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Třída CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)<br/>
[Třída CComAllocator](../../atl/reference/ccomallocator-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
