---
title: Chyba kompilátoru C2503
ms.date: 11/04/2016
f1_keywords:
- C2503
helpviewer_keywords:
- C2503
ms.assetid: da86cc89-fd04-400b-aa8d-a5ffaf7e3918
ms.openlocfilehash: c481a27f19a92f47a19f0cfaa7b59cd509bb3c15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660808"
---
# <a name="compiler-error-c2503"></a>Chyba kompilátoru C2503

'class': základní třídy nemůžou obsahovat pole s nulovou velikostí

Základní třída nebo struktura obsahuje pole s nulovou velikostí. Pole ve třídě musí mít alespoň jeden element.

Následující ukázka generuje C2503:

```
// C2503.cpp
// compile with: /c
class A {
   public:
   int array [];
};

class B : A {};    // C2503

class C {
public:
   int array [10];
};

class D : C {};
```