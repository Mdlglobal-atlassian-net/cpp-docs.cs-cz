---
title: Compiler Error C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 89f6ebb02326413e8dca67d333e555321da4e645
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393633"
---
# <a name="compiler-error-c2390"></a>Compiler Error C2390

'identifier': nesprávná třída úložiště "specifikátor"

Třída úložiště není platný pro identifikátor globální obor. Místo neplatná třída se používá výchozí třídou úložiště.

Možná řešení:

- Pokud identifikátor je funkce, deklarujte ho s `extern` úložiště.

- Pokud identifikátor je formální parametr nebo lokální proměnné, ji deklarujte pomocí automatického úložiště.

- Identifikátor je globální proměnné, deklarujte ho pomocí bez třídy úložiště (automatické úložiště).

## <a name="example"></a>Příklad

- Následující ukázka generuje C2390:

```
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```