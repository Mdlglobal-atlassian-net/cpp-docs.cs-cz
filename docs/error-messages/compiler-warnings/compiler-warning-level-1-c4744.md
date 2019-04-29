---
title: Kompilátor upozornění (úroveň 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: 2118a32af8b99d35c1e1a6691561391ec5d2b8cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385417"
---
# <a name="compiler-warning-level-1-c4744"></a>Kompilátor upozornění (úroveň 1) C4744

'příkaz var' má jiný typ v 'file1' a 'file2': 'type1' a 'type2'

Externí proměnné odkazovat nebo definované ve dvou souborech má různé typy v těchto souborech.  Pokud chcete vyřešit, buď nastavte definice typu stejné nebo změnit název proměnné v jeden ze souborů.

C4744 je vygenerován jenom v případě, že soubory jsou zkompilovány s možností/GL.  Další informace najdete v tématu [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
>  C4744 se obvykle dochází v souborech jazyka C (C++ není), protože v jazyce C++ je upravený název proměnné s informací o typu.  Po ukázka (níže) se zkompiluje jako C++ získáte LNK2019 přiřazena chyba linkeru.

## <a name="example"></a>Příklad

Tato ukázka obsahuje první definice.

```
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4744.

```
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