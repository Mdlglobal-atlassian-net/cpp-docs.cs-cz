---
title: Chyba kompilátoru C3842
ms.date: 11/04/2016
f1_keywords:
- C3842
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
ms.openlocfilehash: a61a69aca53f7f8996d0261a57b749930ecc01cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385508"
---
# <a name="compiler-error-c3842"></a>Chyba kompilátoru C3842

'function': 'const' a 'volatile: kvalifikátory pro členské funkce WinRT nebo spravované typy nejsou podporovány.

[Const](../../cpp/const-cpp.md) a [volatile](../../cpp/volatile-cpp.md) členských funkcí třídy Windows Runtime nebo spravované typy se nepodporují.

Následující ukázka generuje C3842:

```
// C3842a.cpp
// compile with: /clr /c
public ref struct A {
   void f() const {}   // C3842
   void f() volatile {}   // C3842

   void f() {}
};
```