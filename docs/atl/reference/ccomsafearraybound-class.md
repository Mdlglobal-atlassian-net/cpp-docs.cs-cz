---
title: CComSafeArrayBound – třída
ms.date: 05/06/2019
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
ms.openlocfilehash: bd77c2a788e769c74518d73b45c3c05ff27b3f58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496897"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound – třída

Tato třída je obálkou pro strukturu [SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-tagsafearraybound) .

## <a name="syntax"></a>Syntaxe

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|Konstruktor|
|[GetCount](#getcount)|Voláním této metody vrátíte počet prvků.|
|[GetLowerBound](#getlowerbound)|Voláním této metody vrátíte dolní mez.|
|[GetUpperBound](#getupperbound)|Voláním této metody vrátíte horní mez.|
|[SetCount](#setcount)|Voláním této metody nastavíte počet prvků.|
|[SetLowerBound](#setlowerbound)|Voláním této metody nastavíte dolní mez.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|`CComSafeArrayBound` Nastaví na novou hodnotu.|

## <a name="remarks"></a>Poznámky

Tato třída je obálkou pro strukturu `SAFEARRAYBOUND` , kterou používá [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Poskytuje metody pro dotazování a nastavení horních a dolních mezí jedné dimenze `CComSafeArray` objektu a počtu elementů, které obsahuje. Multidimenzionální `CComSafeArray` objekt používá `CComSafeArrayBound` pole objektů, jeden pro každou dimenzi. Proto při použití metod, jako je [GetCount](#getcount), počítejte s tím, že tato metoda nevrátí celkový počet prvků v multidimenzionálním poli.

**Záhlaví:** atlsafe. h

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsafe. h

##  <a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound

Konstruktor

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parametry

*ulCount*<br/>
Počet prvků v poli.

*lLowerBound*<br/>
Dolní mez, ze které je pole očíslováno.

### <a name="remarks"></a>Poznámky

Pokud má být k poli přistup z C++ programu, je doporučeno, aby dolní hranice bylo definováno jako 0. Může být vhodnější použít jinou hodnotu dolní meze, pokud je pole použito v jiných jazycích, například Visual Basic.

##  <a name="getcount"></a>CComSafeArrayBound:: GetCount

Voláním této metody vrátíte počet prvků.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků.

### <a name="remarks"></a>Poznámky

Pokud přidružený `CComSafeArray` objekt představuje multidimenzionální pole, bude tato metoda vracet pouze celkový počet prvků v dimenzi nejvíce vpravo. Chcete-li získat celkový počet prvků, použijte [CComSafeArray:: GetCount](../../atl/reference/ccomsafearray-class.md#getcount) .

##  <a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound

Voláním této metody vrátíte dolní mez.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí dolní mez `CComSafeArrayBound` objektu.

##  <a name="getupperbound"></a>CComSafeArrayBound::GetUpperBound

Voláním této metody vrátíte horní mez.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí horní mez `CComSafeArrayBound` objektu.

### <a name="remarks"></a>Poznámky

Horní mez závisí na počtu prvků a dolní vázané hodnotě. Pokud je dolní mez například 0 a počet prvků je 10, horní hranice bude automaticky nastavena na 9.

##  <a name="operator_eq"></a>CComSafeArrayBound:: operator =

`CComSafeArrayBound` Nastaví na novou hodnotu.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*vázaný*<br/>
A `CComSafeArrayBound` objektu.

*ulCount*<br/>
Počet elementů.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `CComSafeArrayBound` objekt.

### <a name="remarks"></a>Poznámky

Objekt lze přiřadit pomocí existující `CComSafeArrayBound`nebo zadáním počtu prvků, v takovém případě je dolní hranice ve výchozím nastavení nastavena na hodnotu 0. `CComSafeArrayBound`

##  <a name="setcount"></a>CComSafeArrayBound::SetCount

Voláním této metody nastavíte počet prvků.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*ulCount*<br/>
Počet elementů.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v `CComSafeArrayBound` objektu.

##  <a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound

Voláním této metody nastavíte dolní mez.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parametry

*lLowerBound*<br/>
Dolní mez.

### <a name="return-value"></a>Návratová hodnota

Vrátí novou dolní mez `CComSafeArrayBound` objektu.

### <a name="remarks"></a>Poznámky

Pokud má být k poli přistup z vizuálního C++ programu, je doporučeno, aby dolní hranice byla definována jako 0. Může být vhodnější použít jinou hodnotu dolní meze, pokud je pole použito v jiných jazycích, například Visual Basic.

Horní mez závisí na počtu prvků a dolní vázané hodnotě. Pokud je dolní mez například 0 a počet prvků je 10, horní hranice bude automaticky nastavena na 9.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
