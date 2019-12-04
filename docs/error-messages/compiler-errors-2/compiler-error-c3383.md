---
title: Chyba kompilátoru C3383
ms.date: 11/04/2016
f1_keywords:
- C3383
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
ms.openlocfilehash: ceae17689cbcb9585fb3722580042187ff64a6ee
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755626"
---
# <a name="compiler-error-c3383"></a>Chyba kompilátoru C3383

klíčové slovo operator new se nepodporuje s možností/CLR: safe.

Výstupní soubor kompilace **/clr: Safe** je soubor, který je ověřitelný jako bezpečný typ a ukazatele nejsou podporovány.

Další informace najdete v tématu.

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Obecné problémy migrace v 64bitovém prostředí Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Příklad

Následující ukázka generuje C3383.

```cpp
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```
