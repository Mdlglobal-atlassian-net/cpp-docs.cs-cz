---
title: Chyba kompilátoru C2382 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2382
dev_langs:
- C++
helpviewer_keywords:
- C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc54ef088cf756918abe385acd3e5bed6b856a8a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085794"
---
# <a name="compiler-error-c2382"></a>Chyba kompilátoru C2382

'function': předefinování; odlišné specifikace výjimek

V části [/Za](../../build/reference/za-ze-disable-language-extensions.md), tato chyba označuje, že se přetížení funkce jenom na pokusil [specifikace výjimky](../../cpp/exception-specifications-throw-cpp.md).

Následující ukázka generuje C2382:

```
// C2382.cpp
// compile with: /Za /c
void f1(void) throw(int) {}
void f1(void) throw(char) {}   // C2382
void f2(void) throw(char) {}   // OK
```