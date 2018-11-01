---
title: Chyba kompilátoru C2673
ms.date: 11/04/2016
f1_keywords:
- C2673
helpviewer_keywords:
- C2673
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
ms.openlocfilehash: 8a544b6d96089195d7d28f9a62b091b4f1cfc537
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587639"
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