---
title: Třída CAutoPtrElementTraits
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
ms.openlocfilehash: ac29116dc9beedf587c42cc0e52f8c9dbaf3d782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318878"
---
# <a name="cautoptrelementtraits-class"></a>Třída CAutoPtrElementTraits

Tato třída poskytuje metody, statické funkce a typedefs užitečné při vytváření kolekcí inteligentní ukazatele.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.|
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody, statické funkce a typedefs pro pomoc při vytváření objektů třídy kolekce obsahujícíinteligentní ukazatele. Třídy [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) a [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) jsou odvozeny z . `CAutoPtrElementTraits` Pokud vytváření kolekce inteligentní ukazatele, které vyžaduje vektor nové a odstranit operátory, použijte [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) místo.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cautoptrelementtraitsinargtype"></a><a name="inargtype"></a>CAutoPtrElementTraits::INARGTYPE

Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.

```
typedef CAutoPtr<T>& INARGTYPE;
```

## <a name="cautoptrelementtraitsoutargtype"></a><a name="outargtype"></a>CAutoPtrElementTraits::OUTARGTYPE

Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Viz také

[Třída CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
