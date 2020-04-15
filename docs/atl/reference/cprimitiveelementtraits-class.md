---
title: Třída CPrimitiveElementTraits
ms.date: 11/04/2016
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
ms.openlocfilehash: 6b45d93420d1832091cc451a3e6eb309f61d07a3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331441"
---
# <a name="cprimitiveelementtraits-class"></a>Třída CPrimitiveElementTraits

Tato třída poskytuje výchozí metody a funkce pro třídu kolekce složenou z primitivních datových typů.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, která mají být uložena v objektu třídy kolekce.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.|
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje výchozí statické funkce a metody pro přesouvání, kopírování, porovnávání a hash primitivní datové prvky uložené v objektu třídy kolekce.

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cprimitiveelementtraitsinargtype"></a><a name="inargtype"></a>CPrimitiveElementTraits::INARGTYPE

Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.

```
typedef T INARGTYPE;
```

## <a name="cprimitiveelementtraitsoutargtype"></a><a name="outargtype"></a>CPrimitiveElementTraits::OUTARGTYPE

Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Viz také

[Třída CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
