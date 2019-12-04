---
title: Chyba kompilátoru C2511
ms.date: 11/04/2016
f1_keywords:
- C2511
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
ms.openlocfilehash: ff78cb50b274fe40d513739264bd7e9894bbed9d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746562"
---
# <a name="compiler-error-c2511"></a>Chyba kompilátoru C2511

' identifier ': členská funkce přetížení se nenašla v ' class '.

Žádná verze funkce není deklarována se zadanými parametry.  Možné příčiny:

1. Do funkce se předaly nesprávné parametry.

1. Parametry byly předány v nesprávném pořadí.

1. Nesprávný pravopis názvů parametrů.

Následující ukázka generuje C2511:

```cpp
// C2511.cpp
// compile with: /c
class C {
   int c_2;
   int Func(char *, char *);
};

int C::Func(char *, char *, int i) {   // C2511
// try the following line instead
// int C::Func(char *, char *) {
   return 0;
}
```
