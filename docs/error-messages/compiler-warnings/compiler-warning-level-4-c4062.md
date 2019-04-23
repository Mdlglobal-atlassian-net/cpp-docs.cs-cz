---
title: Kompilátor upozornění (úroveň 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 79658afc31565b708cdbd8a88f49b887cdd10cf3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59237182"
---
# <a name="compiler-warning-level-4-c4062"></a>Kompilátor upozornění (úroveň 4) C4062

> Enumerátor "*identifikátor*"v přepnutí výčtu'*výčet*' není zpracován

Enumerátor *identifikátor* nemá žádné přidružené `case` obslužné rutiny v `switch` příkaz a neexistuje žádné `default` popisek, který může zachytit. Chybí příkaz case může být dohledu a se potenciální chyby v kódu. Pro související upozornění na nevyužitých výčty v `switch` příkazy, které mají `default` případu, viz [C4061](compiler-warning-level-4-c4061.md).

Toto upozornění je vypnuto ve výchozím nastavení. Další informace o tom, jak povolit upozornění, které jsou ve výchozím nastavení vypnuta, najdete v části [kompilátoru upozornění, která je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4062 a ukazuje, jak ho opravit:

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>Viz také:

[Upozornění kompilátoru (úroveň 4) C4061](compiler-warning-level-4-c4061.md)
