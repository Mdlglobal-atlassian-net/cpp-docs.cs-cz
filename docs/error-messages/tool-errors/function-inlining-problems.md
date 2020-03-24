---
title: Problémy vložené funkce
ms.date: 11/04/2016
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
ms.openlocfilehash: cb4653bd2f03683b9abad1eea0e9ffa88222090e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184239"
---
# <a name="function-inlining-problems"></a>Problémy vložené funkce

Pokud používáte vkládání funkcí, musíte:

- Vložené funkce jsou implementované v hlavičkovém souboru, který zahrnete.

- V hlavičkovém souboru je zapnuté vkládání.

```cpp
// LNK2019_function_inline.cpp
// compile with: /c
// post-build command: lib LNK2019_function_inline.obj
#include <stdio.h>
struct _load_config_used {
   void Test();
   void Test2() { printf("in Test2\n"); }
};

void _load_config_used::Test() { printf("in Test\n"); }
```

a potom

```cpp
// LNK2019_function_inline_2.cpp
// compile with: LNK2019_function_inline.lib
struct _load_config_used {
   void Test();
   void Test2();
};

int main() {
   _load_config_used x;
   x.Test();
   x.Test2();   // LNK2019
}
```

Pokud používáte direktivu `#pragma inline_depth` kompilátoru, ujistěte se, že máte nastavenou hodnotu 2 nebo vyšší. Hodnota nula vypne vkládání. Také se ujistěte, že používáte možnosti kompilátoru **/OB1** nebo **/Ob2** .

Při kombinování vložených a nevložených možností kompilace v různých modulech může někdy dojít k potížím. Pokud je C++ vytvořená knihovna se zapnutým vkládáním funkcí ([/OB1](../../build/reference/ob-inline-function-expansion.md) nebo [/Ob2](../../build/reference/ob-inline-function-expansion.md)), ale odpovídající hlavičkový soubor, který popisuje funkce pro obložení vypnuto (bez možnosti), se zobrazí chyba linkerů LNK2001. Funkce nejsou vloženy do kódu ze souboru hlaviček, ale vzhledem k tomu, že nejsou v souboru knihovny, není k dispozici žádná adresa pro vyřešení odkazu.

Podobně, projekt, který používá vkládání funkcí, ještě definuje funkce v souboru. cpp, a ne v hlavičkovém souboru, bude také mít LINKERŮ LNK2019. Hlavičkový soubor obsahuje všude považované za vhodné, ale funkce jsou vloženy pouze v případě, že soubor. cpp projde kompilátorem; Proto linker uvidí funkce jako nevyřešené externí typy při použití v jiných modulech.

```cpp
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

a potom

```cpp
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

a potom

```cpp
// LNK2019_FIP_2.cpp
// compile with: LNK2019_FIP.cpp
// LNK2019 expected
#include "LNK2019_FIP.h"
int main() {
   testclass testclsObject;

   // module cannot see the implementation of PublicStatMemFunc1
   testclsObject.PublicStatMemFunc1();
}
```

## <a name="see-also"></a>Viz také

[Chyba linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
