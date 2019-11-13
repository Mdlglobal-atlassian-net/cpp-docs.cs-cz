---
title: Upozornění kompilátoru (úroveň 1) C4546
ms.date: 11/04/2016
f1_keywords:
- C4546
helpviewer_keywords:
- C4546
ms.assetid: 071e1709-3841-46c1-8e71-96109cd22041
ms.openlocfilehash: 7c2e47b92050bb83b1f55836e633d9749bb5e309
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966420"
---
# <a name="compiler-warning-level-1-c4546"></a>Upozornění kompilátoru (úroveň 1) C4546

volání funkce před čárkou nemá seznamu argumentů

Kompilátor zjistil výraz čárky ve formátu nesprávně vytvořeného výrazu.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4546:

```cpp
// C4546.cpp
// compile with: /W1
#pragma warning (default : 4546)
void f(int i) {
   i++;
}

int main() {
   int i = 0, k = 0;

   if ( f, k )   // C4546
   // try the following line instead
   // if ( f(i), k )
      i++;
}
```