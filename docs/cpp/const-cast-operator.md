---
title: const_cast – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- const_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ba0312b255b2957c815bb5f26c97a668d4f7b6d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403021"
---
# <a name="constcast-operator"></a>const_cast – operátor
Odebere **const**, **volatile**, a **__unaligned** atributy ze třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
const_cast <type-id> (expression)  
```  
  
## <a name="remarks"></a>Poznámky  
 Ukazatel na libovolný typ objektu nebo ukazatel na datový člen lze explicitně převést na typ, který je totožný s výjimkou **const**, **volatile**, a **__unaligned** kvalifikátory. Pro ukazatele a odkazy bude výsledek odkazovat na původní objekt. Pro ukazatele na datové členy bude výsledek odkazovat na stejný člen jako původní (nepřetypovaný) ukazatel na datový člen. V závislosti na typu odkazovaného objektu mohou operace zápisu skrz výsledný ukazatel, odkaz nebo ukazatel na datový člen mít za následek nedefinované chování.  
  
 Nelze použít **const_cast** operátor pro přímé přepsání konstantního stavu konstantní proměnné.  
  
 **Const_cast** operátor převede hodnotu ukazatele null na hodnotu ukazatele null cílového typu.  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
  
 Na řádku obsahujícím operátor **const_cast**, datový typ **to** ukazatel `const CCTest *`. **Const_cast** operátor změní datový typ **to** ukazatel na `CCTest *`, umožňuje změnu členu `number` má být upraven. Toto přetypování trvá pouze po zbytek příkazu, ve kterém se zobrazí.  
  
## <a name="see-also"></a>Viz také:  
 [Operátory přetypování](../cpp/casting-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)