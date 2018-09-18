---
title: Upozornění (úroveň 1) C4606 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4606
dev_langs:
- C++
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcdaba046f495dc3a29a7c9228edc561674f568f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035991"
---
# <a name="compiler-warning-level-1-c4606"></a>Kompilátor upozornění (úroveň 1) C4606

\#– Direktiva pragma upozornění: ignoruje; warning_number Upozornění analýzy kódu nejsou přidružená k úrovním upozornění

Pro upozornění analýzy kódu, pouze `error`, `once`, a `default` jsou podporovány [upozornění](../../preprocessor/warning.md) direktivy pragma.

## <a name="example"></a>Příklad

Následující ukázka generuje C4606.

```
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```