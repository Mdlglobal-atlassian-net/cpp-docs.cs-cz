---
title: Třída CAutoVectorPtrElementTraits
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
ms.openlocfilehash: 956fe39c4d3ba89bb9def2f996dca59905753edb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318744"
---
# <a name="cautovectorptrelementtraits-class"></a>Třída CAutoVectorPtrElementTraits

Tato třída poskytuje metody, statické funkce a typedefs užitečné při vytváření kolekcí inteligentní ukazatele pomocí vektoru nové a odstranit operátory.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CAutoVectorPtrElementTraits :
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.|
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody, statické funkce a typedefs pro pomoc při vytváření objektů třídy kolekce obsahujícíinteligentní ukazatele. Na rozdíl od [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md), tato třída používá vektor nové a delete operátory.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cautovectorptrelementtraitsinargtype"></a><a name="inargtype"></a>CAutoVectorPtrElementTraits::INARGTYPE

Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

## <a name="cautovectorptrelementtraitsoutargtype"></a><a name="outargtype"></a>CAutoVectorPtrElementTraits::OUTARGTYPE

Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>Viz také

[Třída CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Třída CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
