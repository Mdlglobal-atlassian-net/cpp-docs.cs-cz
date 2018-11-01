---
title: Kompilátor upozornění (úroveň 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: b4d3356522faacfc343c33908b64597387fbe51c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521068"
---
# <a name="compiler-warning-level-1-c4572"></a>Kompilátor upozornění (úroveň 1) C4572

Atribut [ParamArray] je zastaralá pod parametrem/CLR, použijte tři tečky. místo toho

Zastaralý styl pro zadání Proměnný seznam argumentů byl použit. Při kompilaci pro modul CLR, použijte syntaxi tlačítko se třemi tečkami místo <xref:System.ParamArrayAttribute>. Další informace najdete v tématu [seznamy argumentů proměnných (...) (C + +/ CLI) ](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4572.

```
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```