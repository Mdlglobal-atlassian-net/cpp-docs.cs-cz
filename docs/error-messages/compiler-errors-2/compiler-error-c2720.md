---
title: Chyba kompilátoru C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: 24f4329ee631eafc7c2670d9ebf28609c22e7592
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202128"
---
# <a name="compiler-error-c2720"></a>Chyba kompilátoru C2720

> '*Identifier*': specifikátor *' třídy úložiště ' není pro*členy platný

Třídu úložiště nelze použít pro členy třídy mimo deklaraci. Chcete-li tuto chybu opravit, odeberte z definice člena mimo deklaraci třídy nepotřebný specifikátor [třídy úložiště](../../cpp/storage-classes-cpp.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C2720 a ukazuje, jak ji opravit:

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```
