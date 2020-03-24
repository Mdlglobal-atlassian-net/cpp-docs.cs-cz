---
title: Upozornění kompilátoru (úroveň 4) C4204
ms.date: 11/04/2016
f1_keywords:
- C4204
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
ms.openlocfilehash: 45ed4817dbf2c7ecd63cd0c669d6e1cf768184bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174047"
---
# <a name="compiler-warning-level-4-c4204"></a>Upozornění kompilátoru (úroveň 4) C4204

používá se nestandardní rozšíření: nekonstantní agregační inicializátor

Pomocí rozšíření Microsoft Extensions (/ze) můžete inicializovat agregované typy (pole, struktury, sjednocení a třídy) s hodnotami, které nejsou konstanty.

## <a name="example"></a>Příklad

```c
// C4204.c
// compile with: /W4
int func1()
{
   return 0;
}
struct S1
{
   int i;
};

int main()
{
   struct S1 s1 = { func1() };   // C4204
   return s1.i;
}
```

Taková inicializace nejsou v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) platná.
