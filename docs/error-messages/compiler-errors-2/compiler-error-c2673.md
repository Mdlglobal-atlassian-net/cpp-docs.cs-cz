---
title: Chyba kompilátoru C2673 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2673
dev_langs:
- C++
helpviewer_keywords:
- C2673
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 942ad581c4b272078eabfe225e7fdab2245d0ad2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108512"
---
# <a name="compiler-error-c2673"></a>Chyba kompilátoru C2673

'function': globální funkce nemají ukazatele "this"

Globální funkce se pokusili získat přístup `this`.

Následující ukázka generuje C2673:

```
// C2673.cpp
int main() {
   this = 0;   // C2673
}
```