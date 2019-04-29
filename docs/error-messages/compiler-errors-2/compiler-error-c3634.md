---
title: Chyba kompilátoru C3634
ms.date: 11/04/2016
f1_keywords:
- C3634
helpviewer_keywords:
- C3634
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
ms.openlocfilehash: 2acd76fee5e7ca309991e639044a45ea83ed112b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385664"
---
# <a name="compiler-error-c3634"></a>Chyba kompilátoru C3634

'function': nelze definovat abstraktní metodu třídy spravované nebo WinRTclass

Abstraktní metody mohou být deklarovány ve spravované nebo třída WinRT, ale nelze definovat.

## <a name="example"></a>Příklad

Následující ukázka generuje C3634:

```
// C3634.cpp
// compile with: /clr
ref class C {
   virtual void f() = 0;
};

void C::f() {   // C3634 - don't define managed class' pure virtual method
}
```
