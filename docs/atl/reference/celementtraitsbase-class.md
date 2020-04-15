---
title: Třída CElementTraitsBase
ms.date: 11/04/2016
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
ms.openlocfilehash: 5a29e8778cf2f3400df25b55574950a005bad995
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327003"
---
# <a name="celementtraitsbase-class"></a>Třída CElementTraitsBase

Tato třída poskytuje výchozí metody kopírování a přesunutí pro třídu kolekce.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, která mají být uložena v kolekci.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|Volání této metody ke kopírování prvků uložených v objektu třídy kolekce.|
|[CElementTraitsBase::Přemístitprvky](#relocateelements)|Volání této metody přemístit prvky uložené v objektu třídy kolekce.|

## <a name="remarks"></a>Poznámky

Tato základní třída definuje metody kopírování a přemisťování prvků ve třídě kolekce. Je využíván a třídy [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)a [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

## <a name="celementtraitsbasecopyelements"></a><a name="copyelements"></a>CElementTraitsBase::CopyElements

Volání této metody ke kopírování prvků uložených v objektu třídy kolekce.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
Ukazatel na první prvek, který obdrží zkopírovaná data.

*pSrc*<br/>
Ukazatel na první prvek ke kopírování.

*nPrvky*<br/>
Počet prvků, které chcete kopírovat.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové prvky by se neměly překrývat.

## <a name="celementtraitsbaseinargtype"></a><a name="inargtype"></a>CElementTraitsBase::INARGTYPE

Datový typ, který se má použít pro přidání prvků do kolekce.

```
typedef const T& INARGTYPE;
```

## <a name="celementtraitsbaseoutargtype"></a><a name="outargtype"></a>CElementTraitsBase::OUTARGTYPE

Datový typ, který chcete použít pro načítání prvků z kolekce.

```
typedef T& OUTARGTYPE;
```

## <a name="celementtraitsbaserelocateelements"></a><a name="relocateelements"></a>CElementTraitsBase::Přemístitprvky

Volání této metody přemístit prvky uložené v objektu třídy kolekce.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
Ukazatel na první prvek, který obdrží přemístěná data.

*pSrc*<br/>
Ukazatel na první prvek přemístit.

*nPrvky*<br/>
Počet prvků přemístit.

### <a name="remarks"></a>Poznámky

Tato metoda volá [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), což je dostatečné pro většinu datových typů. Pokud objekty, které jsou přesouvány obsahují ukazatele na své vlastní členy, bude nutné tuto metodu přepsat.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
