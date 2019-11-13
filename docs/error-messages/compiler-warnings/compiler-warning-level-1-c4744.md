---
title: Upozornění kompilátoru (úroveň 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f6954ae7966edf200249bb5d10f0dfb011bcef22
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051551"
---
# <a name="compiler-warning-level-1-c4744"></a>Upozornění kompilátoru (úroveň 1) C4744

klíčové slovo var má odlišný typ v ' Soubor1 ' a ' soubor2 ': ' typ1 ' a ' typ2 '

Externí proměnná, na kterou se odkazuje nebo která je definovaná ve dvou souborech, má v těchto souborech různé typy.  Chcete-li je vyřešit, buď proveďte definice typu, nebo změňte název proměnné v jednom ze souborů.

C4744 se vydává jenom v případě, že jsou soubory kompilovány pomocí/GL.  Další informace naleznete v tématu [/GL (celá optimalizace programu)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
>  K C4744 obvykle dochází v souborech jazyka C++C (ne), C++ protože v názvu proměnné je upraveno pomocí informací o typu.  Když je ukázka (níže) zkompilována jako C++, zobrazí se chyba linkeru linkerů LNK2019.

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