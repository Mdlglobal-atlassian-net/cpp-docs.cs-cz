---
title: Chyba kompilátoru C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: 6a51901477958056356a96d71adde4241d60a2ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750582"
---
# <a name="compiler-error-c2825"></a>Chyba kompilátoru C2825

var: musí být třídou nebo oborem názvů, pokud následuje::

Byl proveden neúspěšný pokus o vytvoření kvalifikovaného názvu.

Ujistěte se například, že váš kód neobsahuje deklaraci funkce, kde název funkce začíná na::.

## <a name="example"></a>Příklad

Následující ukázka generuje C2825:

```cpp
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```
