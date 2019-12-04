---
title: Chyba kompilátoru C3382
ms.date: 11/04/2016
f1_keywords:
- C3382
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
ms.openlocfilehash: 419577ddd5b5d7d2d21a91f500070cb190c72117
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760462"
---
# <a name="compiler-error-c3382"></a>Chyba kompilátoru C3382

možnost sizeof není podporovaná s možností/CLR: safe.

Výstupní soubor kompilace **/clr: Safe** je soubor, který je ověřitelný jako bezpečný typ a operátor sizeof není podporován, protože návratová hodnota operátoru sizeof je size_t, jehož velikost se liší v závislosti na operačním systému.

Další informace najdete v tématu.

- [sizeof – operátor](../../cpp/sizeof-operator.md)

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Obecné problémy migrace v 64bitovém prostředí Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Příklad

Následující ukázka generuje C3382.

```cpp
// C3382.cpp
// compile with: /clr:safe
int main() {
   sizeof( char );   // C3382
}
```
