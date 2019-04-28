---
title: Kompilátor upozornění (úroveň 1) C4544
ms.date: 11/04/2016
f1_keywords:
- C4544
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
ms.openlocfilehash: f2a3f2e64a6a859add8182de4fc883c735563e92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352920"
---
# <a name="compiler-warning-level-1-c4544"></a>Kompilátor upozornění (úroveň 1) C4544

"deklarace": Výchozí argument šablony pro tuto deklaraci šablony ignoruje.

Výchozí argument šablony byla zadána nesprávná místě a byla ignorována. Výchozí argument šablony pro šablonu tříd můžete zadat jenom v deklaraci nebo definici šablony třídy a ne na člena šablony třídy.

Tato ukázka vygeneruje C4545 a další příklad ukazuje, jak ho opravit:

```
// C4544.cpp
// compile with: /W1 /LD
template <class T>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T=int>
template <class T1>
struct S<T>::S1 {};   // C4544
```

V tomto příkladu výchozího parametru se vztahuje na šablonu třídy `S`:

```
// C4544b.cpp
// compile with: /LD
template <class T = int>
struct S
{
   template <class T1>
      struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1 {};
```