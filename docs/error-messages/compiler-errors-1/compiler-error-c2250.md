---
title: Chyba kompilátoru C2250
ms.date: 11/04/2016
f1_keywords:
- C2250
helpviewer_keywords:
- C2250
ms.assetid: f990986f-5c7d-4af4-a25c-b35540f1e217
ms.openlocfilehash: ea426e071eecb09359c3a99a6f569f628595784a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301354"
---
# <a name="compiler-error-c2250"></a>Chyba kompilátoru C2250

'identifier': nejednoznačné dědění "class::member.

Odvozená třída dědí více než jedno přepsání virtuální funkce virtuální základní třídy. Tato přepsání jsou nejednoznačné v odvozené třídě.

Následující ukázka generuje C2286:

```
// C2250.cpp
// compile with: /c
// C2250 expected
struct V {
   virtual void vf();
};

struct A : virtual V {
   void vf();
};

struct B : virtual V {
   void vf();
};

struct D : A, B {
   // Uncomment the following line to resolve.
   // void vf();
};
```