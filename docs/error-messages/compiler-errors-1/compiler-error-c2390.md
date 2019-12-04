---
title: Chyba kompilátoru C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 515e2e151d27dd2eb84fc1dc71b9197b36b14cbb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745041"
---
# <a name="compiler-error-c2390"></a>Chyba kompilátoru C2390

' identifier ': nesprávná třída úložiště ' specifikátor '

Třída úložiště není platná pro identifikátor globálního rozsahu. Výchozí třída úložiště se používá místo neplatné třídy.

Možná řešení:

- Pokud je identifikátor funkce, deklarujte ji pomocí `extern` Storage.

- Pokud je identifikátor formálním parametrem nebo místní proměnnou, deklarujte ji pomocí automatického úložiště.

- Pokud je identifikátor globální proměnnou, deklarujte ji bez třídy úložiště (automatické úložiště).

## <a name="example"></a>Příklad

- Následující ukázka generuje C2390:

```cpp
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```
