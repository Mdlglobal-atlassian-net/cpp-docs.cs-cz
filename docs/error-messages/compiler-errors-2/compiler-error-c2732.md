---
title: Chyba kompilátoru C2732 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 040fd73bcb69ef032d5c6150bb157337f34a2088
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079658"
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