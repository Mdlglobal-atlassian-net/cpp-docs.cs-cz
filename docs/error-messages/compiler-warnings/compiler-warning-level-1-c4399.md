---
title: Kompilátoru (úroveň 1) upozornění C4399 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aedad6aed07a6056f74ad338037a7268c722627f
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703717"
---
# <a name="compiler-warning-level-1-c4399"></a>C4399 kompilátoru upozornění (úroveň 1)

> '*symbol*': symbol na proces by neměl být označené jako deklarace __declspec(dllimport), když kompilujete s/clr: pure

## <a name="remarks"></a>Poznámky

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Data z nativní bitové kopie nebo bitové kopie pomocí nativní a konstrukce CLR nelze importovat do čisté bitové kopii. Toto upozornění vyřešíte kompilovat s **/CLR** (není **/CLR: pure**) nebo odstranění `__declspec(dllimport)`.

## <a name="example"></a>Příklad

Následující ukázka generuje C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```