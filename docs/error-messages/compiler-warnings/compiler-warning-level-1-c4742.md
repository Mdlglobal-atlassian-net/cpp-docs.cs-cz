---
title: Kompilátor upozornění (úroveň 1) C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: 00ac67fec3aafa5a259b5222bd6bb8654210fa61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436359"
---
# <a name="compiler-warning-level-1-c4742"></a>Kompilátor upozornění (úroveň 1) C4742

'příkaz var' má jiné zarovnání v 'file1' a 'file2': číslo a číslo

Externí proměnné, odkazované nebo definované ve dvou souborech má jiné zarovnání v těchto souborech. Toto upozornění je vygenerován, když kompilátor zjistí, že `__alignof` pro proměnné v *file1* se liší od `__alignof` pro proměnné v *file2*. To může být způsobeno pomocí nekompatibilních typů při deklarování proměnné v různých souborů nebo pomocí neodpovídající `#pragma pack` v různých souborech.

Pokud chcete vyřešit toto upozornění, použijte stejné definice typu nebo použít jiné názvy pro proměnné.

Další informace najdete v tématu [pack](../../preprocessor/pack.md) a [__alignof – operátor](../../cpp/alignof-operator.md).

## <a name="example"></a>Příklad

Toto je první soubor, který definuje typ.

```
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4742.

```
// C4742b.c
// compile with: C4742a.c /W1 /GL
// C4742 expected
extern struct X {
   int a;
} global;

int main() {
   global.a = 0;
}
```