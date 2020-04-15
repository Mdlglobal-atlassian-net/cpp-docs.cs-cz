---
title: Třída CStringElementTraits
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
ms.openlocfilehash: 078cfd5ff93bfcd8acc747904ea05e6a2e762bc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330621"
---
# <a name="cstringelementtraits-class"></a>Třída CStringElementTraits

Tato třída poskytuje statické funkce používané `CString` třídy kolekce ukládání objektů.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat, která mají být uložena v kolekci.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CStringElementTraits::INARGTYPE](#inargtype)|Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.|
|[CStringElementTraits::OUTARGTYPE](#outargtype)|Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CStringElementTraits::Porovnatprvky](#compareelements)|(Statické) Volání této funkce porovnat dva řetězce prvky rovnosti.|
|[CStringElementTraits::PorovnatprvkyOrdered](#compareelementsordered)|(Statické) Volání této funkce porovnat dva řetězce prvky.|
|[CStringElementTraits::CopyElements](#copyelements)|(Statické) Volání této funkce `CString` ke kopírování prvků uložených v objektu třídy kolekce.|
|[CStringElementTraits::Hash](#hash)|(Statické) Volání této funkce k výpočtu hodnoty hash pro daný řetězec elementu.|
|[CStringElementTraits::Přemístitprvky](#relocateelements)|(Statické) Volání této funkce `CString` přemístit prvky uložené v objektu třídy kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje statické funkce pro kopírování, přesouvání a porovnávání řetězců a pro vytvoření hodnoty hash. Tyto funkce jsou užitečné při použití třídy kolekce k ukládání dat založených na řetězci. [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) použijte v případě, že jsou požadována porovnání bez rozlišování velkých a malých písmen. [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) při řetězci objekty mají být zpracovány jako odkazy.

Další informace naleznete v tématu [třídy kolekce klíčů ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** cstringt.h

## <a name="cstringelementtraitscompareelements"></a><a name="compareelements"></a>CStringElementTraits::Porovnatprvky

Volání této statické funkce porovnat dva řetězce prvky rovnosti.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První prvek řetězce.

*str2*<br/>
Druhý řetězec element.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou prvky stejné, false otherwise.

## <a name="cstringelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraits::PorovnatprvkyOrdered

Volání této statické funkce porovnat dva řetězce prvky.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parametry

*str1*<br/>
První prvek řetězce.

*str2*<br/>
Druhý řetězec element.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud řetězce jsou identické, < 0, pokud *str1* je menší než *str2*, nebo > 0, pokud *str1* je větší než *str2*. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) Metoda se používá k provedení porovnání.

## <a name="cstringelementtraitscopyelements"></a><a name="copyelements"></a>CStringElementTraits::CopyElements

Volání této statické `CString` funkce ke kopírování prvků uložených v objektu třídy kolekce.

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

## <a name="cstringelementtraitshash"></a><a name="hash"></a>CStringElementTraits::Hash

Volání této statické funkce k výpočtu hodnoty hash pro daný prvek řetězce.

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Prvek řetězce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hash vypočtenou pomocí obsahu řetězce.

## <a name="cstringelementtraitsinargtype"></a><a name="inargtype"></a>CStringElementTraits::INARGTYPE

Datový typ, který se má použít pro přidání prvků do objektu třídy kolekce.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsoutargtype"></a><a name="outargtype"></a>CStringElementTraits::OUTARGTYPE

Datový typ, který se má použít pro načítání prvků z objektu třídy kolekce.

```
typedef T& OUTARGTYPE;
```

## <a name="cstringelementtraitsrelocateelements"></a><a name="relocateelements"></a>CStringElementTraits::Přemístitprvky

Volání této statické funkce `CString` přemístit prvky uložené v objektu třídy kolekce.

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

Tato statická funkce volá [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), což je dostatečné pro většinu datových typů. Pokud objekty, které jsou přesouvány, obsahují ukazatele na své vlastní členy, bude nutné tuto statickou funkci přepsat.

## <a name="see-also"></a>Viz také

[Třída CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Třída CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
