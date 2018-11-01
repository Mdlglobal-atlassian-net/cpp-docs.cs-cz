---
title: Chyba kompilátoru C2153
ms.date: 11/04/2016
f1_keywords:
- C2153
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
ms.openlocfilehash: eeb7da509ffb1b8c408763c79d471586eb94f383
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605930"
---
# <a name="compiler-error-c2153"></a>Chyba kompilátoru C2153

hexadecimální konstanty musí mít alespoň jednu číslici hex

Šestnáctkové konstanty 0 x, 0 X a \x nejsou platné. Musí splňovat aspoň jednu číslici hex x nebo X.

Následující ukázka generuje C2153:

```
// C2153.cpp
int main() {
   int a= 0x;    // C2153
   int b= 0xA;   // OK
}
```