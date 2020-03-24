---
title: Chyba kompilátoru C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 0289d49ebbb0e30153beb6b0b2bc758bff5ef118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201302"
---
# <a name="compiler-error-c3320"></a>Chyba kompilátoru C3320

Typ: typ nemůže mít stejný název jako vlastnost Name modulu.

Exportovaný uživatelem definovaný typ (UDT), který může být struktura, třída, výčet nebo sjednocení, nemůže mít stejný název jako parametr předaný vlastnosti název atributu [Module](../../windows/module-cpp.md) .

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
