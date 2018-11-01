---
title: Chyba kompilátoru C3254
ms.date: 11/04/2016
f1_keywords:
- C3254
helpviewer_keywords:
- C3254
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
ms.openlocfilehash: 7e051c6c44d3b85f6f3faaf5380ecf54cba5d73c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470665"
---
# <a name="compiler-error-c3254"></a>Chyba kompilátoru C3254

'explicitní přepsání': třída obsahuje explicitní přepsání 'override', ale není odvozen z rozhraní, která obsahuje deklaraci funkce

Pokud jste [explicitně přepsat](../../cpp/explicit-overrides-cpp.md) metodu, třídu, která obsahuje přepsání musí být odvozen, přímo nebo nepřímo, z typu, který obsahuje funkce jsou přepisování.

Následující ukázka generuje C3254:

```
// C3254.cpp
__interface I
{
   void f();
};

__interface I1 : I
{
};

struct A /* : I1 */
{
   void I1::f()
   {   // C3254, uncomment : I1 to resolve this C3254
   }
};

int main()
{
}
```