---
title: Chyba kompilátoru C2506
ms.date: 11/04/2016
f1_keywords:
- C2506
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
ms.openlocfilehash: 02f0a81204c4bc1c41111d32bae1c6946dee09ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575549"
---
# <a name="compiler-error-c2506"></a>Chyba kompilátoru C2506

'member': '__declspec(modifier)' nelze použít pro tento symbol

Na úrovni jednotlivého procesu nebo na úrovni appdomain nelze deklarovat pro statické členy třídy spravované třídy.

Zobrazit [appdomain](../../cpp/appdomain.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C2506.

```
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```