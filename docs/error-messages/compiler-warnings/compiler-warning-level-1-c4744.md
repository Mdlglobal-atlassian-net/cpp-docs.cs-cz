---
title: Upozornění kompilátoru (úroveň 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f932b1bcdf011678d4f85e0edf1e116a954b59fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367381"
---
# <a name="compiler-warning-level-1-c4744"></a>Upozornění kompilátoru (úroveň 1) C4744

'var' má jiný typ v 'file1' a 'file2': 'type1' a 'type2'

Externí proměnná odkazovaná nebo definovaná ve dvou souborech má v těchto souborech různé typy.  Chcete-li vyřešit, buď změnit definice typu stejné nebo změnit název proměnné v jednom ze souborů.

C4744 je emitován pouze v případě, že jsou soubory kompilovány s /GL.  Další informace naleznete v tématu [/GL (Optimalizace celého programu).](../../build/reference/gl-whole-program-optimization.md)

> [!NOTE]
> C4744 se obvykle vyskytuje v souborech Jazyka C (nikoli v jazyce C++), protože v jazyce C++ je název proměnné ozdoben informacemi o typu.  Když se ukázka (níže) zkompiluje jako C++, zobrazí se chyba propojovacího programu LNK2019.

## <a name="example"></a>Příklad

Tato ukázka obsahuje první definici.

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4744.

```c
// C4744b.c
// compile with: C4744.c /GL /W1
// C4744 expected
#include <stdio.h>

extern unsigned global;

main()
{
    printf_s("%d\n", global);
}
```
