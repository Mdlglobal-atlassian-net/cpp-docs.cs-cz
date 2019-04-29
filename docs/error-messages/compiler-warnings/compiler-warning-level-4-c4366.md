---
title: Kompilátor upozornění (úroveň 4) C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: 11fcb0070359201de39ca5f33c83d000e02f0835
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391553"
---
# <a name="compiler-warning-level-4-c4366"></a>Kompilátor upozornění (úroveň 4) C4366

Výsledek unárního operátoru 'operator' nemusí být zarovnaný.

Pokud člen struktury může být někdy nezarovnaných z důvodu zabalení, kompilátor se upozornit, pokud, že je přiřazena adresa člena zarovnané ukazatele. Ve výchozím nastavení je zarovnán všechny ukazatele.

Chcete-li vyřešit C4366, Změna zarovnání struktury nebo deklarovat ukazatel s [__unaligned](../../cpp/unaligned.md) – klíčové slovo.

Další informace najdete v tématu __unaligned a [pack](../../preprocessor/pack.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4366.

```
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