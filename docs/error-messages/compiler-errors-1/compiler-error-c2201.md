---
title: Chyba kompilátoru C2201
ms.date: 11/04/2016
f1_keywords:
- C2201
helpviewer_keywords:
- C2201
ms.assetid: ed927659-6e9c-447d-9963-19969ae1e957
ms.openlocfilehash: b011c5027af6c0561010c6d11d3efd07234549f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621596"
---
# <a name="compiler-error-c2201"></a>Chyba kompilátoru C2201

'identifier': musí mít externí propojení dalo Importovat/exportovat

Exportovaný identifikátor je `static`.

Následující ukázka generuje C2286:

```
// C2201.cpp
// compile with: /c
__declspec(dllexport) static void func() {}   // C2201 func() is static
__declspec(dllexport) void func2() {}   // OK
```

## <a name="see-also"></a>Viz také

[Typy propojení](../../cpp/types-of-linkage.md)