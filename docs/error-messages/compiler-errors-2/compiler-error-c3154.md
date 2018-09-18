---
title: Chyba kompilátoru C3154 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3154
dev_langs:
- C++
helpviewer_keywords:
- C3154
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92a888020e306e762ffb242cb92636cc14680bf5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074653"
---
# <a name="compiler-error-c3154"></a>Chyba kompilátoru C3154

Byl očekáván ',' před třemi tečkami. Čárkou oddělený tlačítko se třemi tečkami není podporováno ve funkcích pole parametrů.

Funkce argumentů s proměnnou délkou není deklarovaná správně.

Další informace najdete v tématu [seznamy argumentů proměnných (...) (C + +/ CLI) ](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3154.

```
// C3154.cpp
// compile with: /clr
ref struct R {
   void Func(int ... array<int> ^);   // C3154
   void Func2(int i, ... array<int> ^){}   // OK
   void Func3(array<int> ^){}   // OK
   void Func4(... array<int> ^){}   // OK
};

int main() {
   R ^ r = gcnew R;
   r->Func4(1,2,3);
}
```