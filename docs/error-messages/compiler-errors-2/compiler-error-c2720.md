---
title: Compiler Error C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: c6499fd3f279099ea7c5b31860e70bdaa285e3f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383045"
---
# <a name="compiler-error-c2720"></a>Compiler Error C2720

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