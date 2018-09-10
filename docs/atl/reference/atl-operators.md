---
title: ATL – operátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f5027fa4b84d84bf07766c7ac4e75f140706f0c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103700"
---
# <a name="atl-operators"></a>ATL – operátory

Tato část obsahuje referenční témata pro globální operátory ATL.

|Operátor|Popis|
|--------------|-----------------|
|[Operator ==](#operator_eq_eq)|Porovná dva `CSid` objekty nebo `SID` struktur pro rovnost.|
|[Operator! =](#operator_neq)|Porovná dva `CSid` objekty nebo `SID` struktury nerovnost.|
|[Operator <](#operator_lt)|Testuje, zda `CSid` objektu nebo `SID` je struktura na levé straně operátoru menší než `CSid` objektu nebo `SID` struktury na pravé straně (z důvodu kompatibility standardní knihovna C++).|
|[Operator >](#operator_gt)|Testuje, zda `CSid` objektu nebo `SID` je struktura na levé straně operátoru větší než `CSid` objektu nebo `SID` struktury na pravé straně (z důvodu kompatibility standardní knihovna C++).|
|[Operator < =](#operator_lt__eq)|Testuje, zda `CSid` objektu nebo `SID` struktuře na levé straně operátoru menší než nebo rovno je `CSid` objektu nebo `SID` struktury na pravé straně (z důvodu kompatibility standardní knihovna C++).|
|[Operator > =](#operator_gt__eq)|Testuje, zda `CSid` objektu nebo `SID` je struktura na levé straně operátoru větší než nebo rovna hodnotě `CSid` objektu nebo `SID` struktury na pravé straně (z důvodu kompatibility standardní knihovna C++).|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h.

##  <a name="operator_eq_eq"></a>  Operator ==

Porovná `CSid` objekty nebo `SID` struktury (security identifier) pro rovnost.

```   
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
První `CSid` objektu nebo `SID` struktury k porovnání.

*Zarovnání indirekce RHS*  
Druhá `CSid` objektu nebo `SID` struktury k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud objekty rovnají, FALSE. Pokud nejsou stejné.

##  <a name="operator_neq"></a>  Operator! =

Porovná `CSid` objekty nebo `SID` struktury (security identifier) pro nerovnost.

```   
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
První `CSid` objektu nebo `SID` struktury k porovnání.

*Zarovnání indirekce RHS*  
Druhá `CSid` objektu nebo `SID` struktury k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud jsou tyto objekty stejné, FALSE, pokud jsou shodné.

##  <a name="operator_lt"></a>  Operator <

Testuje, zda `CSid` objektu nebo `SID` je struktura na levé straně operátoru menší než `CSid` objektu nebo `SID` struktury na pravé straně (z důvodu kompatibility standardní knihovna C++).

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
První `CSid` objektu nebo `SID` struktury k porovnání.

*Zarovnání indirekce RHS*  
Druhá `CSid` objektu nebo `SID` struktury k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud adresa *lhs* je objekt menší než adresu *zarovnání indirekce rhs* objektu, FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na adrese `CSid` objektu nebo `SID` struktury a je implementována pro zajištění kompatibility s C++ standardní knihovna tříd kolekcí.

##  <a name="operator_gt"></a>  Operator >

Testuje, zda `CSid` objektu nebo `SID` je struktura na levé straně operátoru větší než `CSid` objektu nebo `SID` struktury na pravé straně (z důvodu kompatibility standardní knihovna C++).

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
První `CSid` objektu nebo `SID` struktury k porovnání.

*Zarovnání indirekce RHS*  
Druhá `CSid` objektu nebo `SID` struktury k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud adresa *lhs* je větší než adresu *zarovnání indirekce rhs*, FALSE, jinak.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na adrese `CSid` objektu nebo `SID` struktury a je implementována pro zajištění kompatibility s C++ standardní knihovna tříd kolekcí.

##  <a name="operator_lt__eq"></a>  Operator < =

Testuje, zda `CSid` objektu nebo `SID` struktuře na levé straně operátoru menší než nebo rovno je `CSid` objektu nebo `SID` struktury na pravé straně (z důvodu kompatibility standardní knihovna C++).

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
První `CSid` objektu nebo `SID` struktury k porovnání.

*Zarovnání indirekce RHS*  
Druhá `CSid` objektu nebo `SID` struktury k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud adresa *lhs* je menší než nebo rovna adresu *zarovnání indirekce rhs*, FALSE, jinak.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na adrese `CSid` objektu nebo `SID` struktury a je implementována pro zajištění kompatibility s C++ standardní knihovna tříd kolekcí.

##  <a name="operator_gt__eq"></a>  Operator > =

Testuje, zda `CSid` objektu nebo `SID` je struktura na levé straně operátoru větší než nebo rovna hodnotě `CSid` objektu nebo `SID` struktury na pravé straně (z důvodu kompatibility standardní knihovna C++).

```   
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
První `CSid` objektu nebo `SID` struktury k porovnání.

*Zarovnání indirekce RHS*  
Druhá `CSid` objektu nebo `SID` struktury k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud adresa *lhs* je větší než nebo rovna hodnotě adresu *zarovnání indirekce rhs*, FALSE, jinak.

### <a name="remarks"></a>Poznámky

Tento operátor funguje na adrese `CSid` objektu nebo `SID` struktury a je implementována pro zajištění kompatibility s C++ standardní knihovna tříd kolekcí.

