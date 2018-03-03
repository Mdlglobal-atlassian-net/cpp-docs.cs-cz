---
title: "const_cast – operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- const_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79c4aa00038f2d4d7e5cc3d1c86d2e28c6d44229
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="constcast-operator"></a>const_cast – operátor
Odebere **const**, `volatile`, a **__unaligned** atributy z třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
const_cast <   
type-id  
 > (   
expression  
 )  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Ukazatel na libovolného typu objektu nebo ukazatele na člena lze explicitně převést na typ, který se shoduje s výjimkou **const**, `volatile`, a **__unaligned** kvalifikátory. Pro ukazatele a odkazy bude výsledek odkazovat na původní objekt. Pro ukazatele na datové členy bude výsledek odkazovat na stejný člen jako původní (nepřetypovaný) ukazatel na datový člen. V závislosti na typu odkazovaného objektu mohou operace zápisu skrz výsledný ukazatel, odkaz nebo ukazatel na datový člen mít za následek nedefinované chování.  
  
 Operátor `const_cast` nelze použít pro přímé přepsání konstantního stavu konstantní proměnné.  
  
 `const_cast` Operátor převede hodnotu ukazatele null. hodnota ukazatele null typu cílový.  
  
## <a name="example"></a>Příklad  
  
```  
// expre_const_cast_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class CCTest {  
public:  
   void setNumber( int );  
   void printNumber() const;  
private:  
   int number;  
};  
  
void CCTest::setNumber( int num ) { number = num; }  
  
void CCTest::printNumber() const {  
   cout << "\nBefore: " << number;  
   const_cast< CCTest * >( this )->number--;  
   cout << "\nAfter: " << number;  
}  
  
int main() {  
   CCTest X;  
   X.setNumber( 8 );  
   X.printNumber();  
}  
```  
  
 Na řádku obsahujícím operátor `const_cast` je datovým typem ukazatele `this` typ `const CCTest *`. Operátor `const_cast` změní datový typ ukazatele `this` na typ `CCTest *`, který umožňuje změnu členu `number`. Toto přetypování trvá pouze po zbytek příkazu, ve kterém se zobrazí.  
  
## <a name="see-also"></a>Viz také  
 [Operátory přetypování](../cpp/casting-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)