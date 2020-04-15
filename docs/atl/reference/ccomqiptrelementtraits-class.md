---
title: Třída CComQIPtrElementTraits
ms.date: 11/04/2016
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
ms.openlocfilehash: 19f2669c157310be02f746672b22f6c0ed005075
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327414"
---
# <a name="ccomqiptrelementtraits-class"></a>Třída CComQIPtrElementTraits

Tato třída poskytuje metody, statické funkce a typedefs užitečné při vytváření kolekcí ukazatelů rozhraní COM.

## <a name="syntax"></a>Syntaxe

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits :
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>Parametry

*I*<br/>
Rozhraní COM určující typ ukazatele, který má být uložen.

*piid*<br/>
Ukazatel na IID *I*.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída odvodí metody a poskytuje typedef užitečné při vytváření třídy kolekce [CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM ukazatele ukazatele objektů. Tato třída je využívána třídami [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) a [CInterfaceList.](../../atl/reference/cinterfacelist-class.md)

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="ccomqiptrelementtraitsinargtype"></a><a name="inargtype"></a>CComQIPtrElementTraits::INARGTYPE

Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>Viz také

[Třída CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
