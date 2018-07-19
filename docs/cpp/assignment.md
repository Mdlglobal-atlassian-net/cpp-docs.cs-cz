---
title: Přiřazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27e78f7429c4d2a0f83ff7184460eb2ae69df129
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960983"
---
# <a name="assignment"></a>Přiřazení
Operátor přiřazení (**=**) je, přesněji řečeno, binární operátor. Jeho deklarace je stejná jako u ostatních binárních operátorů, s následujícími výjimkami:  
  
-   Musí to být funkce nestatického členu. Ne **operátoru =** lze deklarovat jako nečlenskou funkci.  
  
-   Není zděděn z odvozené třídy.  
  
-   Výchozí **operátoru =** funkce můžete generovaný kompilátorem pro typy tříd, pokud žádný neexistuje.  
  
 Následující příklad ukazuje, jak deklarovat operátor přiřazení:  
  
```cpp 
// assignment.cpp  
class Point  
{  
public:  
   Point &operator=( Point & );  // Right side is the argument.  
   int _x, _y;  
};  
  
// Define assignment operator.  
Point &Point::operator=( Point &ptRHS )  
{  
   _x = ptRHS._x;  
   _y = ptRHS._y;  
  
   return *this;  // Assignment operator returns left side.  
}  
  
int main()  
{  
}  
```  
  
 Všimněte si, že zadaný argument představuje pravou stranu výrazu. Operátor vrací objekt pro zachování chování operátoru přiřazení, který po dokončení přiřazení vrací hodnotu levé strany. To umožňuje psaní příkazů, jako je například:  
  
```cpp 
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>Viz také  
 [Přetížení operátoru](../cpp/operator-overloading.md)