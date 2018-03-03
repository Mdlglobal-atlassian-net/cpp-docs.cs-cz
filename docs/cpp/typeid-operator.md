---
title: "typeid – operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b27f3bcb7358b3ea05907df1a4372c107538dfb4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="typeid-operator"></a>typeid – operátor
## <a name="syntax"></a>Syntaxe  
  
```  
  
      typeid(   
      type-id  
       )  
typeid( expression )  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátor `typeid` umožňuje určit typ objektu v době běhu.  
  
 Výsledek `typeid` je **const type_info &**. Hodnota je odkaz na **type_info** objekt, který reprezentuje buď *id typu* nebo typ *výraz*podle toho, jaký typ `typeid` slouží . V tématu [type_info – třída](../cpp/type-info-class.md) Další informace.  
  
 `typeid` Operátor nefunguje s spravované typy (deklarátory abstraktu jazyka nebo instance) najdete v tématu [typeid](../windows/typeid-cpp-component-extensions.md) informace o získávání <xref:System.Type> zadaného typu.  
  
 Operátor `typeid` provádí kontrolu za běhu při použití na l-hodnotu polymorfního typu třídy, kde nelze určit skutečný typ objektu pomocí poskytnutých statických údajů. Takové případy jsou:  
  
-   odkaz na třídu,  
  
-   ukazatel, přístup přes ukazatel pomocí *,  
  
-   indexovaný ukazatel (tj. [ ]). (Použití indexu s ukazatelem na polymorfní typ není obecně bezpečné.)  
  
 Pokud *výraz* odkazuje na typ základní třída, dosud objekt ve skutečnosti je typu odvozeného od základní třídy, **type_info** reference pro odvozené třídy je výsledek. *Výraz* musí odkazovat na polymorfní typ (třída s virtuální funkce). Jinak, výsledkem je **type_info** pro statické třídy podle *výraz*. Dále musí být ukazatel odkázán tak, aby se použil objekt, na který odkazuje. Bez vyhodnocení ukazatele, výsledkem bude **type_info** pro ukazatele, není co IT oddělení odkazuje na. Příklad:  
  
```  
// expre_typeid_Operator.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <typeinfo.h>  
  
class Base {  
public:  
   virtual void vvfunc() {}  
};  
  
class Derived : public Base {};  
  
using namespace std;  
int main() {  
   Derived* pd = new Derived;  
   Base* pb = pd;  
   cout << typeid( pb ).name() << endl;   //prints "class Base *"  
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"  
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"  
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"  
   delete pd;  
}  
```  
  
 Pokud *výraz* je vyhodnocení ukazatel, a že je hodnota ukazatele nula, **typeid** vyvolá [bad_typeid – výjimka](../cpp/bad-typeid-exception.md). Pokud je ukazatel neodkazuje na platný objekt `__non_rtti_object` je vyvolána výjimka, označující pokus o analýze RTTI, který aktivoval chybu (jako jsou například porušení přístupu), protože objekt nějakým způsobem je neplatný (Chybný ukazatel nebo kód nebyl kompilovat s [GR](../build/reference/gr-enable-run-time-type-information.md)).  
  
 Pokud *výraz* není ukazatel ani odkaz na základní třídu objektu, výsledkem je, **type_info** představující statický typ odkazu *výraz*. *Statického typu* výrazu odkazuje na typ výrazu je známý v době kompilace. Sémantika provádění je při vyhodnocování statického typu výrazu ignorována. Kromě toho jsou odkazy ignorovány, pokud je to při stanovení statického typu výrazu možné:  
  
```  
// expre_typeid_Operator_2.cpp  
#include <typeinfo>  
  
int main()  
{  
   typeid(int) == typeid(int&); // evaluates to true  
}  
```  
  
 **typeid** lze také použít v šablonách určit typ parametru šablony:  
  
```  
// expre_typeid_Operator_3.cpp  
// compile with: /c  
#include <typeinfo>  
template < typename T >   
T max( T arg1, T arg2 ) {  
   cout << typeid( T ).name() << "s compared." << endl;  
   return ( arg1 > arg2 ? arg1 : arg2 );  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Informace běhového typu](../cpp/run-time-type-information.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)