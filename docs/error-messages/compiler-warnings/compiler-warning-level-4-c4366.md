---
title: Upozornění (úroveň 4) C4366 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4366
dev_langs:
- C++
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb24c65605857124edf608bec88f1399d9df607d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047041"
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