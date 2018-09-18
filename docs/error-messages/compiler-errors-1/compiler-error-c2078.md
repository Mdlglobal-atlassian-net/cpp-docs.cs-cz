---
title: Chyba kompilátoru C2078 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2078
dev_langs:
- C++
helpviewer_keywords:
- C2078
ms.assetid: 9bead850-4123-46cf-a634-5c77ba974b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8de17341bfb1ad5031be04e977ab68ae4ed1bcb5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111508"
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