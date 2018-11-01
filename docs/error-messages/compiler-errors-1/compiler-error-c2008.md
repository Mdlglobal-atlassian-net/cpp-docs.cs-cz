---
title: Chyba kompilátoru C2008
ms.date: 11/04/2016
f1_keywords:
- C2008
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
ms.openlocfilehash: 0bd9193d6e305a4b6c6851ef2524a68ecc056816
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565708"
---
# <a name="compiler-error-c2008"></a>Chyba kompilátoru C2008

'znak': neočekávalo se v definici makra

Znak, který se zobrazí okamžitě po názvu makra. Chcete-li chybu vyřešit, musí být mezeru po názvu makra.

Následující ukázka generuje C2008:

```
// C2008.cpp
#define TEST1"mytest1"    // C2008
```

Možná řešení:

```
// C2008b.cpp
// compile with: /c
#define TEST2 "mytest2"
```