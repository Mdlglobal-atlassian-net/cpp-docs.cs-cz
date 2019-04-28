---
title: Chyba kompilátoru C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: a00ac997f73175eeab08a0132128e48e8fc58feb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338893"
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