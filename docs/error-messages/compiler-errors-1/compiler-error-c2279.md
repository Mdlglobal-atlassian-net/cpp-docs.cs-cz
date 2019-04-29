---
title: Chyba kompilátoru C2279
ms.date: 11/04/2016
f1_keywords:
- C2279
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
ms.openlocfilehash: f35e384a5b242eb28427e1ff62ac55a3e9b206c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388856"
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