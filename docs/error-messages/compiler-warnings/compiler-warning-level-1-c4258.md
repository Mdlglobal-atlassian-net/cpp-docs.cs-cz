---
title: Upozornění kompilátoru (úroveň 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: 198873792743a9ccdee94d44e2a0599348589ee6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163203"
---
# <a name="compiler-warning-level-1-c4258"></a>Upozornění kompilátoru (úroveň 1) C4258

' Variable ': definice z smyčky for je ignorována; použije se definice z nadřazeného oboru.

V části [/ze](../../build/reference/za-ze-disable-language-extensions.md) a [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)proměnné definované ve smyčce [for](../../cpp/for-statement-cpp.md) jdou mimo rozsah po ukončení smyčky **for** . K tomuto upozornění dochází, pokud je proměnná se stejným názvem jako proměnná smyčky, ale definovaná v ohraničující smyčce, je znovu použita v oboru obsahujícím smyčku **for** . Příklad:

```cpp
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
