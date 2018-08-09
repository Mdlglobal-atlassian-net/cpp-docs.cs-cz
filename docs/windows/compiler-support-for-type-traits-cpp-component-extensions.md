---
title: Podpora kompilátoru pro typové vlastnosti (rozšíření komponent C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __is_simple_value_class
- __has_trivial_destructor
- __has_assign
- __is_union
- __is_class
- __is_abstract
- __has_trivial_assign
- __has_virtual_destructor
- __is_ref_array
- __is_base_of
- __has_copy
- __is_polymorphic
- __has_nothrow_constructor
- __is_ref_class
- __is_delegate
- __is_convertible_to
- __is_value_class
- __is_interface_class
- __has_nothrow_copy
- __is_sealed
- __has_trivial_constructor
- __has_trivial_copy
- __is_enum
- __has_nothrow_assign
- __has_finalizer
- __is_empty
- __is_pod
- __has_user_destructor
dev_langs:
- C++
helpviewer_keywords:
- __is_class keyword [C++]
- __is_pod keyword [C++]
- __is_delegate keyword [C++]
- __is_value_class keyword [C++]
- __has_copy keyword [C++]
- __has_nothrow_copy keyword [C++]
- __is_interface_class keyword [C++]
- __is_sealed keyword [C++]
- __is_convertible_to keyword [C++]
- __is_ref_class keyword [C++]
- __has_trivial_copy keyword [C++]
- __has_user_destructor keyword [C++]
- __is_abstract keyword [C++]
- __is_empty keyword [C++]
- __has_trivial_assign keyword [C++]
- __has_nothrow_constructor keyword [C++]
- __is_ref_array keyword [C++]
- __is_base_of keyword [C++]
- __has_nothrow_assign keyword [C++]
- __has_virtual_destructor keyword [C++]
- __has_finalizer keyword [C++]
- __is_union keyword [C++]
- __has_assign keyword [C++]
- __has_trivial_destructor keyword [C++]
- __is_polymorphic keyword [C++]
- __is_enum keyword [C++]
- __is_simple_value_class keyword [C++]
- __has_trivial_constructor keyword [C++]
ms.assetid: cd440630-0394-48c0-a16b-1580b6ef5844
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a88994133b65432566254fb77ddc35d5f2aab47b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644866"
---
# <a name="compiler-support-for-type-traits-c-component-extensions"></a>Podpora kompilátoru pro typové vlastnosti (C++ Component Extensions)
Kompilátor podporuje *zadejte vlastnosti*, který označuje různé vlastnosti typu v době kompilace.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
### <a name="remarks"></a>Poznámky  
  
 Typové vlastnosti jsou zvláště užitečné pro programátory, kteří vytvářejí knihovny.  
  
 Následující seznam obsahuje typové, které jsou podporovány kompilátorem. Zadejte všechny vlastnosti vrátit **false** Pokud není splněná podmínka uvedená v názvu vlastnosti typu.  
  
 (V seznamu následující příklady kódu byly vytvořeny pouze v jazyce C + +/ CLI. Ale odpovídající typ vlastnosti je podporováno také v [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)] Pokud není uvedeno jinak. Termín, "typ platformy" odkazuje na typy Windows Runtime nebo běžné language runtime typy.)  
  
-   `__has_assign(` `type` `)`  
  
     Vrátí **true** Pokud platformy nebo nativní typ má operátor přiřazení kopie.  
  
    ```cpp  
    ref struct R {  
    void operator=(R% r) {}  
    };  
  
    int main() {  
    System::Console::WriteLine(__has_assign(R));  
    }  
    ```  
  
-   `__has_copy(` `type` `)`  
  
     Vrátí **true** Pokud platformy nebo nativní typ má konstruktor kopie.  
  
    ```cpp  
    ref struct R {  
    R(R% r) {}  
    };  
  
    int main() {  
    System::Console::WriteLine(__has_copy(R));  
    }  
    ```  
  
-   `__has_finalizer(` `type` `)`  
  
     (Není podporováno v [!INCLUDE[cppwrt](../build/reference/includes/cppwrt_md.md)].) Vrátí **true** Pokud typ CLR má finalizační metodu. Zobrazit [destruktory a finalizační metody v tom, jak: definice a používání tříd a struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) Další informace.  
  
    ```cpp  
    using namespace System;  
    ref struct R {  
    ~R() {}  
    protected:  
    !R() {}  
    };  
  
    int main() {  
    Console::WriteLine(__has_finalizer(R));  
    }  
    ```  
  
-   `__has_nothrow_assign(` `type` `)`  
  
     Vrátí **true** Pokud operátor přiřazení kopie má specifikaci výjimky prázdný.  
  
    ```cpp  
    #include <stdio.h>  
    struct S {  
    void operator=(S& r) throw() {}  
    };  
  
    int main() {  
    __has_nothrow_assign(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__has_nothrow_constructor(` `type` `)`  
  
     Vrátí **true** Pokud výchozí konstruktor má specifikaci výjimky prázdný.  
  
    ```cpp  
    #include <stdio.h>  
    struct S {  
    S() throw() {}  
    };  
  
    int main() {  
    __has_nothrow_constructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__has_nothrow_copy(` `type` `)`  
  
     Vrátí **true** Pokud konstruktor kopie je specifikaci výjimky prázdný.  
  
    ```cpp  
    #include <stdio.h>  
    struct S {  
    S(S& r) throw() {}  
    };  
  
    int main() {  
    __has_nothrow_copy(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__has_trivial_assign(` `type` `)`  
  
     Vrátí **true** Pokud má typ přiřazení triviální, vygeneruje kompilátor operátor.  
  
    ```cpp  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_assign(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__has_trivial_constructor(` `type` `)`  
  
     Vrátí **true** Pokud má typ jednoduchého dotazu, vygeneruje kompilátor konstruktor.  
  
    ```cpp  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_constructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__has_trivial_copy(` `type` `)`  
  
     Vrátí **true** Pokud typ má konstruktor kopie triviální, generovaný kompilátorem.  
  
    ```cpp  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_copy(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__has_trivial_destructor(` `type` `)`  
  
     Vrátí **true** Pokud má typ jednoduchého dotazu, vygeneruje kompilátor destruktor.  
  
    ``` cpp 
    // has_trivial_destructor.cpp  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __has_trivial_destructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__has_user_destructor(` `type` `)`  
  
     Vrátí **true** Pokud platformy nebo nativní typ má destruktor uživatelem deklarované.  
  
    ```cpp
    // has_user_destructor.cpp  
  
    using namespace System;  
    ref class R {  
    ~R() {}  
    };  
  
    int main() {  
    Console::WriteLine(__has_user_destructor(R));  
    }  
    ```  
  
-   `__has_virtual_destructor(` `type` `)`  
  
     Vrátí **true** Pokud typ má virtuální destruktor.  
  
     `__has_virtual_destructor` funguje na typech platforem a uživatelem definovaný destruktor typu platformy je také virtuální destruktor.  
  
    ```cpp  
    // has_virtual_destructor.cpp  
    #include <stdio.h>  
    struct S {  
    virtual ~S() {}  
    };  
  
    int main() {  
    __has_virtual_destructor(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__is_abstract(` `type` `)`  
  
     Vrátí **true** Pokud abstraktní typ je typ. Další informace o nativní abstraktní typy, najdete v části [abstraktní](../windows/abstract-cpp-component-extensions.md).  
  
     `__is_abstract` funguje i pro typy platforem. Rozhraní s nejméně jeden člen je abstraktní typ, jako je typem odkazu s alespoň jeden abstraktní člen. Další informace o typech abstraktní platforem, naleznete v tématu [abstraktní třídy](../cpp/abstract-classes-cpp.md)  
  
    ```cpp  
    // is_abstract.cpp  
    #include <stdio.h>  
    struct S {  
    virtual void Test() = 0;  
    };  
  
    int main() {  
    __is_abstract(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__is_base_of(` `base` `,` `derived` `)`  
  
     Vrátí **true** Pokud prvním typem je základní třídou druhý typ, pokud oba typy jsou stejné.  
  
     `__is_base_of` funguje taky na typech platforem. Například vrátí **true** Pokud je první typ [třída rozhraní](../windows/interface-class-cpp-component-extensions.md) a druhý typ implementuje rozhraní.  
  
    ```cpp
    // is_base_of.cpp  
    #include <stdio.h>  
    struct S {};  
    struct T : public S {};  
  
    int main() {  
    __is_base_of(S, T) == true ?  
    printf("true\n") : printf("false\n");  
  
    __is_base_of(S, S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__is_class(` `type` `)`  
  
     Vrátí **true** Pokud je typ nativní třídy nebo struktury.  
  
    ```cpp
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __is_class(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__is_convertible_to(` `from` `,`  `to` `)`  
  
     Vrátí **true** Pokud první typ lze převést na typ druhého.  
  
    ```cpp  
    #include <stdio.h>  
    struct S {};  
    struct T : public S {};  
  
    int main() {  
    S * s = new S;  
    T * t = new T;  
    s = t;  
    __is_convertible_to(T, S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__is_delegate(` `type` `)`  
  
     Vrátí **true** Pokud `type` je delegát. Další informace najdete v tématu [delegate (rozšíření komponent C++)](../windows/delegate-cpp-component-extensions.md).  
  
    ```cpp  
    delegate void MyDel();  
    int main() {  
    System::Console::WriteLine(__is_delegate(MyDel));  
    }  
    ```  
  
-   `__is_empty(` `type` `)`  
  
     Vrátí **true** Pokud typ nemá žádné datové členy instance.  
  
    ```cpp  
    #include <stdio.h>  
    struct S {  
    int Test() {}  
    static int i;  
    };  
    int main() {  
    __is_empty(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__is_enum(` `type` `)`  
  
     Vrátí **true** typ je nativní výčet.  
  
    ```cpp
    // is_enum.cpp  
    #include <stdio.h>  
    enum E { a, b };  
  
    struct S {  
    enum E2 { c, d };  
    };  
  
    int main() {  
    __is_enum(E) == true ?  
    printf("true\n") : printf("false\n");  
  
    __is_enum(S::E2) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__is_interface_class(` `type` `)`  
  
     Vrátí **true** Pokud předaná rozhraní platformy. Další informace najdete v tématu [třída rozhraní](../windows/interface-class-cpp-component-extensions.md).  
  
    ```cpp
    // is_interface_class.cpp  
  
    using namespace System;  
    interface class I {};  
    int main() {  
    Console::WriteLine(__is_interface_class(I));  
    }  
    ```  
  
-   `__is_pod(` `type` `)`  
  
     Vrátí **true** Pokud je typ třídy nebo sjednocení se žádný konstruktor nebo soukromé nebo chráněné nestatické členy žádné základní třídy a žádné virtuální funkce. C++ standard, oddíly 8.5.1/1, 9 nebo 4 a 3.9/10 pro další informace naleznete na tyto Pody.  
  
     `__is_pod` Vrátí hodnotu false na základní typy.  
  
    ```cpp  
    #include <stdio.h>  
    struct S {};  
  
    int main() {  
    __is_pod(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__is_polymorphic(` `type` `)`  
  
     Vrátí **true** pokud nativní typ má virtuální funkce.  
  
    ```cpp  
    #include <stdio.h>  
    struct S {  
    virtual void Test(){}  
    };  
  
    int main() {  
    __is_polymorphic(S) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__is_ref_array(` `type` `)`  
  
     Vrátí **true** Pokud předaná pole platformy. Další informace najdete v tématu [pole](../windows/arrays-cpp-component-extensions.md).  
  
    ```cpp  
    using namespace System;  
    int main() {  
    array<int>^ x = gcnew array<int>(10);  
    Console::WriteLine(__is_ref_array(array<int>));  
    }  
    ```  
  
-   `__is_ref_class(` `type` `)`  
  
     Vrátí **true** předán referenční třídy. Další informace o typy odkazů definované uživatelem, naleznete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md).  
  
    ```cpp  
    using namespace System;  
    ref class R {};  
    int main() {  
    Console::WriteLine(__is_ref_class(Buffer));  
    Console::WriteLine(__is_ref_class(R));  
    }  
    ```  
  
-   `__is_sealed(` `type` `)`  
  
     Vrátí **true** předán platformy nebo nativní typ označen zapečetěné. Další informace najdete v tématu [zapečetěné](../windows/sealed-cpp-component-extensions.md).  
  
    ```cpp  
    ref class R sealed{};  
    int main() {  
    System::Console::WriteLine(__is_sealed(R));  
    }  
    ```  
  
-   `__is_simple_value_class(` `type` `)`  
  
     Vrátí **true** předán hodnotový typ, který neobsahuje žádné odkazy na haldě uvolňování. Další informace o typech hodnotu definovanou uživatelem, naleznete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md).  
  
    ```cpp  
    using namespace System;  
    ref class R {};  
    value struct V {};  
    value struct V2 {  
    R ^ r;   // not a simnple value type  
    };  
  
    int main() {  
    Console::WriteLine(__is_simple_value_class(V));  
    Console::WriteLine(__is_simple_value_class(V2));  
    }  
    ```  
  
-   `__is_union(` `type` `)`  
  
     Vrátí **true** Pokud je typ sjednocení.  
  
    ```cpp  
    #include <stdio.h>  
    union A {  
    int i;  
    float f;  
    };  
  
    int main() {  
    __is_union(A) == true ?  
    printf("true\n") : printf("false\n");  
    }  
    ```  
  
-   `__is_value_class(` `type` `)`  
  
     Vrátí **true** předán typ hodnoty. Další informace o typech hodnotu definovanou uživatelem, naleznete v tématu [třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md).  
  
    ```cpp  
    value struct V {};  
  
    int main() {  
    System::Console::WriteLine(__is_value_class(V));  
    }  
    ```  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
### <a name="remarks"></a>Poznámky  
  
 `__has_finalizer(` *Typ* `)` typovou vlastnost není podporována, protože tato platforma nepodporuje finalizační metody.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/ZW`  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
### <a name="remarks"></a>Poznámky  
  
 (Neexistují žádné poznámky specifické pro platformu pro tuto funkci.)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/clr`  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu ukazuje, jak použít šablonu třídy vystavit vlastnosti kompilátoru typu pro `/clr` kompilace. Další informace najdete v tématu [Windows Runtime a spravované šablony](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).  
  
```cpp  
// compiler_type_traits.cpp  
// compile with: /clr  
using namespace System;  
  
template <class T>  
ref struct is_class {  
   literal bool value = __is_ref_class(T);  
};  
  
ref class R {};  
  
int main () {  
   if (is_class<R>::value)  
      Console::WriteLine("R is a ref class");  
   else  
      Console::WriteLine("R is not a ref class");  
}  
```  
  
```Output  
R is a ref class  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)