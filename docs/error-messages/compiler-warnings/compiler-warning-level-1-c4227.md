---
title: Upozornění (úroveň 1) C4227 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4227
dev_langs:
- C++
helpviewer_keywords:
- C4227
ms.assetid: 78f98374-c00b-4000-aefa-1b1c67b4666b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fda3a31b228f16b27f4bdefd3131a0ddcb90f5b5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060851"
---
# <a name="compiler-warning-level-1-c4227"></a>Kompilátor upozornění (úroveň 1) C4227

anachronismus: kvalifikátory pro odkaz se ignorují.

Použití kvalifikátorů, jako je `const` nebo `volatile` s odkazy na C++ je zastaralý postup.

## <a name="example"></a>Příklad

```
// C4227.cpp
// compile with: /W1 /c
int j = 0;
int &const i = j;   // C4227
```