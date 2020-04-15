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
ms.openlocfilehash: e118d7e3cce47ebb93cef16319a8fc45aab1118b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349944"
---
# <a name="safeintexception-class"></a>SafeIntException – třída

Třída `SafeInt` používá `SafeIntException` k identifikaci, proč nelze dokončit matematickou operaci.

> [!NOTE]
> Nejnovější verze této knihovny [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)je umístěna na adrese .

## <a name="syntax"></a>Syntaxe

```cpp
class SafeIntException;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                    | Popis
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Vytvoří `SafeIntException` objekt.

## <a name="remarks"></a>Poznámky

Třída [SafeInt](../safeint/safeint-class.md) je jediná třída, `SafeIntException` která používá třídu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SafeIntException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Obor názvů:** msl::nástroje

## <a name="safeintexceptionsafeintexception"></a><a name="safeintexception"></a>Výjimka SafeIntException::SafeIntException

Vytvoří `SafeIntException` objekt.

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parametry

*Kód*<br/>
[v] Výčet datové hodnoty, která popisuje chybu, ke které došlo.

### <a name="remarks"></a>Poznámky

Možné hodnoty *kódu* jsou definovány v souboru Safeint.h. Pro větší pohodlí jsou zde uvedeny také možné hodnoty.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
