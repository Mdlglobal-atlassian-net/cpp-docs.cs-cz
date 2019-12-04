---
title: Chyba kompilátoru C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 69613a1058bd5178ea4c03931664dd00bad7a101
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748993"
---
# <a name="compiler-error-c3909"></a>Chyba kompilátoru C3909

aWinRT nebo spravovaná deklarace události se musí vyskytovat v WinRT nebo spravovaném typu.

Událost prostředí Windows Runtime nebo spravovaná událost byla deklarována v nativním typu. Chcete-li tuto chybu opravit, deklarujte události v prostředí Windows Runtimech typech nebo spravovaných typech.

Další informace najdete v tématu [událost](../../extensions/event-cpp-component-extensions.md).

Následující ukázka generuje C3909 a ukazuje, jak ji opravit:

```cpp
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
