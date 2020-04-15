---
title: Třída CHeapPtrElementTraits
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
ms.openlocfilehash: f09da968b264463eba759372e4e0756397e9978e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326879"
---
# <a name="cheapptrelementtraits-class"></a>Třída CHeapPtrElementTraits

Tato třída poskytuje metody, statické funkce a typedefs užitečné při vytváření kolekcí ukazatelů haldy.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T, class Allocator = ATL::CCRTAllocator>
class CHeapPtrElementTraits :
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu, který má být uložen ve třídě kolekce.

*Přidělování*<br/>
Třída přidělení paměti, která má být používána. Výchozí hodnota je [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.|
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody, statické funkce a typedefs pro pomoc při vytváření objektů třídy kolekce obsahující ukazatele haldy. Třída `CHeapPtrList` je odvozena od `CHeapPtrElementTraits`.

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="cheapptrelementtraitsinargtype"></a><a name="inargtype"></a>CHeapPtrElementTraits::INARGTYPE

Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

## <a name="cheapptrelementtraitsoutargtype"></a><a name="outargtype"></a>CHeapPtrElementTraits::OUTARGTYPE

Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Viz také

[Třída CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Třída CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
