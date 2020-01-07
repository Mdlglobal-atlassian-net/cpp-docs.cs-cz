---
title: Chyba kompilátoru C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: 7dbf7266a6330a1fdb46d7f2df90e7684f026d9a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301961"
---
# <a name="compiler-error-c2085"></a>Chyba kompilátoru C2085

' identifier ': není v seznamu formálních parametrů

Identifikátor byl deklarován v definici funkce, ale není v seznamu formálních parametrů. (Pouze ANSI C)

Následující ukázka generuje C2085:

```c
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

Možné řešení:

```c
// C2085b.c
void func1( void );
int main( void ) {}
```

Chybí-li středník, `func1()` vypadá jako definice funkce, nikoli prototyp, takže `main` je definována v rámci `func1()`, generuje se C2085 chyby pro identifikátor `main`.
