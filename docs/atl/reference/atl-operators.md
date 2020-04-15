---
title: Operátory ATL
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 8c15daa1d2b12c58323ef5ef75559a2ab911ad93
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319225"
---
# <a name="atl-operators"></a>Operátory ATL

Tato část obsahuje referenční témata pro globální operátory ATL.

|Operátor|Popis|
|--------------|-----------------|
|[operátor ==](#operator_eq_eq)|Porovná dva `CSid` objekty nebo `SID` struktury pro rovnost.|
|[operátor !=](#operator_neq)|Porovná dva `CSid` objekty nebo `SID` struktury pro nerovnost.|
|[<operátora](#operator_lt)|Testuje, `CSid` zda `SID` je objekt nebo struktura na levé `CSid` straně `SID` operátoru menší než objekt nebo struktura na pravé straně (pro kompatibilitu standardní knihovny jazyka C++).|
|[>operátora](#operator_gt)|Testuje, `CSid` zda `SID` je objekt nebo struktura na levé `CSid` straně `SID` operátoru větší než objekt nebo struktura na pravé straně (pro kompatibilitu standardní knihovny jazyka C++).|
|[operátor <=](#operator_lt__eq)|Testuje, `CSid` zda `SID` je objekt nebo struktura na levé straně operátoru menší nebo rovna objektu `CSid` nebo `SID` struktuře na pravé straně (pro kompatibilitu standardní knihovny jazyka C++).|
|[operátor >=](#operator_gt__eq)|Testuje, `CSid` zda `SID` je objekt nebo struktura na levé straně operátoru větší nebo rovna objektu `CSid` nebo `SID` struktuře na pravé straně (pro kompatibilitu standardní knihovny jazyka C++).|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>operátor ==

Porovnává `CSid` objekty `SID` nebo (identifikátor zabezpečení) struktury pro rovnost.

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
První `CSid` objekt `SID` nebo struktura porovnat.

*rhs*<br/>
Druhý `CSid` objekt `SID` nebo strukturu porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud jsou objekty stejné, NEPRAVDA, pokud nejsou stejné.

## <a name="operator-"></a><a name="operator_neq"></a>operátor !=

Porovnává `CSid` objekty `SID` nebo (identifikátor zabezpečení) struktury pro nerovnost.

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
První `CSid` objekt `SID` nebo struktura porovnat.

*rhs*<br/>
Druhý `CSid` objekt `SID` nebo strukturu porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud objekty nejsou stejné, NEPRAVDA, pokud jsou stejné.

## <a name="operator-"></a><a name="operator_lt"></a>operátor <

Testuje, `CSid` zda `SID` je objekt nebo struktura na levé `CSid` straně `SID` operátoru menší než objekt nebo struktura na pravé straně (pro kompatibilitu standardní knihovny jazyka C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
První `CSid` objekt `SID` nebo struktura porovnat.

*rhs*<br/>
Druhý `CSid` objekt `SID` nebo strukturu porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je adresa objektu *lhs* menší než adresa objektu *rhs,* FALSE jinak.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na `CSid` adresu `SID` objektu nebo struktury a je implementován k zajištění kompatibility s třídami kolekce standardní knihovny jazyka C++.

## <a name="operator-"></a><a name="operator_gt"></a>operátor >

Testuje, `CSid` zda `SID` je objekt nebo struktura na levé `CSid` straně `SID` operátoru větší než objekt nebo struktura na pravé straně (pro kompatibilitu standardní knihovny jazyka C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
První `CSid` objekt `SID` nebo struktura porovnat.

*rhs*<br/>
Druhý `CSid` objekt `SID` nebo strukturu porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je adresa *lhs* větší než adresa *rhs*, FALSE jinak.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na `CSid` adresu `SID` objektu nebo struktury a je implementován k zajištění kompatibility s třídami kolekce standardní knihovny jazyka C++.

## <a name="operator-"></a><a name="operator_lt__eq"></a>operátor <=

Testuje, `CSid` zda `SID` je objekt nebo struktura na levé straně operátoru menší nebo rovna objektu `CSid` nebo `SID` struktuře na pravé straně (pro kompatibilitu standardní knihovny jazyka C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
První `CSid` objekt `SID` nebo struktura porovnat.

*rhs*<br/>
Druhý `CSid` objekt `SID` nebo strukturu porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je adresa *lhs* menší nebo rovna adrese *rhs*, FALSE jinak.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na `CSid` adresu `SID` objektu nebo struktury a je implementován k zajištění kompatibility s třídami kolekce standardní knihovny jazyka C++.

## <a name="operator-"></a><a name="operator_gt__eq"></a>operátor >=

Testuje, `CSid` zda `SID` je objekt nebo struktura na levé straně operátoru větší nebo rovna objektu `CSid` nebo `SID` struktuře na pravé straně (pro kompatibilitu standardní knihovny jazyka C++).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
První `CSid` objekt `SID` nebo struktura porovnat.

*rhs*<br/>
Druhý `CSid` objekt `SID` nebo strukturu porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je adresa *lhs* větší nebo rovna adrese *rhs*, FALSE jinak.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na `CSid` adresu `SID` objektu nebo struktury a je implementován k zajištění kompatibility s třídami kolekce standardní knihovny jazyka C++.
