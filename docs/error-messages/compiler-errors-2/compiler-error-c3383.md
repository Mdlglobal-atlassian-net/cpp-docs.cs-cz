---
title: Chyba kompilátoru C3383
ms.date: 11/04/2016
f1_keywords:
- C3383
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
ms.openlocfilehash: 38aea188eeac90cd23d9203a53b4e630be2f115b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428012"
---
# <a name="compiler-error-c3383"></a>Chyba kompilátoru C3383

operator new není podporovaná s/clr: safe

Výstupní soubor **/CLR: safe** kompilace je soubor, který je prokazatelně typově bezpečný a ukazatele nejsou podporovány.

Další informace najdete v tématu,

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Obecné problémy migrace v 64bitovém prostředí Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Příklad

Následující ukázka generuje C3383.

```
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```