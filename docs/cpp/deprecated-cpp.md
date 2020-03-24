---
title: deprecated (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: e4689d3cb1a1757e2ac3bf4ca9eef7670ad5c655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189478"
---
# <a name="deprecated-c"></a>deprecated (C++)

Toto téma se týká deklarace declspec zastaralosti specifické pro společnost Microsoft. Informace o atributu `[[deprecated]]` c++ 14 a pokyny, kdy použít tento atribut vs. declspec nebo pragma specifické pro společnost Microsoft, naleznete v tématu [ C++ standardní atributy](attributes.md).

S výjimkami uvedenými níže, **zastaralá** deklarace nabízí stejné funkce jako [zastaralá](../preprocessor/deprecated-c-cpp.md) direktiva pragma:

- **Zastaralá** deklarace umožňuje určit konkrétní formy přetížení funkce jako zastaralé, zatímco formulář pragma se vztahuje na všechny přetížené formy názvu funkce.

- **Zastaralá** deklarace umožňuje určit zprávu, která se zobrazí v době kompilace. Text zprávy může být z makra.

- Makra mohou být označena jako zastaralá s **vystaralou** direktivou pragma.

Pokud kompilátor narazí na použití zastaralého identifikátoru nebo atributu standardní [`[[deprecated]]`](attributes.md) , je vyvolána [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) upozornění.

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

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
