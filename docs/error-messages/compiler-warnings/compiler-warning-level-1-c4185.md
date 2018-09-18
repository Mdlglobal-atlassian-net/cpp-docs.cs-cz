---
title: Upozornění (úroveň 1) C4185 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4185
dev_langs:
- C++
helpviewer_keywords:
- C4185
ms.assetid: 37e7063a-35b1-4e05-ae31-e811dced02b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acd6750eff911f52cdf656aa4e9a54cfe084ff00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027372"
---
# <a name="compiler-warning-level-1-c4185"></a>Kompilátor upozornění (úroveň 1) C4185

ignoruje se neznámý #import atribut 'attribute'

Atribut není platný atribut `#import`. Ignorováno.

## <a name="example"></a>Příklad

```
// C4185.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_such_attribute   // C4185
```