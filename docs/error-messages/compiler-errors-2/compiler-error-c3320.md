---
title: Chyba kompilátoru C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 622e7366dda4cd6693d9b6128855fa0966e07952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222476"
---
# <a name="compiler-error-c3320"></a>Chyba kompilátoru C3320

'type': typ nemůže mít stejný název jako vlastnost 'name' module

Exportované uživatelem definovaný typ (UDT), které by mohly být struktury, třídy, výčtu nebo sjednocení, nemůže mít stejný název jako parametr předaný [modulu](../../windows/module-cpp.md) vlastnost name atributu.

## <a name="example"></a>Příklad

Následující ukázka generuje C3320:

```cpp
// C3320.cpp
#include "unknwn.h"
[module(name="xx")];

[export] struct xx {   // C3320
// Try the following line instead
// [export] struct yy {
   int i;
};
```