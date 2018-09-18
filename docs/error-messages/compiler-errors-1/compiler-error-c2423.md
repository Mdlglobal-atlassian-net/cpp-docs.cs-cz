---
title: Chyba kompilátoru C2423 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2423
dev_langs:
- C++
helpviewer_keywords:
- C2423
ms.assetid: 8797fb8b-b58b-4add-b6e6-2a9a3cd9084d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e7a974a83935dbbcc9cd78bcc9280c9f0fbc2a4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029309"
---
# <a name="compiler-error-c2423"></a>Chyba kompilátoru C2423

'number': Neplatné měřítko

Vložený kód sestavení používá číslo než 1, 2, 4 nebo 8 škálování registru.

Následující ukázka generuje C2423:

```
// C2423.cpp
// processor: x86
int main() {
   _asm {
      lea EAX, [EAX*3]   // C2423
      lea EAX, [EAX+EAX*2]   // OK
   }
}
```