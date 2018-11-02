---
title: Chyba kompilátoru C2433
ms.date: 11/04/2016
f1_keywords:
- C2433
helpviewer_keywords:
- C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
ms.openlocfilehash: 8a98fcf7570605694569b7ae466ae0a3c7cf14bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512049"
---
# <a name="compiler-error-c2433"></a>Chyba kompilátoru C2433

'identifier': není povolené pro deklarace dat. modifikátor

`friend`, `virtual`, A `inline` Modifikátory nelze použít pro deklarace na data.

## <a name="example"></a>Příklad

Následující ukázka generuje C2433.

```
// C2433.cpp
class C{};

int main() {
   inline C c;   // C2433
}
```