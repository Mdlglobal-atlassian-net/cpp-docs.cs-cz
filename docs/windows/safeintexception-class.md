---
title: SafeIntException – třída
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
ms.openlocfilehash: 80a1573c2f43b1f4b31731083974f87ba389fac2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566657"
---
# <a name="safeintexception-class"></a>SafeIntException – třída

`SafeInt` Třídy používá `SafeIntException` identifikovat důvod, proč matematické operaci nejde dokončit.

> [!NOTE]
> Nejnovější verzi této knihovny se nachází v [ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt).

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
