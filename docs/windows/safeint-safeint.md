---
title: SafeInt::SafeInt | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt::SafeInt
- SafeInt
- SafeInt.SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class, constructor
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de318ab79638f63fae98856987340ad62534f695
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721342"
---
# <a name="safeintsafeint"></a>SafeInt::SafeInt

Vytvoří **SafeInt** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
SafeInt() throw

SafeInt (
   const T& i
) throw ()

SafeInt (
   bool b
) throw ()

template <typename U>
SafeInt (
   const SafeInt <U, E>& u
)

I template <typename U>
SafeInt (
   const U& i
)  
```

### <a name="parameters"></a>Parametry

*i*<br/>
[in] Hodnota pro novou **SafeInt** objektu. Musí se jednat o parametr typu T nebo U, v závislosti na konstruktor.

*b*<br/>
[in] Logická hodnota pro novou **SafeInt** objektu.

*u*<br/>
[in] A **SafeInt** z typu U. Nové **SafeInt** objektu bude mít stejnou hodnotu jako *u*, ale budou typu T.

U typu dat uložených v **SafeInt**. To může být typu logická hodnota, znak nebo celé číslo. Pokud je typ integer, může být podepsané nebo nepodepsané a mít délku 8 až 64 bitů.

## <a name="remarks"></a>Poznámky

Další informace o typech šablon `T` a `E`, naleznete v tématu [SafeInt – třída](../windows/safeint-class.md).

Vstupní parametr pro konstruktor, *můžu* nebo *u*, musí být typu logická hodnota, znak nebo celé číslo. Pokud je jiný typ parametru, **SafeInt** třídy volání [static_assert](../cpp/static-assert.md) udávajících Neplatný vstupní parametr.

Konstruktory, které používají typ šablony `U` automaticky převést na typ zadaný vstupní parametr `T`. **SafeInt** převede data bez ztráty dat třídy. Oznámí na obslužnou rutinu chyby `E` Pokud nemůže převést data na typ `T` bez ztráty dat.

Pokud jste vytvořili **SafeInt** z parametr logické hodnoty, je nutné inicializovat hodnotu okamžitě. Nelze vytvořit **SafeInt** pomocí kódu `SafeInt<bool> sb;`. Tím se vygeneruje chybu kompilace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** safeint.h

**Namespace:** msl::utilities

## <a name="see-also"></a>Viz také

[SafeInt – knihovna](../windows/safeint-library.md)  
[SafeInt – třída](../windows/safeint-class.md)  
[SafeIntException – třída](../windows/safeintexception-class.md)