---
title: Chyba kompilátoru C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: 5cd7a83575da7ab2a30401406d0c2ccf6c1b603e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438530"
---
# <a name="compiler-error-c2435"></a>Chyba kompilátoru C2435

> "*var*': dynamická inicializace vyžaduje spravované CRT; nejde kompilovat s/clr: safe

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Inicializace proměnné globální domény na aplikaci vyžaduje CRT zkompilovaná `/clr:pure`, který nevytváří ověřitelný bitové kopie.

Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [procesu](../../cpp/process.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2435:

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```