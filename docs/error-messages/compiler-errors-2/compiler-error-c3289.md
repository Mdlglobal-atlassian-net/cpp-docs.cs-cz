---
title: Chyba kompilátoru C3289
ms.date: 11/04/2016
f1_keywords:
- C3289
helpviewer_keywords:
- C3289
ms.assetid: 3c1c623b-7fcf-43ab-a89a-8722532a8d29
ms.openlocfilehash: ee80fb2c917281163156ef148403088cef8e8545
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760163"
---
# <a name="compiler-error-c3289"></a>Chyba kompilátoru C3289

' Property ': triviální vlastnost nemůže být indexována

Vlastnost byla deklarována nesprávně. Pro indexovanou vlastnost je nutné definovat přístupové objekty. Další informace najdete v tématu [vlastnost](../../extensions/property-cpp-component-extensions.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C3289.

```cpp
// C3289.cpp
// compile with: /clr
public ref struct C {
   // user-defined simple indexer
   property int indexer1[int];   // C3289

   // user-defined indexer
   property int indexer2[int] {
      int get(int i) { return 0; }
      void set(int i, int j) {}
   }
};

int main() {
   C ^ MyC = gcnew C();
   MyC->indexer2[0] = 1;
}
```
