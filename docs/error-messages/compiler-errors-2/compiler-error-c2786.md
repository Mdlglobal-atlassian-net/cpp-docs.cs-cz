---
title: Chyba kompilátoru C2786
ms.date: 11/04/2016
f1_keywords:
- C2786
helpviewer_keywords:
- C2786
ms.assetid: 6676d8c0-86dd-4a39-bdda-b75a35f4d137
ms.openlocfilehash: ba5d05e9c7cc702509144fb876a1301bfc8bf3d4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739607"
---
# <a name="compiler-error-c2786"></a>Chyba kompilátoru C2786

' type ': neplatný operand pro __uuidof

Operátor [__uuidof](../../cpp/uuidof-operator.md) přebírá uživatelsky definovaný typ s PŘIPOJENým identifikátorem GUID nebo objektem takového uživatelsky definovaného typu.  Možné příčiny:

1. Argument není uživatelem definovaný typ.

1. `__uuidof` nemůže z argumentu extrahovat identifikátor GUID.

Následující ukázka generuje C2786:

```cpp
// C2786.cpp
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};

int main() {
   __uuidof(int);   // C2786
   __uuidof(int *);   // C2786
   __uuidof(A **);   // C2786

   // no error
   __uuidof(A);
   __uuidof(A *);
   __uuidof(A &);
   __uuidof(A[]);

   int i;
   int *pi;
   A **ppa;

   __uuidof(i);      // C2786
   __uuidof(pi);     // C2786
   __uuidof(ppa);    // C2786
}
```
