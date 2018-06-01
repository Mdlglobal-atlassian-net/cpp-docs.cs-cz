---
title: C2435 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2435
dev_langs:
- C++
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ddf078420da8aba170bbd21a0db775f9246cea4
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703639"
---
# <a name="compiler-error-c2435"></a>C2435 chyby kompilátoru

> '*var*': dynamické inicializace vyžaduje spravované CRT, nelze kompilovat s/clr: safe

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Inicializace proměnné globální pro aplikační doménu vyžaduje CRT kompilovat s `/clr:pure`, který nevytváří ověřitelný bitové kopie.

Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [proces](../../cpp/process.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2435:

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```