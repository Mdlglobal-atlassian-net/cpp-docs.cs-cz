---
title: Chyba kompilátoru C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 435288ba657bd22ba29c6681014ae15baa051cec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636459"
---
# <a name="compiler-error-c3909"></a>Chyba kompilátoru C3909

aWinRT nebo deklaraci spravovaného události musí proběhnout v WinRT nebo spravovaného typu

Událost Windows Runtimu nebo spravovaných událostí byl deklarován v nativním typu. Chcete-li tuto chybu opravit, deklarujte události v typy Windows Runtime nebo spravované typy.

Další informace najdete v tématu [události](../../windows/event-cpp-component-extensions.md).

Následující ukázka generuje C3909 a ukazuje, jak ho opravit:

```
// C3909.cpp
// compile with: /clr /c
delegate void H();
class X {
   event H^ E;   // C3909 - use ref class X instead
};

ref class Y {
   static event H^ E {
      void add(H^) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```