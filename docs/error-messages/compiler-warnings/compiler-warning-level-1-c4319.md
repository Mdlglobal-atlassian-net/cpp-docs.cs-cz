---
title: "Kompilátoru (úroveň 1) upozornění C4319 | Microsoft Docs"
ms.custom: 
ms.date: 1/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4319
dev_langs:
- C++
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a492194003a639f684e84d125450067cd425276
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="compiler-warning-level-1-c4319"></a>C4319 kompilátoru upozornění (úroveň 1)

> ' ~': nulové rozšíření '*type1*'do'*type2*' větší velikosti

Výsledkem  **~**  (bitového doplňku) operátor je nepodepsané a pak nula rozšířené, když je převést na typ větší.

## <a name="example"></a>Příklad

V následujícím příkladu `~(a - 1)` je vyhodnocena jako výraz bez znaménka dlouho 32bitová verze a následně převeden na 64 bitů nulové rozšíření. To může vést k operaci neočekávané výsledky.

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
