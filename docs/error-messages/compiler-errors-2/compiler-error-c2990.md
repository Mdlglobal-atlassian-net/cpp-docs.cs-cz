---
title: Chyba kompilátoru C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: 1c58c2d5da0049ec670e11c930b397caec3cbbee
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751518"
---
# <a name="compiler-error-c2990"></a>Chyba kompilátoru C2990

' class ': typ netříděný jako již byl deklarován jako typ třídy

Třída, která není obecná nebo Template, předefinuje obecnou třídu nebo třídu šablony. Ověřte konflikty souborů hlaviček.

Následující ukázka generuje C2990:

```cpp
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

C2990 může také nastat při použití generických typů:

```cpp
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

K C2990 může také dojít z důvodu zásadní změny kompilátoru Microsoft C++ pro Visual Studio 2005; Kompilátor nyní vyžaduje, aby více deklarací pro stejný typ bylo stejné jako v souladu se specifikací šablony.

Následující ukázka generuje C2990:

```cpp
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
