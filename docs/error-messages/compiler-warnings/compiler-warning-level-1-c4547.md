---
title: Upozornění kompilátoru (úroveň 1) C4547
ms.date: 11/04/2016
f1_keywords:
- C4547
helpviewer_keywords:
- C4547
ms.assetid: 3edf1c2e-c0d5-444d-ae83-44a7cce24bb2
ms.openlocfilehash: 2a456d2fc4097dd01524f9b62d46dc49160cd7d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186241"
---
# <a name="compiler-warning-level-1-c4547"></a>Upozornění kompilátoru (úroveň 1) C4547

' operator ': operátor před čárkou nemá žádný vliv; očekával se operátor s vedlejším účinkem.

Kompilátor zjistil výraz čárky ve formátu nesprávně vytvořeného výrazu.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Následující ukázka generuje C4547:

```cpp
// C4547.cpp
// compile with: /W1
#pragma warning (default : 4547)
int i = 0;
int j = 1;
int main() {
   int l = (i != i,0);   // C4547
   // try the following line instead
   // int l = (i != i);
   // or
   // int l = ((void)(i != i),0);
}
```
