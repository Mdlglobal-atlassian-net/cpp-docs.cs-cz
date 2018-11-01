---
title: Kompilátor upozornění (úroveň 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: 84045ea2c285be8b1c1c9d1fd62b417db00dd29c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445315"
---
# <a name="compiler-warning-level-2-c4396"></a>Kompilátor upozornění (úroveň 2) C4396

"name": specifikátor inline nejde použít, když deklarace friend odkazuje na specializaci šablony funkce

Specializace šablony funkcí nemůže určit kterékoli z [vložené](../../cpp/inline-functions-cpp.md) specifikátorů. Kompilátor vydá upozornění C4396 a ignoruje specifikátor inline.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte `inline`, `__inline`, nebo `__forceinline` specifikátor v deklaraci funkce friend.

## <a name="example"></a>Příklad

Následující příklad ukazuje kód neplatný spřátelené funkce deklarace s `inline` specifikátor.

```
// C4396.cpp
// compile with: /W2 /c

class X;
template<class T> void Func(T t, int i);

class X {
    friend inline void Func<char>(char t, int i);  //C4396
// try the following line instead
//    friend void Func<char>(char t, int i);
    int i;
};
```