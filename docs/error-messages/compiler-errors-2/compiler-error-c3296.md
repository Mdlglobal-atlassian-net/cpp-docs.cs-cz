---
title: Chyba kompilátoru C3296
ms.date: 11/04/2016
f1_keywords:
- C3296
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
ms.openlocfilehash: 2e9787b063a5a37af8d0e0fdd04492a743792646
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588107"
---
# <a name="compiler-error-c3296"></a>Chyba kompilátoru C3296

'property': vlastnost s tímto názvem již existuje.

Kompilátoru došlo k více než jednu vlastnost se stejným názvem. Každou vlastnost v typu musí mít jedinečný název.

Další informace najdete v tématu [vlastnost](../../windows/property-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3296.

```
// C3296.cpp
// compile with: /clr /c
using namespace System;

ref class R {
public:
   property int MyProp[int] { int get(int); }

   property String^ MyProp[int] { void set(int, String^); }   // C3296
};
```