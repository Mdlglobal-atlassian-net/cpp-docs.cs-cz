---
title: Chyba kompilátoru C2181
ms.date: 11/04/2016
f1_keywords:
- C2181
helpviewer_keywords:
- C2181
ms.assetid: d52b2fe4-566a-40a9-b8e2-8dce1f287668
ms.openlocfilehash: 64aea11924d9a1624090c2dd6f640ee2f9a037a0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737150"
---
# <a name="compiler-error-c2181"></a>Chyba kompilátoru C2181

neplatné else bez odpovídajícího if

Každý `else` musí mít `if`.

Následující ukázka generuje C2181:

```cpp
// C2181.cpp
int main() {
   int i = 0;
   else   // C2181
      i = 1;
}
```

Možné řešení:

```cpp
// C2181b.cpp
int main() {
   int i = 0;
   if(i)
      i = 0;
   else
      i = 1;
}
```
