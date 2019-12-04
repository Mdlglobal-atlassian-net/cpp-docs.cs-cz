---
title: Chyba kompilátoru C3452
ms.date: 11/04/2016
f1_keywords:
- C3452
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
ms.openlocfilehash: c491217f01d8e78375401b54faa48d9db410ccad
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756718"
---
# <a name="compiler-error-c3452"></a>Chyba kompilátoru C3452

člen argumentu seznamu není konstanta.

Argument byl předán atributu, který očekával konstantu, hodnotu, která může být vyhodnocena v době kompilace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3452.

```cpp
// C3452.cpp
// compile with: /c
int i;
[module( name="mod", type=dll, custom={i} ) ];   // C3452
// try the following line instead
// [module( name="mod", type=dll, custom={"a"} ) ];
```
