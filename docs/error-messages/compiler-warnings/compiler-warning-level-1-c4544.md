---
title: Upozornění kompilátoru (úroveň 1) C4544
ms.date: 11/04/2016
f1_keywords:
- C4544
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
ms.openlocfilehash: 094662270569c7362b7bb3c4953a466b19ed2e65
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966484"
---
# <a name="compiler-warning-level-1-c4544"></a>Upozornění kompilátoru (úroveň 1) C4544

deklarace: výchozí argument šablony se pro tuto deklaraci šablony ignoruje.

Výchozí argument šablony byl zadán v nesprávném umístění a byl ignorován. Výchozí argument šablony pro šablonu třídy lze zadat pouze v deklaraci nebo definici šablony třídy, nikoli v členu šablony třídy.

Tato ukázka vygeneruje C4545 a další ukázka ukazuje, jak ji opravit:

```cpp
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

V tomto příkladu se výchozí parametr vztahuje na šablonu třídy `S`:

```cpp
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