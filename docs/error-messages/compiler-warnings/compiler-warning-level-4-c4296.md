---
title: Upozornění (úroveň 4) C4296 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4296
dev_langs:
- C++
helpviewer_keywords:
- C4296
ms.assetid: 9d99aafe-f6bd-4ee0-b8d0-98ce5712274d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a687c885a3388e01b2089aca1b399d0559803128
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045613"
---
# <a name="compiler-warning-level-4-c4296"></a>Kompilátor upozornění (úroveň 4) C4296

'operator': výraz je vždy nepravda

Proměnná typu bez znaménka byla použita v operaci porovnání s hodnotou nula.

Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.

Následující ukázka generuje C4296:

```
// C4296.cpp
// compile with: /W4
#pragma warning(default : 4296)
int main()
{
   unsigned int u = 9;
   if (u < 0)    // C4296
      u++;
   if (u >= 0)   // C4296
      u++;
}
```