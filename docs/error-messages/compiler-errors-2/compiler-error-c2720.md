---
title: Chyba kompilátoru C2720 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2720
dev_langs:
- C++
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2d75c9847016102d4ae8609fb0a0a78726e4c67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084013"
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