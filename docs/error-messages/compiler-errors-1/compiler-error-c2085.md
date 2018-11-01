---
title: Chyba kompilátoru C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: a65e3c0ea622950b99b9ba83fc168b4718d13e46
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560157"
---
# <a name="compiler-error-c2085"></a>Chyba kompilátoru C2085

'identifier': není v seznamu formálních parametrů.

Identifikátor byl deklarován v definici funkce, ale ne v seznamu formálních parametrů. (Pouze ANSI C)

Následující ukázka generuje C2085:

```
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

Možná řešení:

```
// C2085b.c
void func1( void );
int main( void ) {}
```

S chybějícími středník, `func1()` vypadá jako definice funkce, nikoli prototyp, takže `main` je definována v rámci `func1()`, generuje se chyba C2085 pro identifikátor `main`.