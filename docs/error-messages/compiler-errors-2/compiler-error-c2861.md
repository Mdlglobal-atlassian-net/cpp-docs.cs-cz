---
title: Chyba kompilátoru C2861
ms.date: 11/04/2016
f1_keywords:
- C2861
helpviewer_keywords:
- C2861
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
ms.openlocfilehash: bb61272b5a8d94a26096bd05260de331e853bf0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329072"
---
# <a name="compiler-error-c2861"></a>Chyba kompilátoru C2861

'název funkce': členská funkce rozhraní nemůže být definovaná.

Kompilátor zjistil – klíčové slovo interface nebo odvodit struktura jako rozhraní, ale pak najít člen definici funkce.  Rozhraní nemůže obsahovat definice členské funkce.

## <a name="example"></a>Příklad

Následující ukázka generuje C2861:

```
// C2861.cpp
// compile with: /c
#include <objbase.h>   // required for IUnknown definition
[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IMyInterface : IUnknown {
   HRESULT mf(int a);
};

HRESULT IMyInterface::mf(int a) {}   // C2861
```