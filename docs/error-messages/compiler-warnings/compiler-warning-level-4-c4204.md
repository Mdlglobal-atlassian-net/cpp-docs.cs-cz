---
title: Kompilátor upozornění (úroveň 4) C4204
ms.date: 11/04/2016
f1_keywords:
- C4204
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
ms.openlocfilehash: e16cb9fb59ee6ec24bb9b68dad1be9432d9eee3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401238"
---
# <a name="compiler-warning-level-4-c4204"></a>Kompilátor upozornění (úroveň 4) C4204

používá se nestandardní rozšíření: nekonstantní agregační inicializátor

S rozšířeními společnosti Microsoft (/Ze) můžete inicializovat agregované typy (pole, struktury, sjednocení a tříd) nahraďte hodnotami, které nejsou konstanty.

## <a name="example"></a>Příklad

```
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

Tyto inicializace jsou neplatné pod kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).