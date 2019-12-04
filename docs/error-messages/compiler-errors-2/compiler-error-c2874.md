---
title: Chyba kompilátoru C2874
ms.date: 11/04/2016
f1_keywords:
- C2874
helpviewer_keywords:
- C2874
ms.assetid: b54fa9d8-8df5-40d9-9b3b-aa3e9dd6a3be
ms.openlocfilehash: a54cb9dda4ae07ea274eaa970248b9ce9002693b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736370"
---
# <a name="compiler-error-c2874"></a>Chyba kompilátoru C2874

deklarace using-Declaration způsobí vícenásobnou deklaraci symbolu.

Deklarace má za následek definování stejné položky dvakrát.

Následující ukázka generuje C2874:

```cpp
// C2874.cpp
namespace Z {
   int i;
}

int main() {
   int i;
   using Z::i;   // C2874, i already declared
}
```
