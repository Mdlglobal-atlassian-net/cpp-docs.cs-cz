---
title: Chyba kompilátoru C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 39f779ee846cf4f328f9c7af59ae394d97d7a3ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744729"
---
# <a name="compiler-error-c2422"></a>Chyba kompilátoru C2422

neplatné přepsání segmentu v operandu

Kód vloženého sestavení nesprávně používá operátor přepisu segmentu (dvojtečka) na operandu.  Mezi možné příčiny patří:

- Registr před operátorem není registr segmentu.

- Registr před operátorem není jediný registr segmentu v operandu.

- Operátor přepsání segmentu se zobrazí v operátoru dereference (hranaté závorky).

- Výraz za operátorem přepsání segmentu není okamžitý operand nebo operand paměti.

Následující ukázka generuje C2422:

```cpp
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```
