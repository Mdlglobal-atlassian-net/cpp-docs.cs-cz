---
title: Upozornění kompilátoru (úroveň 1) C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: af97c72f496177d2e94cf18f9685ac33c5e62404
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185656"
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
