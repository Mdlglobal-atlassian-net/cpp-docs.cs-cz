---
title: Celementtraitsbase – třída
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
ms.openlocfilehash: 207207d26a2c43367a00b382f80761429159a7b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259115"
---
# <a name="celementtraitsbase-class"></a>Celementtraitsbase – třída

Tato třída poskytuje výchozí kopie a přesunutí metody pro třídu kolekce.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat uložených v kolekci.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání prvků do objektu třídy kolekce.|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|Datový typ použitý pro získání prvky z třídy objektu kolekce.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|Volání této metody pro kopírování prvků uložených v objektu třídy kolekce.|
|[CElementTraitsBase::RelocateElements](#relocateelements)|Volejte tuto metodu za účelem přemístit prvků uložených v objektu třídy kolekce.|

## <a name="remarks"></a>Poznámky

Tato základní třída definuje metody pro kopírování a přemístění elementů ve třídě kolekce. Se používá v rámci tříd [cdefaultelementtraits –](../../atl/reference/cdefaultelementtraits-class.md), [cstringrefelementtraits –](../../atl/reference/cstringrefelementtraits-class.md), a [cstringelementtraitsi –](../../atl/reference/cstringelementtraitsi-class.md).

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcoll.h

##  <a name="copyelements"></a>  CElementTraitsBase::CopyElements

Volání této metody pro kopírování prvků uložených v objektu třídy kolekce.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
Ukazatel na první prvek, který bude příjemcem zkopírovaná data.

*pSrc*<br/>
Ukazatel na první prvek ke kopírování.

*nElements*<br/>
Počet prvků ke zkopírování.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové elementy se nesmí překrývat.

##  <a name="inargtype"></a>  CElementTraitsBase::INARGTYPE

Datový typ pro použití při přidávání prvků do kolekce.

```
typedef const T& INARGTYPE;
```

##  <a name="outargtype"></a>  CElementTraitsBase::OUTARGTYPE

Datový typ použitý pro získání elementy z kolekce.

```
typedef T& OUTARGTYPE;
```

##  <a name="relocateelements"></a>  CElementTraitsBase::RelocateElements

Volejte tuto metodu za účelem přemístit prvků uložených v objektu třídy kolekce.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
Ukazatel na první prvek, který bude příjemcem přemisťování dat.

*pSrc*<br/>
Ukazatel na první prvek pro přemístění.

*nElements*<br/>
Počet prvků, které mají přemístění.

### <a name="remarks"></a>Poznámky

Tato metoda volá [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), který stačí pro většinu datových typů. Pokud objekty přesouvaných obsahují ukazatele a jejich členy, bude nutné tuto metodu přepsat.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
