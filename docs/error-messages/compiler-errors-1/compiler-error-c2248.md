---
title: "C2248 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2248
dev_langs:
- C++
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b5493e6e91a639b83adcddcbd1f680d29ce9f9dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2248"></a>C2248 chyby kompilátoru
'*člen*': nemůže získat přístup k '*access_level*'člen deklarovaná ve třídě,*– třída*.  
  
Nelze získat přístup k členy odvozené třídy `private` členy základní třídy. Nelze získat přístup `private` nebo `protected` členy instancí třídy.  
  
## <a name="example"></a>Příklad  
  
Následující ukázka generuje C2248 při privátní nebo chráněné členy třídy, ke kterým se přistupuje z mimo třídu. Chcete-li tento problém vyřešit, přístup k těchto členů mimo třídu přímo. Použijte data veřejné členů a členské funkce pro interakci s třídou.  
  
```cpp  
// C2248_access.cpp 
// compile with: cl /EHsc /W4 C2248_access.cpp 
#include <stdio.h>  

class X {  
public:  
    int  m_publicMember;  
    void setPrivateMember( int i ) {  
        m_privateMember = i;  
        printf_s("\n%d", m_privateMember);  
    }  
protected:  
    int  m_protectedMember;  
  
private:  
    int  m_privateMember;  
} x;  
  
int main() {  
    x.m_publicMember = 4;  
    printf_s("\n%d", x.m_publicMember);  
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected  
    x.m_privateMember = 3;   // C2248  m_privMemb is private  
    x.setPrivateMember(0);   // OK uses public access function  
}  
```  
  
Jinému problému shoda, která zveřejňuje C2248 je použití šablona – friends a specializace. Chcete-li tento problém vyřešit, deklarujte friend funkce šablon s využitím prázdnou šablonou parametr seznamu <> nebo parametry konkrétní šablony.  
  
```cpp  
// C2248_template.cpp 
// compile with: cl /EHsc /W4 C2248_template.cpp 
template<class T>  
void f(T t) {  
    t.i;   // C2248  
}  
  
struct S {  
private:  
    int i;  
  
public:  
    S() {}  
    friend void f(S);   // refer to the non-template function void f(S)  
    // To fix, comment out the previous line and
    // uncomment the following line.  
    // friend void f<S>(S);  
};  
  
int main() {  
    S s;  
    f<S>(s);  
}  
```  
  
Jinému problému shoda, která zveřejňuje C2248 je při pokusu o deklarovat, přítele třídy a třída není viditelná pro deklaraci friend v oboru třídy. Chcete-li tento problém vyřešit, udělte Přátelský k třídě nadřazených.  
  
```cpp  
// C2248_enclose.cpp  
// compile with: cl /W4 /c C2248_enclose.cpp  
class T {  
    class S {  
        class E {};  
    };  
    friend class S::E;   // C2248  
};  
  
class A {  
    class S {  
        class E {};  
        friend class A;  // grant friendship to enclosing class  
    };  
    friend class S::E;   // OK  
};  
```