---
title: Chyba kompilátoru C2078
ms.date: 11/04/2016
f1_keywords:
- C2078
helpviewer_keywords:
- C2078
ms.assetid: 9bead850-4123-46cf-a634-5c77ba974b2b
ms.openlocfilehash: 514776c0feb12c46dea56dd8e85043345754a229
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756445"
---
# <a name="compiler-error-c2078"></a>Chyba kompilátoru C2078

příliš mnoho inicializátorů

Počet inicializátorů překračuje počet objektů, které mají být inicializovány.

Kompilátor může odvodit správné přiřazení inicializátorů objektům a vnitřním objektům, když jsou vnitřní složené závorky vynechaného Copy ze seznamu inicializátorů. Úplné složené závorky také eliminují nejednoznačnost a výsledkem je správné přiřazení. Částečné složené závorky můžou způsobit C2078 z důvodu nejednoznačnosti v přiřazení inicializátorů k objektům.

Následující ukázka generuje C2078 a ukazuje, jak ji opravit:

```cpp
// C2078.cpp
// Compile by using: cl /c /W4 C2078.cpp
struct S {
   struct {
      int x, y;
   } z[2];
};

int main() {
   int d[2] = {1, 2, 3};   // C2078
   int e[2] = {1, 2};      // OK

   char a[] = {"a", "b"};  // C2078
   char *b[] = {"a", "b"}; // OK
   char c[] = {'a', 'b'};  // OK

   S s1{1, 2, 3, 4};       // OK
   S s2{{1, 2}, {3, 4}};   // C2078
   S s3{{1, 2, 3, 4}};     // OK
   S s4{{{1, 2}, {3, 4}}}; // OK
}
```
