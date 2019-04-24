---
title: Kompilátor upozornění (úroveň 4) C4510
ms.date: 11/04/2016
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 80183e9f7ef17cbc37592f36eb8db1df2be94827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221086"
---
# <a name="compiler-warning-level-4-c4510"></a>Kompilátor upozornění (úroveň 4) C4510

'class': nebylo možné vygenerovat výchozí konstruktor.

Kompilátor nemůže generovat výchozí konstruktor pro zadanou třídu a byl vytvořen žádný uživatelem definovaný konstruktor. Nebudete moct vytvořit objekty tohoto typu.

Existuje několik situací, které zabránění kompilátoru generování výchozího konstruktoru, včetně:

- Datový člen const.

- Datový člen, který je odkaz.

Je potřeba vytvořit uživatelem definovaný výchozí konstruktor pro třídu, která inicializuje těchto členů.

Následující ukázka generuje C4510:

```
// C4510.cpp
// compile with: /W4
struct A {
   const int i;
   int &j;
   A& operator=( const A& ); // C4510 expected
   // uncomment the following line to resolve this C4510
   // A(int ii, int &jj) : i(ii), j(jj) {}
};   // C4510

int main() {
}
```