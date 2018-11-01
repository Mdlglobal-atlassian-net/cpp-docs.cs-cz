---
title: Chyba kompilátoru C3733
ms.date: 11/04/2016
f1_keywords:
- C3733
helpviewer_keywords:
- C3733
ms.assetid: 0cc1a9fe-1400-4be3-b35a-16435cba7a5a
ms.openlocfilehash: 006f87691c6e0839115e2c02ab0d922aa95eaa93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501644"
---
# <a name="compiler-error-c3733"></a>Chyba kompilátoru C3733

'událost': nesprávná syntaxe pro zadání události COM; Nezapomněli jste zadat '__interface'?

Pro události COM byl použit chybnou syntaxi. Pokud chcete tuto chybu opravit, změnit typ události opravte syntaxi pro dosažení souladu s pravidly událostí modelu COM

Následující ukázka generuje C3733:

```
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[coclass, event_source(com), // change 'com' to 'native' to resolve
uuid("00000000-0000-0000-0000-000000000001")]
class A
{
   __event void func();   // C3733
};

int main()
{
}
```