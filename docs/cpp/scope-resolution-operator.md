---
title: "Operátor řešení rozsahu::: | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '::'
dev_langs: C++
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69b52b3029271ffae3d4a7b3441c49a01270abb4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="scope-resolution-operator-"></a>Operátor řešení rozsahu: ::
Operátor řešení rozsahu `::` se používá k identifikaci a odstranit nejednoznačnost identifikátory používané v různých oborech. Další informace o rozsahu najdete v tématu [oboru](../cpp/scope-visual-cpp.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
:: identifier  
class-name :: identifier  
namespace :: identifier  
enum class :: identifier  
enum struct :: identifier  
```  
  
## <a name="remarks"></a>Poznámky  
 `identifier` Může být proměnné, funkce nebo hodnotu výčtu.  
  
## <a name="with-classes-and-namespaces"></a>S třídami a obory názvů  
 Následující příklad ukazuje, jak se používá operátor řešení rozsahu se obory názvů a třídy:  
  
```cpp  
namespace NamespaceA{  
    int x;  
    class ClassA {  
    public:  
        int x;  
    };  
}  
  
int main() {  
  
    // A namespace name used to disambiguate  
    NamespaceA::x = 1;  
  
    // A class name used to disambiguate  
    NamespaceA::ClassA a1;  
    a1.x = 2;  
  
}  
  
```  
  
 Operátor řešení rozsahu bez kvalifikátor oboru odkazuje na obor názvů globální.  
  
```cpp  
namespace NamespaceA{  
    int x;  
}  
  
int x;   
  
int main() {  
    int x;  
  
    // the x in main()  
    x = 0;   
    // The x in the global namespace  
    ::x = 1;   
  
    // The x in the A namespace  
    NamespaceA::x = 2;   
}  
```  
  
 Operátor řešení rozsahu slouží k identifikaci členů oboru názvů, nebo obor názvů, který se jmenuje oboru názvů člen v pomocí direktiva zjistit. V následujícím příkladu můžete použít `NamespaceC` ke kvalifikaci `ClassB`, i když `ClassB` byla deklarována v oboru názvů `NamespaceB`, protože `NamespaceB` byla uvedené v `NamespaceC` pomocí direktiva.  
  
```cpp  
namespace NamespaceB {  
    class ClassB {  
    public:  
        int x;  
    };  
}  
  
namespace NamespaceC{  
    using namespace B;  
  
}  
int main() {  
    NamespaceB::ClassB c_b;  
    NamespaceC::ClassB c_c;  
  
    c_b.x = 3;  
    c_c.x = 4;  
}  
  
```  
  
 Můžete použít řetězy operátorů oboru rozlišení. V následujícím příkladu `NamespaceD::NamespaceD1` identifikuje vnořené obor názvů `NamespaceD1`, a `NamespaceE::ClassE::ClassE1` identifikuje vnořené třídy `ClassE1`.  
  
```cpp  
namespace NamespaceD{  
    namespace NamespaceD1{  
        int x;  
    }  
}  
  
namespace NamespaceE{  
  
    class ClassE{  
    public:  
        class ClassE1{  
        public:  
            int x;  
        };  
    };  
}  
  
int main() {  
    NamespaceD:: NamespaceD1::x = 6;  
    NamespaceE::ClassE::ClassE1 e1;  
    e1.x = 7  ;  
}  
  
```  
  
## <a name="with-static-members"></a>S statické členy  
 Operátor řešení rozsahu musíte použít k volání statické členy třídy.  
  
```cpp  
class ClassG {  
public:  
    static int get_x() { return x;}  
    static int x;  
};  
  
int ClassG::x = 6;  
  
int main() {  
  
    int gx1 = ClassG::x;  
    int gx2 = ClassG::get_x();   
}  
  
```  
  
## <a name="with-scoped-enumerations"></a>S vymezená výčty  
 Operátor oboru řešení používá taky hodnotami vymezená výčtu [deklarace výčtů](../cpp/enumerations-cpp.md), jako v následujícím příkladu:  
  
```cpp  
enum class EnumA{  
    First,  
    Second,  
    Third  
};  
  
int main() {  
  
    EnumA enum_value = EnumA::First;  
}  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Obory názvů](../cpp/namespaces-cpp.md)   