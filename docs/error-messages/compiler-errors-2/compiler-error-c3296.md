---
title: Compiler Error C3296
ms.date: 11/04/2016
f1_keywords:
- C3296
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
ms.openlocfilehash: c0a162590ac2a72dda17b2ecfc96899e94cde24c
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767038"
---
# <a name="compiler-error-c3296"></a>Compiler Error C3296

'property': vlastnost s tímto názvem již existuje.

Kompilátoru došlo k více než jednu vlastnost se stejným názvem. Každou vlastnost v typu musí mít jedinečný název.

Další informace najdete v tématu [vlastnost](../../extensions/property-cpp-component-extensions.md).

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