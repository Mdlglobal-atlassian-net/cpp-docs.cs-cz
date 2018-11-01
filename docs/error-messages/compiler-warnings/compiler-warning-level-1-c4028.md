---
title: Kompilátor upozornění (úroveň 1) C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: bfe54fc40b4d6927a1d75f529ec9b619f9b29226
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490512"
---
# <a name="compiler-warning-level-1-c4028"></a>Kompilátor upozornění (úroveň 1) C4028

formální parametr 'number' liší od deklarace

Typ formálního parametru nesouhlasí s odpovídajícím parametrem v deklaraci. Typ v původní deklaraci se používá.

Toto upozornění je platná pouze pro zdrojový kód jazyka C.

## <a name="example"></a>Příklad

Následující ukázka generuje C4028.

```
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```