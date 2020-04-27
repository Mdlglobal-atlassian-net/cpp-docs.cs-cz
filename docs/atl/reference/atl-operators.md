---
title: Operátory ATL
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: fe5363d3d05123c17e45254898e2210797400022
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168849"
---
# <a name="atl-operators"></a>Operátory ATL

Tato část obsahuje referenční témata pro globální operátory ATL.

|Operátor|Popis|
|--------------|-----------------|
|[operator = = – operátor](#operator_eq_eq)|Porovná `CSid` dva objekty `SID` nebo struktury pro rovnost.|
|[! = – operátor](#operator_neq)|Porovná `CSid` dva objekty `SID` nebo struktury pro nerovnost.|
|[operátor <](#operator_lt)|Testuje, `CSid` zda je objekt `SID` nebo struktura na levé straně operátoru menší než `CSid` objekt nebo `SID` struktura na pravé straně (v případě kompatibility standardní knihovny C++).|
|[operátor >](#operator_gt)|Testuje, `CSid` zda je objekt `SID` nebo struktura na levé straně operátoru větší než `CSid` objekt nebo `SID` struktura na pravé straně (pro kompatibilitu standardní knihovny C++).|
|[operátor <=](#operator_lt__eq)|Testuje, zda `CSid` je objekt `SID` nebo struktura na levé straně operátoru menší než nebo rovna `CSid` objektu nebo `SID` struktuře na pravé straně (pro kompatibilitu standardní knihovny C++).|
|[operátor >=](#operator_gt__eq)|Testuje, zda `CSid` je objekt `SID` nebo struktura na levé straně operátoru větší než nebo rovna `CSid` objektu nebo `SID` struktuře na pravé straně (pro kompatibilitu standardní knihovny C++).|

## <a name="requirements"></a>Požadavky

**Hlavička:** atlsecurity. h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>operator = = – operátor

Porovná `CSid` struktury `SID` objektů nebo (identifikátorů zabezpečení) pro rovnost.

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První `CSid` objekt nebo `SID` struktura, které mají být porovnány.

*zarovnání indirekce RHS*<br/>
Druhý `CSid` objekt nebo `SID` struktura pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud jsou objekty stejné, FALSE, pokud nejsou stejné.

## <a name="operator-"></a><a name="operator_neq"></a>! = – operátor

Porovná `CSid` struktury `SID` objektů nebo (identifikátorů zabezpečení) pro nerovnost.

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První `CSid` objekt nebo `SID` struktura, které mají být porovnány.

*zarovnání indirekce RHS*<br/>
Druhý `CSid` objekt nebo `SID` struktura pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud jsou objekty stejné, FALSE, pokud jsou stejné.

## <a name="operator-"></a><a name="operator_lt"></a>operátor <

Testuje, `CSid` zda je objekt `SID` nebo struktura na levé straně operátoru menší než `CSid` objekt nebo `SID` struktura na pravé straně (v případě kompatibility standardní knihovny C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První `CSid` objekt nebo `SID` struktura, které mají být porovnány.

*zarovnání indirekce RHS*<br/>
Druhý `CSid` objekt nebo `SID` struktura pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je adresa objektu *LHS* menší než adresa objektu *Zarovnání INDIREKCE RHS* , jinak false.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na adrese `CSid` objektu nebo `SID` struktury a je implementován pro zajištění kompatibility s třídami kolekce knihovny Standard C++.

## <a name="operator-"></a><a name="operator_gt"></a>operátor >

Testuje, `CSid` zda je objekt `SID` nebo struktura na levé straně operátoru větší než `CSid` objekt nebo `SID` struktura na pravé straně (pro kompatibilitu standardní knihovny C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První `CSid` objekt nebo `SID` struktura, které mají být porovnány.

*zarovnání indirekce RHS*<br/>
Druhý `CSid` objekt nebo `SID` struktura pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je adresa *LHS* větší než adresa *Zarovnání indirekce RHS*, jinak false.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na adrese `CSid` objektu nebo `SID` struktury a je implementován pro zajištění kompatibility s třídami kolekce knihovny Standard C++.

## <a name="operator-"></a><a name="operator_lt__eq"></a>operátor <=

Testuje, zda `CSid` je objekt `SID` nebo struktura na levé straně operátoru menší než nebo rovna `CSid` objektu nebo `SID` struktuře na pravé straně (pro kompatibilitu standardní knihovny C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První `CSid` objekt nebo `SID` struktura, které mají být porovnány.

*zarovnání indirekce RHS*<br/>
Druhý `CSid` objekt nebo `SID` struktura pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je adresa *LHS* menší nebo rovna adrese *Zarovnání indirekce RHS*, jinak false.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na adrese `CSid` objektu nebo `SID` struktury a je implementován pro zajištění kompatibility s třídami kolekce knihovny Standard C++.

## <a name="operator-"></a><a name="operator_gt__eq"></a>operátor >=

Testuje, zda `CSid` je objekt `SID` nebo struktura na levé straně operátoru větší než nebo rovna `CSid` objektu nebo `SID` struktuře na pravé straně (pro kompatibilitu standardní knihovny C++).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První `CSid` objekt nebo `SID` struktura, které mají být porovnány.

*zarovnání indirekce RHS*<br/>
Druhý `CSid` objekt nebo `SID` struktura pro porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je adresa *LHS* větší než nebo rovna adrese *Zarovnání indirekce RHS*, jinak false.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na adrese `CSid` objektu nebo `SID` struktury a je implementován pro zajištění kompatibility s třídami kolekce knihovny Standard C++.
