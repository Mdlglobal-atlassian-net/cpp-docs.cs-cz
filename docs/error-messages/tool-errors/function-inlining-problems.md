---
title: Problémy vložené funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98d0ed20881ef89264f7c162750f600c7f68412b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088134"
---
# <a name="function-inlining-problems"></a>Problémy vložené funkce

Pokud používáte funkci vkládání, musíte mít:

- Mít vložené funkce v souboru hlaviček, které jsou implementovány.

- Mít vkládání zapnuté v hlavičkovém souboru.

```
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

a pak,

```
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

Pokud používáte `#pragma inline_depth` kompilátoru direktiv, ujistěte se, že máte hodnotu 2 nebo vyšší nastavení. Hodnota 0 vypne vkládání. Také se ujistěte, že používáte **/Ob1** nebo **/ob2** – možnosti kompilátoru.

Kombinování vložené a které nejsou vložené možnosti kompilace na různých modulů v některých případech může způsobovat problémy. Pokud knihovnu C++ se vytvoří pomocí funkce vkládání zapnuté ([/Ob1](../../build/reference/ob-inline-function-expansion.md) nebo [/ob2](../../build/reference/ob-inline-function-expansion.md)), ale odpovídající soubor záhlaví popisující funkce má vkládání vypnuto (žádná volba), zobrazí se chyba LNK2001. Funkce není vloženy do kódu ze souboru hlaviček, ale protože nejsou v souboru knihovny není žádná adresa přeložit odkaz.

Obdobně projekt, který používá funkci vkládání ještě definuje funkce v souboru s příponou .cpp, spíše než v hlavičce souboru získají LNK2019. Soubor hlaviček je součástí všude, kde považujete za vhodné, ale funkce jsou pouze vložené když soubor .cpp prochází kompilátoru; proto linkeru považuje funkce nerozpoznané externí typy při použití v dalších modulů.

```
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

a pak,

```
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

a pak,

```
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