---
title: Chyba kompilátoru C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: a00ac997f73175eeab08a0132128e48e8fc58feb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498186"
---
# <a name="compiler-error-c2464"></a>Chyba kompilátoru C2464

'identifier': nelze použít "nové" k přidělení odkazu

Identifikátor odkazu byl přidělený `new` operátor. Odkazy nejsou objekty paměti, takže `new` nelze vrací ukazatel na ně. Pomocí syntaxe standardní deklarace proměnné můžete deklarovat odkaz.

Následující ukázka generuje C2464:

```
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```