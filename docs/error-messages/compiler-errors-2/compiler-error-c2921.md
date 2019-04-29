---
title: Compiler Error C2921
ms.date: 11/04/2016
f1_keywords:
- C2921
helpviewer_keywords:
- C2921
ms.assetid: 323642a0-bfc4-4942-9f41-c3adf5c54296
ms.openlocfilehash: 47f348f6c30d96e8c4ae40e0c26a8ebade14c8ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385872"
---
# <a name="compiler-error-c2921"></a>Compiler Error C2921

Předefinování: 'class': Třída šablona nebo obecná hodnota je znovu deklarován jako 'type'

Třída rozvrhy generic nebo šablony má více deklarací, které nejsou ekvivalentní. Chcete-li vyřešit tuto chybu, použijte jiné názvy pro různé typy nebo odeberte předefinování název typu.

Následující ukázka generuje C2921:

```
// C2921.cpp
// compile with: /c
template <class T> struct TC2 {};
typedef int TC2;   // C2921
// try the following line instead
// typedef struct TC2<int> x;   // OK - declare a template instance
```

C2921 může dojít také při použití obecných typů.

```
// C2921b.cpp
// compile with: /clr /c
generic <class T> ref struct GC2 {};
typedef int GC2;   // C2921
// try the following line instead
// typedef ref struct GC2<int> x;
```