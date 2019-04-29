---
title: Chyba kompilátoru C2422
ms.date: 11/04/2016
f1_keywords:
- C2422
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
ms.openlocfilehash: 524eeadb6cf066d3eba3a7e88c45a9e2b993c0ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402882"
---
# <a name="compiler-error-c2422"></a>Chyba kompilátoru C2422

Neplatné přepsání segmentu "operand"

Vložený kód sestavení nesprávně používá operátor přepsání segmentu (dvojtečka) na operand.  Mezi možné příčiny patří:

- Registr předcházející operátor, který není registr segmentu.

- Registr předcházející operátor, který není pouze registrace segment v operandu.

- Operátor přepsání segmentu se objeví v rámci operátor dereference (závorek).

- Výraz, který následuje operátor přepsání segmentu se přímý operand nebo operand paměti.

Následující ukázka generuje C2422:

```
// C2422.cpp
// processor: x86
int main() {
   _asm {
      mov AX, [BX:ES]   // C2422
      mov AX, ES   // OK
   }
}
```