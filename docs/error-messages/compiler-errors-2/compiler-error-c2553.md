---
title: Chyba kompilátoru C2553 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2553
dev_langs:
- C++
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38fb61b7281dd0371c546fd7b7bc960232cf2e00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043986"
---
# <a name="compiler-error-c2553"></a>Chyba kompilátoru C2553

'base_function': přepisující virtuální funkce vrátí typ se liší od "override_function.

Funkce v odvozené třídě se pokusil přepsat virtuální funkce v základní třídě, ale funkce odvozené třídy neměl vracet hodnotu stejného typu jako funkci základní třídy.  Podpis funkce přepsání musí odpovídat signatuře funkce přepsání.

Následující ukázka generuje C2553:

```
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```