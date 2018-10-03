---
title: SafeIntException – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
dev_langs:
- C++
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4ffd82f80b8af0b53ca86ca3daded84580e1e07b
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235734"
---
# <a name="safeintexception-class"></a>SafeIntException – třída

`SafeInt` Třídy používá `SafeIntException` identifikovat důvod, proč matematické operaci nejde dokončit.

## <a name="syntax"></a>Syntaxe

```cpp
class SafeIntException;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                    | Popis
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Vytvoří `SafeIntException` objektu.

## <a name="remarks"></a>Poznámky

[SafeInt – třída](../windows/safeint-class.md) je jediná třída, která používá `SafeIntException` třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SafeIntException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Namespace:** msl::utilities

## <a name="safeintexception"></a>SafeIntException::SafeIntException

Vytvoří `SafeIntException` objektu.

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parametry

*kód*<br/>
[in] Hodnota výčtu dat, popisující chybu, ke které došlo.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *kód* jsou definovány v souboru Safeint.h. Pro usnadnění práce možné hodnoty jsou také uvedeny zde.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
