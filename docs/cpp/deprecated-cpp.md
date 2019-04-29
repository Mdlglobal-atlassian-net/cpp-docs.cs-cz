---
title: deprecated (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: 34f9c10cd898b0359463d5933141822576fa4a11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398950"
---
# <a name="deprecated-c"></a>deprecated (C++)

Toto téma se věnuje specifické pro Microsoft zastaralé declspec deklarace. Informace o C ++ 14 `[[deprecated]]` atribut a pokyny, kdy použít tento atribut vs. declspec specifické pro společnost Microsoft nebo direktivy pragma, najdete v části [C++ standardní atributy](attributes.md).

S výjimkami uvedenými níže **zastaralé** nabízí stejné funkce jako deklarace [zastaralé](../preprocessor/deprecated-c-cpp.md) – Direktiva pragma:

- **Zastaralé** deklarace umožňuje určit konkrétní podoby přetížení funkce jako zastaralé, kdežto forma direktivy pragma se vztahuje na všechny přetížené formy názvu funkce.

- **Zastaralé** deklarace umožňuje zadat zprávu, která se zobrazí v době kompilace. Text zprávy může být z makra.

- Makra lze pouze označené jako zastaralé s **zastaralé** direktivy pragma.

Pokud kompilátor narazí na použití zastaralého identifikátoru nebo standardní [ `[[deprecated]]` ](attributes.md) atribut [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) je vyvoláno upozornění.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak označit funkce jako zastaralé a jak určit zprávu, která se zobrazí v době kompilace při použití zastaralé funkce.

```cpp
// deprecated.cpp
// compile with: /W3
#define MY_TEXT "function is deprecated"
void func1(void) {}
__declspec(deprecated) void func1(int) {}
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}
__declspec(deprecated(MY_TEXT)) void func3(int) {}

int main() {
   func1();
   func1(1);   // C4996
   func2(1);   // C4996
   func3(1);   // C4996
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak označit třídy jako zastaralé a jak určit zprávu, která se zobrazí v době kompilace při použití zastaralé třídy.

```cpp
// deprecate_class.cpp
// compile with: /W3
struct __declspec(deprecated) X {
   void f(){}
};

struct __declspec(deprecated("** X2 is deprecated **")) X2 {
   void f(){}
};

int main() {
   X x;   // C4996
   X2 x2;   // C4996
}
```

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)