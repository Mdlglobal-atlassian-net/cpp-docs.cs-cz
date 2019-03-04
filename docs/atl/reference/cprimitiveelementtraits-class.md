---
title: CPrimitiveElementTraits Class
ms.date: 11/04/2016
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
ms.openlocfilehash: 53d039b15c9f4a79956bd86fbb93600854f90e5f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263049"
---
# <a name="cprimitiveelementtraits-class"></a>CPrimitiveElementTraits Class

Tato třída poskytuje výchozí metody a funkce pro třídy kolekce tvořené primitivní datové typy.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat uložených v kolekci objektu třídy.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání prvků do objektu třídy kolekce.|
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|Datový typ použitý pro získání prvky z třídy objektu kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje výchozí statické funkce a metody pro přesunutí, kopírování, porovnávání a hashování primitivní datový typ prvků uložených v objektu třídy kolekce.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cdefaultcomparetraits –](../../atl/reference/cdefaultcomparetraits-class.md)

[Cdefaulthashtraits –](../../atl/reference/cdefaulthashtraits-class.md)

[Celementtraitsbase –](../../atl/reference/celementtraitsbase-class.md)

[Cdefaultelementtraits –](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="inargtype"></a>  CPrimitiveElementTraits::INARGTYPE

Datový typ pro použití při přidávání prvků do objektu třídy kolekce.

```
typedef T INARGTYPE;
```

##  <a name="outargtype"></a>  CPrimitiveElementTraits::OUTARGTYPE

Datový typ použitý pro získání prvky z třídy objektu kolekce.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Viz také:

[CDefaultElementTraits – třída](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
