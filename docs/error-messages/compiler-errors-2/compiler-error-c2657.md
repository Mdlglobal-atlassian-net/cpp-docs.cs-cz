---
title: Chyba kompilátoru C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: 4e2816092b3c0c210ae2c544e9bf9a823a9c5d18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661133"
---
# <a name="compiler-error-c2657"></a>Chyba kompilátoru C2657

' třída:: * "na začátku příkazu (Nezapomněli jste zadat typ?)

Na řádku začal s identifikátorem pointer-to-member.

Tuto chybu může způsobovat chybějící specifikátor typu v deklaraci ukazatele na člen.

Následující ukázka generuje C2657:

```
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```