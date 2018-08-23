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
ms.openlocfilehash: 2ddb7092b1a5556485848d122e21ac54b6efe182
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606952"
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

[in] *mi*  
Hodnota pro novou **SafeInt** objektu. Musí se jednat o parametr typu T nebo U, v závislosti na konstruktor.

[in] *b*  
Logická hodnota pro novou **SafeInt** objektu.

[in] *u*  
A **SafeInt** z typu U. Nové **SafeInt** objektu bude mít stejnou hodnotu jako *u*, ale budou typu T.

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