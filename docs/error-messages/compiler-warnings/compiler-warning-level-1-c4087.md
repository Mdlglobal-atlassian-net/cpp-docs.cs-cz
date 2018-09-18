---
title: Upozornění (úroveň 1) C4087 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4087
dev_langs:
- C++
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4be252163d9c45d2404629bcf9e2d82e3225a84a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086288"
---
# <a name="compiler-warning-level-1-c4087"></a>Kompilátor upozornění (úroveň 1) C4087

'function': deklarované se seznamem parametrů void.

Deklarace funkce nemá žádné formální parametry, ale volání funkce má skutečných parametrů. Další parametry jsou předány podle konvence volání funkce.

Toto upozornění je pro kompilátor jazyka C.

## <a name="example"></a>Příklad

```
// C4087.c
// compile with: /W1
int f1( void ) {
}

int main() {
   f1( 10 );   // C4087
}
```