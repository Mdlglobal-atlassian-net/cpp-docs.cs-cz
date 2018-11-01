---
title: Chyba kompilátoru C2190
ms.date: 11/04/2016
f1_keywords:
- C2190
helpviewer_keywords:
- C2190
ms.assetid: 34e15f85-d979-4948-80fc-46c414508a70
ms.openlocfilehash: b52797b945b1a652506b4a85171e60a91544bbf0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546477"
---
# <a name="compiler-error-c2190"></a>Chyba kompilátoru C2190

první seznam parametrů je delší než druhý.

Funkce jazyka C se deklaroval podruhé s kratším seznamem parametrů. C nepodporuje přetížené funkce.

Následující ukázka generuje C2190:

```
// C2190.c
// compile with: /Za /c
void func( int, float );
void func( int  );   // C2190, different parameter list
void func2( int  );   // OK
```