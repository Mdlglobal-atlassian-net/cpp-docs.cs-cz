---
title: Chyba kompilátoru C2279 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2279
dev_langs:
- C++
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1b194476e6400618045324a14c9e4781f9ec8f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067945"
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