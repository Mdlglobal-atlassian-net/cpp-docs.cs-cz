---
title: CAutoPtrArray – třída
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: 11f39eac8b8d080fd840f6454f393e33ebcb9e1c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167658"
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray – třída

Tato třída poskytuje metody užitečné při vytváření pole inteligentních ukazatelů.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

### <a name="parameters"></a>Parametry

*Cerebrální*<br/>
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|Konstruktor|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje konstruktor a odvozuje metody z [CAtlArray](../../atl/reference/catlarray-class.md) a [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) pro pomoc při vytváření objektu třídy kolekce, který ukládá inteligentní ukazatele.

Další informace naleznete v tématu [třídy kolekcí ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll. h

## <a name="cautoptrarraycautoptrarray"></a><a name="cautoptrarray"></a>CAutoPtrArray::CAutoPtrArray

Konstruktor

```cpp
CAutoPtrArray() throw();
```

### <a name="remarks"></a>Poznámky

Inicializuje pole inteligentního ukazatele.

## <a name="see-also"></a>Viz také

[CAtlArray – třída](../../atl/reference/catlarray-class.md)<br/>
[CAutoPtrElementTraits – třída](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[CAutoPtrList – třída](../../atl/reference/cautoptrlist-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
