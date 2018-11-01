---
title: Chyba kompilátoru C3060
ms.date: 11/04/2016
f1_keywords:
- C3060
helpviewer_keywords:
- C3060
ms.assetid: 6282bb92-0546-4b59-9435-d3840bf93bdb
ms.openlocfilehash: c77af7fa1220aa5211d480cddf3bf0979c642ade
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515398"
---
# <a name="compiler-error-c3060"></a>Chyba kompilátoru C3060

'member': funkce friend nemůže být definovaná uvnitř třídy pomocí kvalifikovaného názvu (to může být jedině deklarovaná)

Funkce friend byl definován pomocí kvalifikovaného názvu, což není povoleno.

Následující ukázka generuje C3060:

```
// C3060.cpp
class A {
public:
   void func();
};

class C {
public:
   friend void A::func() { }   // C3060
   // Try the following line and the out of class definition:
   // friend void A::func();
};

// void A::func(){}
```