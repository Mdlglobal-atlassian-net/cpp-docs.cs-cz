---
title: Upozornění (úroveň 1) C4258 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4258
dev_langs:
- C++
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4d9aacd6e3681a1eb42073df8a13d7ce72c5634
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083532"
---
# <a name="compiler-warning-level-1-c4258"></a>Kompilátor upozornění (úroveň 1) C4258

'variable': definice z for loop se ignoruje; definice z nadřazeného oboru se používá"

V části [/Ze](../../build/reference/za-ze-disable-language-extensions.md) a [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md), proměnné definované v [pro](../../cpp/for-statement-cpp.md) smyčky dostanou mimo rozsah po **pro** skončení smyčky. K tomuto upozornění dochází, pokud proměnnou se stejným názvem jako proměnná smyčky, ale definovanou v nadřazeném smyčce se používá znovu v oboru obsahující **pro** smyčky. Příklad:

```
// C4258.cpp
// compile with: /Zc:forScope /W1
int main()
{
   int i;
   {
      for (int i =0; i < 1; i++)
         ;
      i = 20;   // C4258 i (in for loop) has gone out of scope
   }
}
```