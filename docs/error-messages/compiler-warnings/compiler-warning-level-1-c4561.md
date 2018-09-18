---
title: Upozornění (úroveň 1) C4561 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4561
dev_langs:
- C++
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba0770a8b8b42c8174d421f55dd45ff7f335d06
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115785"
---
# <a name="compiler-warning-level-1-c4561"></a>Kompilátor upozornění (úroveň 1) C4561

"__fastcall' nekompatibilní s" / clr' možnost: převod na "\__stdcall"

[__Fastcall](../../cpp/fastcall.md) konvence volání funkce nelze použít s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru. Kompilátor ignoruje volání `__fastcall`. Pokud chcete vyřešit toto upozornění, buď odeberte volání **__fastcall** nebo proveďte kompilaci bez **/CLR**.

Následující ukázka generuje C4561:

```
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```