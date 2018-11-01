---
title: Chyba kompilátoru C2498
ms.date: 11/04/2016
f1_keywords:
- C2498
helpviewer_keywords:
- C2498
ms.assetid: 0839f12c-aaa4-4a02-bb33-7f072715dd14
ms.openlocfilehash: 1087dbb2297058f752e0a15776e4a7185e32a5c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462267"
---
# <a name="compiler-error-c2498"></a>Chyba kompilátoru C2498

'function': "novtable" může používat jedině pro definice nebo deklarace tříd

Tato chyba může být způsobena pomocí `__declspec(novtable)` s funkcí.

## <a name="example"></a>Příklad

Následující ukázka generuje C2498:

```
// C2498.cpp
// compile with: /c
void __declspec(novtable) f() {}   // C2498
class __declspec(novtable) A {};   // OK
```