---
title: Cstringelementtraits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43581995e8979ec733d8c82374896009c843166b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766643"
---
# <a name="cstringelementtraits-class"></a>Cstringelementtraits – třída

Tato třída poskytuje statické funkce, které používají třídy kolekcí ukládání `CString` objekty.

## <a name="syntax"></a>Syntaxe

```
template <typename T>  
class CStringElementTraits
```

#### <a name="parameters"></a>Parametry

*T*  
Typ dat uložených v kolekci.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CStringElementTraits::INARGTYPE](#inargtype)|Datový typ pro použití při přidávání prvků do objektu třídy kolekce.|
|[CStringElementTraits::OUTARGTYPE](#outargtype)|Datový typ použitý pro získání prvky z třídy objektu kolekce.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStringElementTraits::CompareElements](#compareelements)|(Statické) Voláním této funkce porovnání dvou prvků řetězce pro rovnosti.|
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|(Statické) Voláním této funkce porovnání dvou prvků řetězce.|
|[CStringElementTraits::CopyElements](#copyelements)|(Statické) Voláním této funkce zkopírujte `CString` prvků uložených v objektu třídy kolekce.|
|[CStringElementTraits::Hash](#hash)|(Statické) Voláním této funkce pro výpočet hodnoty hash pro prvek zadaného řetězce.|
|[CStringElementTraits::RelocateElements](#relocateelements)|(Statické) Voláním této funkce můžou přemístit `CString` prvků uložených v objektu třídy kolekce.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje statické funkce pro kopírování, přesunutí a porovnávání řetězců a pro vytvoření hodnoty hash. Tyto funkce jsou užitečné při použití třídy kolekce k ukládání dat založené na řetězci. Použití [cstringelementtraitsi –](../../atl/reference/cstringelementtraitsi-class.md) při porovnávání se vyžadují. Použití [cstringrefelementtraits –](../../atl/reference/cstringrefelementtraits-class.md) při řetězcových objektů mají být zpracovány jako odkazy.

Další informace najdete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** cstringt.h

##  <a name="compareelements"></a>  CStringElementTraits::CompareElements

Voláním této funkce statických porovnat dva prvky řetězce pro rovnosti.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parametry

*Str1*  
První řetězec elementu.

*řetězci Str2*  
Druhý řetězec elementu.

### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud prvky jsou stejné, jinak hodnota false.

##  <a name="compareelementsordered"></a>  CStringElementTraits::CompareElementsOrdered

Voláním této funkce statických porovnat dva prvky řetězce.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parametry

*Str1*  
První řetězec elementu.

*řetězci Str2*  
Druhý řetězec elementu.

### <a name="return-value"></a>Návratová hodnota

Nula v případě, že jsou řetězce identické, < 0 Pokud *str1* je menší než *řetězci str2*, nebo > 0 Pokud *str1* je větší než *řetězci str2*. [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) metoda se používá k provádění porovnání.  

##  <a name="copyelements"></a>  CStringElementTraits::CopyElements

Voláním této funkce statických zkopírujte `CString` prvků uložených v objektu třídy kolekce.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest*  
Ukazatel na první prvek, který bude příjemcem zkopírovaná data.

*pSrc*  
Ukazatel na první prvek ke kopírování.

*nElements*  
Počet prvků ke zkopírování.

### <a name="remarks"></a>Poznámky

Zdrojové a cílové elementy se nesmí překrývat.

##  <a name="hash"></a>  CStringElementTraits::Hash

Voláním této funkce statických vypočítat hodnotu hash pro prvek zadaného řetězce.

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>Parametry

*str*  
Element řetězce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu hash pomocí obsahu řetězce.

##  <a name="inargtype"></a>  CStringElementTraits::INARGTYPE

Datový typ pro použití při přidávání prvků do objektu třídy kolekce.

```
typedef T::PCXSTR INARGTYPE;
```

##  <a name="outargtype"></a>  CStringElementTraits::OUTARGTYPE

Datový typ použitý pro získání prvky z třídy objektu kolekce.

```
typedef T& OUTARGTYPE;
```

##  <a name="relocateelements"></a>  CStringElementTraits::RelocateElements

Voláním této funkce statických přemístit `CString` prvků uložených v objektu třídy kolekce.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parametry

*pDest*  
Ukazatel na první prvek, který bude příjemcem přemisťování dat.

*pSrc*  
Ukazatel na první prvek pro přemístění.

*nElements*  
Počet prvků, které mají přemístění.

### <a name="remarks"></a>Poznámky

Tato statická funkce volá [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), který stačí pro většinu datových typů. Pokud objekty přesouvaných obsahují ukazatele a jejich členy, Tato statická funkce bude nutné přepsat.

## <a name="see-also"></a>Viz také

[Celementtraitsbase – třída](../../atl/reference/celementtraitsbase-class.md)   
[Cstringelementtraitsi – třída](../../atl/reference/cstringelementtraitsi-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
