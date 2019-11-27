---
title: Upozornění kompilátoru (úroveň 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: e15140bd2f0983bde64c89a054fd733d1ab902ac
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541868"
---
# <a name="compiler-warning-level-4-c4208"></a>Upozornění kompilátoru (úroveň 4) C4208

používá se nestandardní rozšíření: delete [exp]-exp vyhodnoceno, ale ignorováno.

Pomocí rozšíření Microsoft Extensions (/ze) můžete odstranit pole pomocí [operátoru delete](../../cpp/delete-operator-cpp.md)v závorkách. Hodnota se ignoruje.

```cpp
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

Tyto hodnoty jsou neplatné v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).