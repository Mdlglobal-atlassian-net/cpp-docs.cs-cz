---
title: Upozornění kompilátoru (úroveň 4) C4213
ms.date: 11/04/2016
f1_keywords:
- C4213
helpviewer_keywords:
- C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
ms.openlocfilehash: 318b228a1af17543062943a336ccccd06bc6ae46
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541816"
---
# <a name="compiler-warning-level-4-c4213"></a>Upozornění kompilátoru (úroveň 4) C4213

používá se nestandardní rozšíření: přetypování na l-hodnotu.

S výchozími rozšířeními Microsoft (/ze) můžete použít přetypování na levé straně příkazu přiřazení.

## <a name="example"></a>Příklad

```c
// C4213.c
// compile with: /W4
void *a;
void f()
{
   int   i[3];
   a = &i;
   *(( int * )a )++ = 3;  // C4213
}

int main()
{
}
```

Tato přetypování nejsou v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) platná.