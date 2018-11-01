---
title: Chyba kompilátoru C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: c665c4ed82fefaf0ee724defb8c205f86fc06dd0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435305"
---
# <a name="compiler-error-c2562"></a>Chyba kompilátoru C2562

'identifier': "void" funkce vrací hodnotu

Funkce je deklarována jako `void` , ale vrací hodnotu.

Tuto chybu může způsobovat prototypu nesprávná funkce.

Tato chyba může být stanovena, pokud zadáte návratový typ v deklaraci funkce.

Následující ukázka generuje C2562:

```
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```