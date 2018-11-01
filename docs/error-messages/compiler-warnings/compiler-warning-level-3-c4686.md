---
title: Kompilátor upozornění (úroveň 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 5e23e6aa69fe8a59e3dfd22af7e33780c223cdd3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584515"
---
# <a name="compiler-warning-level-3-c4686"></a>Kompilátor upozornění (úroveň 3) C4686

> "*uživatelem definovaného typu*': možné změny v chování, změna ve vrácení konvence volání

## <a name="remarks"></a>Poznámky

Specializace šablony třídy nebyl určen předtím, než byl použit v návratovém typu. Cokoli, co vytvoří instanci třídy vyřeší C4686; deklarování instance nebo přístup ke členovi (C\<int >:: NIC) jsou také možnosti.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

## <a name="example"></a>Příklad

Zkuste místo toho následující:

```cpp
// C4686.cpp
// compile with: /W3
#pragma warning (default : 4686)
template <class T>
class C;

template <class T>
C<T> f(T);

template <class T>
class C {};

int main() {
   f(1);   // C4686
}

template <class T>
C<T> f(T) {
   return C<int>();
}
```