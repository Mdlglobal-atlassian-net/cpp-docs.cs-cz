---
title: Chyba kompilátoru C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: 27db194cb308d711a259127b628c60b4d10b94ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383227"
---
# <a name="compiler-error-c2477"></a>Chyba kompilátoru C2477

'member': Statický datový člen nejde inicializovat prostřednictvím odvozené třídy

Statický datový člen třídy šablony byl inicializován nesprávně. Toto je k zásadní změně verze kompilátoru Visual C++ před Visual Studio .NET 2003, aby bylo možné v souladu s ISO C++ standard.

Následující ukázka generuje C2477:

```
// C2477.cpp
// compile with: /Za /c
template <class T>
struct S {
   static int n;
};

struct X {};
struct A: S<X> {};

int A::n = 0;   // C2477

template<>
int S<X>::n = 0;
```