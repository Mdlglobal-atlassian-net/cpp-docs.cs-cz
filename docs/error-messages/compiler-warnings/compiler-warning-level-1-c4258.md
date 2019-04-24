---
title: Kompilátor upozornění (úroveň 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: a3ce4c81a86920baddfc1b277df0236a96254be4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207393"
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