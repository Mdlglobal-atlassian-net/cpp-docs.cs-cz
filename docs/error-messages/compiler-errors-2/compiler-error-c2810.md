---
title: Chyba kompilátoru C2810
ms.date: 11/04/2016
f1_keywords:
- C2810
helpviewer_keywords:
- C2810
ms.assetid: f63e8f24-d7f6-42ac-904f-72ff49592ba6
ms.openlocfilehash: 171b9d1b3b09b793c55756500cafed1db7eb9d99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627484"
---
# <a name="compiler-error-c2810"></a>Chyba kompilátoru C2810

'rozhraní': rozhraní může dědit jedině z jiného rozhraní

[Rozhraní](../../cpp/interface.md) může dědit jedině z jiného rozhraní a nemůže dědit z třídy nebo struktury.

Následující ukázka generuje C2810:

```
// C2810.cpp
#include <unknwn.h>
class CBase1 {
public:
  HRESULT mf1();
  int  m_i;
};

[object, uuid="40719E20-EF37-11D1-978D-0000F805D73B"]
__interface IDerived : public CBase1 {  // C2810
// try the following line instead
// __interface IDerived {
   HRESULT mf2(void *a);
};

struct CBase2 {
   HRESULT mf1(int a, char *b);
   HRESULT mf2();
};
```