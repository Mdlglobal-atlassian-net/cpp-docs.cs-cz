---
title: Chyba kompilátoru C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 820a620b7e4414123c56433f84536393834f6fd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208399"
---
# <a name="compiler-error-c2732"></a>Chyba kompilátoru C2732

Specifikace propojení konfliktu s předchozí specifikací pro 'function'

Funkce je už deklarovaná se specifikátorem rozdílné propojení.

Tato chyba může být způsobena podle zahrnout soubory s specifikátory rozdílné propojení.

Chcete-li tuto chybu vyřešit, změňte `extern` příkazy tak, aby vazby souhlas. Zejména nezalamují `#include` direktivy v `extern "C"` bloky.

## <a name="example"></a>Příklad

Následující ukázka generuje C2732:

```
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```