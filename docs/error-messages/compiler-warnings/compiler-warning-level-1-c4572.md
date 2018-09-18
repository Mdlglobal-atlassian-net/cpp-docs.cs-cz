---
title: Upozornění (úroveň 1) C4572 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4572
dev_langs:
- C++
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b87b3dd4264db9fd7ea3699f342358fa6d4d5aac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076837"
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