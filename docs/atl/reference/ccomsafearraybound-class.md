---
title: Ccomsafearraybound – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 457c880f7f7eb6c011637b438fa3bcc25d57303b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758271"
---
# <a name="ccomsafearraybound-class"></a>Ccomsafearraybound – třída

Tato třída představuje obálku pro [SAFEARRAYBOUND](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagsafearraybound) struktury.

## <a name="syntax"></a>Syntaxe

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Ccomsafearraybound –](#ccomsafearraybound)|Konstruktor|
|[GetCount](#getcount)|Voláním této metody vrátí počet prvků.|
|[GetLowerBound](#getlowerbound)|Voláním této metody vrátí dolní mez.|
|[GetUpperBound](#getupperbound)|Voláním této metody vrátí horní mez.|
|[SetCount](#setcount)|Voláním této metody lze nastavit počet prvků.|
|[SetLowerBound](#setlowerbound)|Voláním této metody lze nastavit dolní mez.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Nastaví `CComSafeArrayBound` na novou hodnotu.|

## <a name="remarks"></a>Poznámky

Tato třída představuje obálku pro `SAFEARRAYBOUND` struktura používá [tříd CComSafeArray](../../atl/reference/ccomsafearray-class.md). Poskytuje metody pro dotazování a nastavování horní a dolní meze jednu dimenzi `CComSafeArray` objektu a počet prvků, které obsahuje. Multidimenzionální `CComSafeArray` objekt používá pole `CComSafeArrayBound` objekty, jeden pro každou dimenzi. Proto při použití metody jako například [GetCount](#getcount), mějte na paměti, že tato metoda nevrátí celkový počet prvků v multidimenzionálního pole.

**Záhlaví:** atlsafe.h

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsafe.h

##  <a name="ccomsafearraybound"></a>  CComSafeArrayBound::CComSafeArrayBound

Konstruktor

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>Parametry

*ulCount*  
Počet prvků v poli.

*lLowerBound*  
Dolní mez, ze kterého je číslovaný matice.

### <a name="remarks"></a>Poznámky

Pokud pole je přístupný z programu v jazyce Visual C++, doporučuje se, že je dolní mez být definováno jako 0. Může být vhodnější použít jiné dolní mez hodnotu, pokud je pole, který se má použít s jinými jazyky, jako je například Visual Basic.

##  <a name="getcount"></a>  CComSafeArrayBound::GetCount

Voláním této metody vrátí počet prvků.

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků.

### <a name="remarks"></a>Poznámky

Pokud přidružené `CComSafeArray` objekt představuje multidimenzionálního pole, tato metoda vrátí pouze celkový počet prvků v rozměr nejvíce vpravo. Použití [CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount) získat celkový počet prvků.

##  <a name="getlowerbound"></a>  CComSafeArrayBound::GetLowerBound

Voláním této metody vrátí dolní mez.

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí dolní mez `CComSafeArrayBound` objektu.

##  <a name="getupperbound"></a>  CComSafeArrayBound::GetUpperBound

Voláním této metody vrátí horní mez.

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí horní mez `CComSafeArrayBound` objektu.

### <a name="remarks"></a>Poznámky

Horní mez závisí na počtu prvků a hodnot dolní mez. Například pokud je dolní mez 0 a 10 je počet elementů, horní mez bude automaticky nastavit do 9.

##  <a name="operator_eq"></a>  CComSafeArrayBound::operator =

Nastaví `CComSafeArrayBound` na novou hodnotu.

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*vázaný*  
A `CComSafeArrayBound` objektu.

*ulCount*  
Počet prvků.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel `CComSafeArrayBound` objektu.

### <a name="remarks"></a>Poznámky

`CComSafeArrayBound` Objekt lze přiřadit pomocí existující `CComSafeArrayBound`, nebo zadáním počet prvků, ve kterých případ dolní mez ve výchozím nastavení nastavena na hodnotu 0.

##  <a name="setcount"></a>  CComSafeArrayBound::SetCount

Voláním této metody lze nastavit počet prvků.

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>Parametry

*ulCount*  
Počet prvků.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet prvků v `CComSafeArrayBound` objektu.

##  <a name="setlowerbound"></a>  CComSafeArrayBound::SetLowerBound

Voláním této metody lze nastavit dolní mez.

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>Parametry

*lLowerBound*  
Dolní mez.

### <a name="return-value"></a>Návratová hodnota

Vrátí nový dolní mez `CComSafeArrayBound` objektu.

### <a name="remarks"></a>Poznámky

Pokud pole je přístupný z programu v jazyce Visual C++, doporučuje se, že je dolní mez být definováno jako 0. Může být vhodnější použít jiné dolní mez hodnotu, pokud je pole, který se má použít s jinými jazyky, jako je například Visual Basic.

Horní mez závisí na počtu prvků a hodnot dolní mez. Například pokud je dolní mez 0 a 10 je počet elementů, horní mez bude automaticky nastavit do 9.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
