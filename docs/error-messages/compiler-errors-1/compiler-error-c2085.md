---
title: Chyba kompilátoru C2085 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d88968e49e38a13782dde2d905a614ad4d177e81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082375"
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