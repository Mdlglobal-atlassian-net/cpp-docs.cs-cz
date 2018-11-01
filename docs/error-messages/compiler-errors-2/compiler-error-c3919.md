---
title: Chyba kompilátoru C3919
ms.date: 11/04/2016
f1_keywords:
- C3919
helpviewer_keywords:
- C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
ms.openlocfilehash: 0fe7e61c28ad2688a6d97b4164c2b5cfa81a37b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474864"
---
# <a name="compiler-error-c3919"></a>Chyba kompilátoru C3919

'event_method': funkce musí mít typ 'type'

Metoda přístupového objektu události nebyl deklarován správně.

Další informace o událostech najdete v tématu [události](../../windows/event-cpp-component-extensions.md).

Následující ukázka generuje C3919:

```
// C3919.cpp
// compile with: /clr /c
using namespace System;
delegate void D(String^);
ref class R {
   event D^ e {
      int add(int);   // C3919
      int remove(int);   // C3919

      void add(D^);   // OK
      void remove(D^);   // OK
   }
};
```