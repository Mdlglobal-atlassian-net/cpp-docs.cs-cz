---
title: Chyba kompilátoru C2078
ms.date: 11/04/2016
f1_keywords:
- C2078
helpviewer_keywords:
- C2078
ms.assetid: 9bead850-4123-46cf-a634-5c77ba974b2b
ms.openlocfilehash: a800a6efa6e02f323b4b6597f1aa983f13674e83
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182805"
---
# <a name="compiler-error-c2078"></a>Chyba kompilátoru C2078

moc velký počet inicializátorů

Počet inicializátory překračuje počet objektů, které mají být inicializovány.

Kompilátor může odvodit správné přiřazení inicializátory objektů a vnitřních objektů, když vnitřní závorky jsou vynechaného ze seznamu inicializátorů. Kompletní výztuhy také eliminuje nejednoznačnosti a výsledkem správné přiřazení. Částečné výztuhy může způsobit C2078 z důvodu nejednoznačnosti v přiřazení inicializátory objektů.

Následující ukázka generuje C2078 a ukazuje, jak ho opravit:

```
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