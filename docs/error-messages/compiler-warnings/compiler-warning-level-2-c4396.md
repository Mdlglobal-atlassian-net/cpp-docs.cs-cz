---
title: Upozornění (úroveň 2) C4396 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4396
dev_langs:
- C++
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa0a084e90db9d48f517bfe65c6340eb532f0ae6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118567"
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