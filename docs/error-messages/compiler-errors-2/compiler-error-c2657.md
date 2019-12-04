---
title: Chyba kompilátoru C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: e060c2b9a38866a898a3c5ada9e595464050877e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756094"
---
# <a name="compiler-error-c2657"></a>Chyba kompilátoru C2657

' class::* ' nalezen na začátku příkazu (Nezapomněli jste zadat typ?)

Řádek začal identifikátorem ukazatele na člen.

Tato chyba může být způsobena chybějícím specifikátorem typu v deklaraci ukazatele na člena.

Následující ukázka generuje C2657:

```cpp
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```
