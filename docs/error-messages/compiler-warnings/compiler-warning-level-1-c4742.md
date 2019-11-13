---
title: Upozornění kompilátoru (úroveň 1) C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: 11663a9b8672e2f91feb59e275181dbe645484e9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051313"
---
# <a name="compiler-warning-level-1-c4742"></a>Upozornění kompilátoru (úroveň 1) C4742

klíčové slovo var má jiné zarovnání v Soubor1 a soubor2: číslo a číslo.

Externí proměnná, na kterou bylo odkazováno nebo definováno ve dvou souborech, má v těchto souborech jiné zarovnání. Toto upozornění je vygenerováno, pokud kompilátor zjistí, že `__alignof` pro proměnnou v Soubor1 se v poli *Soubor1* liší od `__alignof` pro proměnnou v *soubor2*. To může být způsobeno použitím nekompatibilních typů při deklaraci proměnné v různých souborech nebo pomocí nevyhovující `#pragma pack` v různých souborech.

Chcete-li vyřešit toto upozornění, použijte stejnou definici typu nebo použijte jiné názvy proměnných.

Další informace najdete v tématu operátor [Pack](../../preprocessor/pack.md) a [__alignof](../../cpp/alignof-operator.md).

## <a name="example"></a>Příklad

Toto je první soubor, který definuje typ.

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4742.

```c
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