---
title: Chyba kompilátoru C2533
ms.date: 11/04/2016
f1_keywords:
- C2533
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
ms.openlocfilehash: 00cb13d1999b00dfcaa5a2bc7bfb3b8eb16af5f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661874"
---
# <a name="compiler-error-c2533"></a>Chyba kompilátoru C2533

'identifier': konstruktory není povolený návratový typ.

Konstruktor nemůže mít návratový typ (včetně `void` návratový typ).

Běžné příčiny této chyby je chybí středník mezi koncem definice třídy a první implementaci konstruktoru. Kompilátor považuje definici návratový typ funkce konstruktoru třídy a generuje C2533.

Následující ukázka generuje C2533 a ukazuje, jak ho opravit:

```
// C2533.cpp
// compile with: /c
class X {
public:
   X();
};

int X::X() {}   // C2533 - constructor return type not allowed
X::X() {}   // OK - fix by using no return type
```