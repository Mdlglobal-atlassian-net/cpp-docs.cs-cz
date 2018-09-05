---
title: Ccomheapptr – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
dev_langs:
- C++
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7a5b30ca507387b1529c9e9726e48735c844fac
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764826"
---
# <a name="ccomheapptr-class"></a>Ccomheapptr – třída

Třída inteligentní ukazatel pro správu haldy ukazatele.

## <a name="syntax"></a>Syntaxe

```
template<typename T>  
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Parametry

*T*  
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

*pData*  
Existující objekt `CComHeapPtr`.

### <a name="remarks"></a>Poznámky

Ukazatel haldy lze vytvořit volitelně pomocí existující `CComHeapPtr` objektu. Pokud ano, nové `CComHeapPtr` objekt zodpovědnost za správu nový ukazatel a prostředky.

## <a name="see-also"></a>Viz také

[Cheapptr – třída](../../atl/reference/cheapptr-class.md)   
[Cheapptrbase – třída](../../atl/reference/cheapptrbase-class.md)   
[Ccomallocator – třída](../../atl/reference/ccomallocator-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
