---
title: Chyba kompilátoru C2228
ms.date: 11/04/2016
f1_keywords:
- C2228
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
ms.openlocfilehash: 56eed6aeff5a955253a440d5931d66118f4604e0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759279"
---
# <a name="compiler-error-c2228"></a>Chyba kompilátoru C2228

vlevo od '. identifier ' musí mít třídu/strukturu/sjednocení.

Operand vlevo od tečky (.) není třída, struktura nebo sjednocení.

Následující ukázka generuje C2228:

```cpp
// C2228.cpp
int i;
struct S {
public:
    int member;
} s, *ps = &s;

int main() {
   i.member = 0;   // C2228 i is not a class type
   ps.member = 0;  // C2228 ps is a pointer to a structure

   s.member = 0;   // s is a structure type
   ps->member = 0; // ps points to a structure S
}
```

Tato chyba se zobrazí také v případě, že při použití spravovaných rozšíření použijete nesprávnou syntaxi. V jiných jazycích sady Visual Studio můžete použít operátor tečka pro přístup ke členu spravované třídy, ukazatel na objekt v C++ znamená, že je nutné použít operátor-> pro přístup ke členu:

Chybné: `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`

Right: `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`
