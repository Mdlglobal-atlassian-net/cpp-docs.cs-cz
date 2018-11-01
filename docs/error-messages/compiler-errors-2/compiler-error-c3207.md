---
title: Chyba kompilátoru C3207
ms.date: 11/04/2016
f1_keywords:
- C3207
helpviewer_keywords:
- C3207
ms.assetid: 4a28b976-142a-4cff-aa2f-480b892c50ca
ms.openlocfilehash: 51873e089499e42f4ddeb97c95e3f18416df447c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515489"
---
# <a name="compiler-error-c3207"></a>Chyba kompilátoru C3207

'function': Neplatný argument šablony pro argument, očekávala se šablony tříd

Funkce šablon je definován, aby přijímaly šablonu argumentu šablony. Však byl předán argument typu šablony.

Následující ukázka generuje C3207:

```
// C3207.cpp
template <template <class T> class TT>
void f(){}

template <class T>
struct S
{
};

void f1()
{
   f<S<int> >();   // C3207
   // try the following line instead
   // f<S>();
}
```