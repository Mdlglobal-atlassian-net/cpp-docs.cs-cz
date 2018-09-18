---
title: Chyba kompilátoru C2511 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2511
dev_langs:
- C++
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b628adda383baee0f2ec03ace715d94c6cca764c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058143"
---
# <a name="compiler-error-c2511"></a>Chyba kompilátoru C2511

'identifier': členská funkce, nebyl nalezen v 'class' přetížení

Žádná verze funkce je deklarovaná se zadanými parametry.  Možné příčiny:

1. Funkci byl předán chybný parametry.

1. Parametry předané v nesprávném pořadí.

1. Překlep názvy parametrů.

Následující ukázka generuje C2511:

```
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