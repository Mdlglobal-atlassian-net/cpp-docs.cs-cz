---
title: Upozornění kompilátoru (úroveň 4) C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: fb4cead9367c5ef69627f607c521f480ad94271f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991049"
---
# <a name="compiler-warning-level-4-c4366"></a>Upozornění kompilátoru (úroveň 4) C4366

Výsledek unárního operátoru ' operator ' nemůže být zarovnaný

Pokud by byl člen struktury někdy zarovnaný z důvodu balení, kompilátor zobrazí upozornění, pokud je adresa tohoto člena přiřazena k zarovnaný ukazateli. Ve výchozím nastavení jsou všechny ukazatele zarovnány.

Chcete-li vyřešit C4366, buď změňte zarovnání struktury, nebo deklarujte ukazatel pomocí klíčového slova [__unaligned](../../cpp/unaligned.md) .

Další informace najdete v tématu __unaligned a [Pack](../../preprocessor/pack.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4366.

```cpp
// C4366.cpp
// compile with: /W4 /c
// processor: IPF x64
#pragma pack(1)
struct X {
   short s1;
   int s2;
};

int main() {
   X x;
   short * ps1 = &x.s1;   // OK
   int * ps2 = &x.s2;   // C4366
}
```
