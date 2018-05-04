---
title: Přiřazení | Microsoft Docs
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
ms.openlocfilehash: 66fd08215c3849bf487578b28b1824afbec14c52
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="assignment"></a>Přiřazení
Operátor přiřazení (**=**) je přesněji řečeno, binární operátor. Jeho deklarace je stejná jako u ostatních binárních operátorů, s následujícími výjimkami:  
  
-   Musí to být funkce nestatického členu. Žádný `operator=` nelze deklarovat jako nečlenskou funkci.  
  
-   Není zděděn z odvozené třídy.  
  
-   Výchozí funkce `operator=`, pokud neexistuje, může být pro typy tříd vytvořena kompilátorem. (Další informace o výchozí `operator=` funkce, najdete v části [Memberwise přiřazení a inicializace](http://msdn.microsoft.com/en-us/94048213-8b49-4416-8069-b1b7a6f271f9).)  
  
 Následující příklad ukazuje, jak deklarovat operátor přiřazení:  
  
```  
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
  
```  
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>Viz také  
 [Přetížení operátoru](../cpp/operator-overloading.md)