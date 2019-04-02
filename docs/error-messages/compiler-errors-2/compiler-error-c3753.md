---
title: Chyba kompilátoru C3753
ms.date: 11/04/2016
f1_keywords:
- C3753
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
ms.openlocfilehash: 7c9c078e72babc85dc7092b8d6414625e9c0db7b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771095"
---
# <a name="compiler-error-c3753"></a>Chyba kompilátoru C3753

obecná vlastnost není povolená

Seznamy obecných parametrů může vyskytovat jenom u spravované třídy, struktury nebo funkce.

Další informace najdete v tématu [obecných typů](../../extensions/generics-cpp-component-extensions.md) a [vlastnost](../../extensions/property-cpp-component-extensions.md).

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