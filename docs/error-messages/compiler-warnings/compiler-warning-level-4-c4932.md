---
title: Upozornění (úroveň 4) C4932 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4932
dev_langs:
- C++
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c9143406fc4b52d50b5dc68215fa796f5100fb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053918"
---
# <a name="compiler-warning-level-4-c4932"></a>Kompilátor upozornění (úroveň 4) C4932

__identifier(Identifier) a \__identifier(identifier) jsou

Kompilátor nedokáže rozlišit **_finally** a `__finally` nebo `__try` a **_try** jako parametr předaný do [__identifier](../../windows/identifier-cpp-cli.md). By se neměly pokoušet použít je jako identifikátory ve stejném programu, jinak dojde v [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) chyby.

Následující ukázka generuje C4932:

```
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```