---
title: Upozornění (úroveň 1) C4229 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4229
dev_langs:
- C++
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e485f4e49859a12b17eac5dd378853bb3795bd7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064039"
---
# <a name="compiler-warning-level-1-c4229"></a>Kompilátor upozornění (úroveň 1) C4229

anachronismus: Modifikátory pro data se ignorují.

Pomocí modifikátoru Microsoft, například `__cdecl` na datové deklarace je zastaralý postup.

## <a name="example"></a>Příklad

```
// C4229.cpp
// compile with: /W1 /LD
int __cdecl counter;   // C4229 cdecl ignored
```