---
title: Chyba kompilátoru C2422 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17421f2d4a7823c0e2fbb34a54a7c562223c798c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047028"
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