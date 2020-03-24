---
title: Upozornění kompilátoru (úroveň 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: f37fcc7ece09bb9028a522ec6baf85d0e0e585c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161812"
---
# <a name="compiler-warning-level-2-c4396"></a>Upozornění kompilátoru (úroveň 2) C4396

"Name": specifikátor inline nelze použít, pokud deklarace typu Friend odkazuje na specializaci šablony funkce.

Specializace šablony funkce nemůže určovat žádný z [vložených](../../cpp/inline-functions-cpp.md) specifikátorů. Kompilátor vydá upozornění C4396 a ignoruje vložený specifikátor.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte z deklarace funkce Friend specifikátor `inline`, `__inline`nebo `__forceinline`.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje neplatnou deklaraci funkce Friend s specifikátorem `inline`.

```cpp
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
