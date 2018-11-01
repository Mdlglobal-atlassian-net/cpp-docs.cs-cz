---
title: Chyba kompilátoru C3753
ms.date: 11/04/2016
f1_keywords:
- C3753
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
ms.openlocfilehash: b6b1e8c3241a778b29045e734fffebb663554e62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498368"
---
# <a name="compiler-error-c3753"></a>Chyba kompilátoru C3753

obecná vlastnost není povolená

Seznamy obecných parametrů může vyskytovat jenom u spravované třídy, struktury nebo funkce.

Další informace najdete v tématu [obecných typů](../../windows/generics-cpp-component-extensions.md) a [vlastnost](../../windows/property-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3753.

```
// C3753.cpp
// compile with: /clr /c
ref struct A {
   generic <typename T>
   property int i;   // C3753 error
};
```