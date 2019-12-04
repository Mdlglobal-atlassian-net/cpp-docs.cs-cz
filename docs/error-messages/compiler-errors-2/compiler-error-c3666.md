---
title: Chyba kompilátoru C3666
ms.date: 11/04/2016
f1_keywords:
- C3666
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
ms.openlocfilehash: 990dea32b2928671f426235138698071fe038f63
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758148"
---
# <a name="compiler-error-c3666"></a>Chyba kompilátoru C3666

' konstruktor ': specifikátor override ' klíčové slovo ' není pro konstruktor povolen

V konstruktoru se použil specifikátor přepsání, který není povolený. Další informace najdete v tématu [specifikátory přepisu](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3666.

```cpp
// C3666.cpp
// compile with: /clr /c
ref struct R {
   R() new {}   // C3666
   R(int i) {}   // OK
};
```
