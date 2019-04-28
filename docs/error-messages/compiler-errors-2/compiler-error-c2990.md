---
title: Compiler Error C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: f7327b7d2b0cc9fa4b617a9a6033116c43db6258
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366326"
---
# <a name="compiler-error-c2990"></a>Compiler Error C2990

'class': typ bez třídy, které jsou už byl deklarován jako typ třídy.

Bez obecného nebo třída šablony předefinuje rozvrhy generic nebo šablony třídy. Zkontrolujte soubory hlaviček pro je v konfliktu.

Následující ukázka generuje C2990:

```
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

C2990 může dojít také při použití obecných typů:

```
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

C2990 může také dojít z důvodu rozbíjející změny v kompilátoru jazyka Visual C++ pro Visual C++ 2005; Kompilátor nyní vyžaduje, aby více deklarací stejného typu identické s ohledem na specifikaci šablony.

Následující ukázka generuje C2990:

```
// C2990c.cpp
// compile with: /c
template<class T>
class A;

template<class T>
struct A2 {
   friend class A;   // C2990
};

// OK
template<class T>
struct B {
   template<class T>
   friend class A;
};
```