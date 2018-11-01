---
title: Chyba kompilátoru C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: c6499fd3f279099ea7c5b31860e70bdaa285e3f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638591"
---
# <a name="compiler-error-c2720"></a>Chyba kompilátoru C2720

> "*identifikátor*": "*specifikátor*' není pro členy platný specifikátor třídy úložiště

Třída úložiště se nedá použít u členů třídy mimo deklaraci. Chcete-li tuto chybu vyřešit, odeberte nepotřebné [třídu úložiště](../../cpp/storage-classes-cpp.md) specifikátor z definice členů mimo deklaraci třídy.

## <a name="example"></a>Příklad

Následující ukázka generuje C2720 a ukazuje, jak ho opravit:

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```