---
title: Chyba kompilátoru C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: c6eb207342f44655d54e49d4cf0cd2410f7095da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562029"
---
# <a name="compiler-error-c3912"></a>Chyba kompilátoru C3912

'událost': typ události musí být typu delegáta

Události byla deklarovaná, ale nemá správný typ.

Další informace najdete v tématu [události](../../windows/event-cpp-component-extensions.md).

Následující ukázka generuje C3912:

```
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```