---
title: __if_exists – příkaz | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __if_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac866487c25ee4ce75abbebe9b9f9c2a5e97828
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405941"
---
# <a name="ifexists-statement"></a>__if_exists – příkaz
**__If_exists** příkaz testuje, jestli existuje zadaný identifikátor. Pokud identifikátor neexistuje, je spuštěn zadaný blok příkazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__if_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*identifikátor*|Identifikátor, jehož existence bude testována.|  
|*Příkazy*|Jeden nebo více příkazů, které budou spuštěny, pokud *identifikátor* existuje.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  K dosažení nejspolehlivějších výsledků, použít **__if_exists** příkaz následujícími omezeními.  
  
-   Použít **__if_exists** příkazu pouze jednoduché typy, nikoli na šablony.  
  
-   Použít **__if_exists** příkaz na identifikátory uvnitř i vně třídy. Se nevztahují **__if_exists** příkaz pro lokální proměnné.  
  
-   Použití **__if_exists** příkaz jenom v těle funkce. Mimo tělo funkce **__if_exists** příkazu můžete testovat pouze plně definované typy.  
  
-   Při testování přetížených funkcí nelze testovat konkrétní formu přetížení.  
  
 Doplněk k **__if_exists** příkaz je [__if_not_exists](../cpp/if-not-exists-statement.md) příkazu.  
  
## <a name="example"></a>Příklad  
 Všimněte si, že v tomto příkladu šablony, které se nedoporučuje.  
  
```cpp 
// the__if_exists_statement.cpp  
// compile with: /EHsc  
#include <iostream>  
  
template<typename T>  
class X : public T {  
public:  
   void Dump() {  
      std::cout << "In X<T>::Dump()" << std::endl;  
  
      __if_exists(T::Dump) {  
         T::Dump();  
      }  
  
      __if_not_exists(T::Dump) {  
         std::cout << "T::Dump does not exist" << std::endl;  
      }  
   }     
};  
  
class A {  
public:  
   void Dump() {  
      std::cout << "In A::Dump()" << std::endl;  
   }  
};  
  
class B {};  
  
bool g_bFlag = true;  
  
class C {  
public:  
   void f(int);  
   void f(double);  
};  
  
int main() {   
   X<A> x1;  
   X<B> x2;  
  
   x1.Dump();  
   x2.Dump();  
  
   __if_exists(::g_bFlag) {  
      std::cout << "g_bFlag = " << g_bFlag << std::endl;  
   }  
  
   __if_exists(C::f) {  
      std::cout << "C::f exists" << std::endl;  
   }  
  
   return 0;  
}  
```  
  
## <a name="output"></a>Výstup  
  
```Output  
In X<T>::Dump()  
In A::Dump()  
In X<T>::Dump()  
T::Dump does not exist  
g_bFlag = 1  
C::f exists  
```  
  
## <a name="see-also"></a>Viz také:  
 [Příkazy výběru](../cpp/selection-statements-cpp.md)   
 [klíčová slova](../cpp/keywords-cpp.md)   
 [__if_not_exists – příkaz](../cpp/if-not-exists-statement.md)