---
title: Třída CComSafeArrayBound
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
ms.openlocfilehash: 2c2f8b787e5366ec893538a88049f6f53dc35caf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327384"
---
# <a name="ccomsafearraybound-class"></a>Třída CComSafeArrayBound

Tato třída je obálka pro [safearraybound](/windows/win32/api/oaidl/ns-oaidl-safearraybound) struktury.

## <a name="syntax"></a>Syntaxe

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|Konstruktor|
|[GetCount](#getcount)|Volání této metody vrátit počet prvků.|
|[GetLowerBound](#getlowerbound)|Volání této metody vrátit dolní mez.|
|[GetUpperBound](#getupperbound)|Volání této metody vrátit horní mez.|
|[SetCount](#setcount)|Volání této metody nastavit počet prvků.|
|[Nastavit dolní hranice](#setlowerbound)|Volání této metody pro nastavení dolní mez.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Nastaví `CComSafeArrayBound` na novou hodnotu.|

## <a name="remarks"></a>Poznámky

Tato třída je obálka `SAFEARRAYBOUND` pro strukturu používanou [CComSafeArray](../../atl/reference/ccomsafearray-class.md). Poskytuje metody pro dotazování a nastavení horní a dolní hranice `CComSafeArray` jedné dimenze objektu a počet prvků, které obsahuje. Vícerozměrný `CComSafeArray` objekt používá `CComSafeArrayBound` pole objektů, jeden pro každou dimenzi. Proto při použití metod, jako je [Například GetCount](#getcount), uvědomte si, že tato metoda nevrátí celkový počet prvků v multidimenzionální pole.

**Záhlaví:** atlsafe.h

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsafe.h

## <a name="ccomsafearrayboundccomsafearraybound"></a><a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound

Konstruktor

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parametry

*ulCount*<br/>
Počet prvků v poli.

*lDolní hranice*<br/>
Dolní mez, ze kterého je pole číslováno.

### <a name="remarks"></a>Poznámky

Pokud má být pole přístupné z programu jazyka C++, doporučuje se, aby dolní mez byla definována jako 0. Může být vhodnější použít jinou dolní mez hodnotu, pokud pole má být použit s jinými jazyky, jako je například Visual Basic.

## <a name="ccomsafearrayboundgetcount"></a><a name="getcount"></a>CComSafeArrayBound::GetCount

Volání této metody vrátit počet prvků.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků.

### <a name="remarks"></a>Poznámky

Pokud přidružený `CComSafeArray` objekt představuje vícerozměrné pole, tato metoda vrátí pouze celkový počet prvků v nejvýraznější dimenzi. Pomocí [CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount) získat celkový počet prvků.

## <a name="ccomsafearrayboundgetlowerbound"></a><a name="getlowerbound"></a>CComSafeArrayBound::GetlowerBound

Volání této metody vrátit dolní mez.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí dolní mez `CComSafeArrayBound` objektu.

## <a name="ccomsafearrayboundgetupperbound"></a><a name="getupperbound"></a>CComSafeArrayBound::GetupperBound

Volání této metody vrátit horní mez.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí horní mez `CComSafeArrayBound` objektu.

### <a name="remarks"></a>Poznámky

Horní mez závisí na počtu prvků a dolní mez hodnoty. Pokud je například dolní mez 0 a počet prvků je 10, horní mez bude automaticky nastavena na 9.

## <a name="ccomsafearrayboundoperator-"></a><a name="operator_eq"></a>CComSafeArrayBound::operátor =

Nastaví `CComSafeArrayBound` na novou hodnotu.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*Vázán*<br/>
Objekt. `CComSafeArrayBound`

*ulCount*<br/>
Počet prvků.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `CComSafeArrayBound` objekt.

### <a name="remarks"></a>Poznámky

Objekt `CComSafeArrayBound` lze přiřadit pomocí `CComSafeArrayBound`existujícího nebo zadáním počtu prvků, v takovém případě je dolní mez nastavena na 0 ve výchozím nastavení.

## <a name="ccomsafearrayboundsetcount"></a><a name="setcount"></a>CComSafeArrayBound::SetCount

Volání této metody nastavit počet prvků.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*ulCount*<br/>
Počet prvků.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v `CComSafeArrayBound` objektu.

## <a name="ccomsafearrayboundsetlowerbound"></a><a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound

Volání této metody pro nastavení dolní mez.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parametry

*lDolní hranice*<br/>
Dolní mez.

### <a name="return-value"></a>Návratová hodnota

Vrátí novou dolní mez objektu. `CComSafeArrayBound`

### <a name="remarks"></a>Poznámky

Pokud má být pole přístupné z programu Visual C++, doporučuje se, aby dolní mez byla definována jako 0. Může být vhodnější použít jinou dolní mez hodnotu, pokud pole má být použit s jinými jazyky, jako je například Visual Basic.

Horní mez závisí na počtu prvků a dolní mez hodnoty. Pokud je například dolní mez 0 a počet prvků je 10, horní mez bude automaticky nastavena na 9.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
