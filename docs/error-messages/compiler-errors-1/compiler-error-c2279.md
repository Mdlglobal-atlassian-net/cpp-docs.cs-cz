---
title: Chyba kompilátoru C2279
ms.date: 11/04/2016
f1_keywords:
- C2279
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
ms.openlocfilehash: f35e384a5b242eb28427e1ff62ac55a3e9b206c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666217"
---
# <a name="compiler-error-c2279"></a>Chyba kompilátoru C2279

Specifikace výjimky se nemůže vyskytovat v deklaraci typedef.

V části **/Za**, [specifikace výjimek](../../cpp/exception-specifications-throw-cpp.md) nejsou povolené v deklaraci typedef.

Následující ukázka generuje C2279:

```
// C2279.cpp
// compile with: /Za /c
typedef int (*xy)() throw(...);   // C2279
typedef int (*xyz)();   // OK
```