---
title: Upozornění kompilátoru (úroveň 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: e874e00d44eef29240cca55541837facfcf64495
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052030"
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