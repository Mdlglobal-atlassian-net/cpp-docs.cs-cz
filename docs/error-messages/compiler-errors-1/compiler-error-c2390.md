---
title: Chyba kompilátoru C2390 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2390
dev_langs:
- C++
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5de5a9af8f8aa04219f0a7d61162336745fd4bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098209"
---
# <a name="compiler-error-c2390"></a>Chyba kompilátoru C2390

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