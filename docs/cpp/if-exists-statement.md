---
title: "__if_exists – příkaz | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __if_exists_cpp
dev_langs: C++
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c22374acb8bdd794ea20fdcb1f798c2a240cdf58
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ifexists-statement"></a>__if_exists – příkaz
Příkaz `__if_exists` testuje, zda existuje zadaný identifikátor. Pokud existuje identifikátor, blok zadaný příkaz je spustit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__if_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`identifier`|Identifikátor, jehož existence bude testována.|  
|`statements`|Jeden nebo více příkazů k provedení Pokud `identifier` existuje.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  K dosažení nejspolehlivějších výsledků je třeba použít příkaz `__if_exists` s následujícími omezeními.  
  
-   Příkaz `__if_exists` je třeba použít pouze na jednoduché typy, nikoli na šablony.  
  
-   Příkaz `__if_exists` je třeba použít na identifikátory uvnitř i vně třídy. Příkaz `__if_exists` se nepoužívá pro lokální proměnné.  
  
-   Příkaz `__if_exists` je třeba použít pouze v rámci těla funkce. Mimo tělo funkce může příkaz `__if_exists` testovat pouze plně definované typy.  
  
-   Při testování přetížených funkcí nelze testovat konkrétní formu přetížení.  
  
 Doplněk k `__if_exists` příkaz [__if_not_exists –](../cpp/if-not-exists-statement.md) příkaz.  
  
## <a name="example"></a>Příklad  
 Všimněte si, že tento příklad používá šablony, které se nedoporučuje.  
  
```  
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
  
```  
In X<T>::Dump()  
In A::Dump()  
In X<T>::Dump()  
T::Dump does not exist  
g_bFlag = 1  
C::f exists  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkazy výběru](../cpp/selection-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [__if_not_exists – příkaz](../cpp/if-not-exists-statement.md)