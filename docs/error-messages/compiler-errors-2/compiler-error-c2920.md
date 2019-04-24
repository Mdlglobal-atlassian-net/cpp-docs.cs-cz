---
title: Chyba kompilátoru C2920
ms.date: 11/04/2016
f1_keywords:
- C2920
helpviewer_keywords:
- C2920
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
ms.openlocfilehash: 28bbbd30bcb16e2ea5fc14fe0f48f86814ee13c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311667"
---
# <a name="compiler-error-c2920"></a>Chyba kompilátoru C2920

Předefinování: 'class': Třída šablona nebo obecná hodnota již byl deklarován jako 'type'

Třída rozvrhy generic nebo šablony má více deklarací, které nejsou ekvivalentní. Chcete-li vyřešit tuto chybu, použijte jiné názvy pro různé typy nebo odeberte předefinování název typu.

Následující ukázka generuje C2920 a ukazuje, jak ho opravit:

```
// C2920.cpp
// compile with: /c
typedef int TC1;
template <class T>
struct TC1 {};   // C2920
struct TC2 {};   // OK - fix by using a different name
```

C2920 může dojít také při použití obecných typů:

```
// C2920b.cpp
// compile with: /clr /c
typedef int GC1;
generic <class T>
ref struct GC1 {};   // C2920
ref struct GC2 {};   // OK - fix by using a different name
```