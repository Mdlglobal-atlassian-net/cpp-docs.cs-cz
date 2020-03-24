---
title: Podpora kompilátoru pro typové vlastnosti (C++/CLI a C++/CX)
ms.date: 10/12/2018
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
ms.openlocfilehash: 1bfb4308dc76e3393eceddf8dedd6d11e73adc17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172527"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>Podpora kompilátoru pro typové vlastnosti (C++/CLI a C++/CX)

Kompilátor společnosti C++ Microsoft podporuje *typové vlastnosti* pro C++rozšíření/CLI a C++/CX, což značí různé charakteristiky typu v době kompilace.

## <a name="all-runtimes"></a>Všechny moduly runtime

### <a name="remarks"></a>Poznámky

Typové vlastnosti jsou zvláště užitečné pro programátory, kteří zapisují knihovny.

Následující seznam obsahuje vlastnosti typu, které kompilátor podporuje. Pokud není splněna podmínka určená názvem vlastnosti typu, vrátí všechny vlastnosti typu **hodnotu false** .

(V následujícím seznamu jsou příklady kódu zapisovány pouze v C++/CLI. Ale odpovídající typ vlastnosti je také podporován v C++/CX, pokud není uvedeno jinak. Pojem "typ platformy" odkazuje buď na typy prostředí Windows Runtime, nebo na typy modulu CLR (Common Language Runtime).)

- *typ* `__has_assign(` `)`

   Vrátí **hodnotu true** , pokud má platforma nebo nativní typ operátor přiřazení kopie.

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- *typ* `__has_copy(` `)`

   Vrátí **hodnotu true** , pokud má platforma nebo nativní typ kopírovací konstruktor.

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- *typ* `__has_finalizer(` `)`

   (Nepodporováno C++v/CX.) Vrátí **hodnotu true** , pokud má typ CLR finalizační metodu. Další informace naleznete [v tématu Destruktory a finalizační metody v tématu How to: Define andC++spotřebovávají Classes and Structs (/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) .

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

- *typ* `__has_nothrow_assign(` `)`

   Vrátí **hodnotu true** , pokud operátor přiřazení kopie obsahuje prázdnou specifikaci výjimky.

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

- *typ* `__has_nothrow_constructor(` `)`

   Vrátí **hodnotu true** , pokud má výchozí konstruktor prázdnou specifikaci výjimky.

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

- *typ* `__has_nothrow_copy(` `)`

   Vrátí **hodnotu true** , pokud konstruktor Copy má prázdnou specifikaci výjimky.

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

- *typ* `__has_trivial_assign(` `)`

   Vrátí **hodnotu true** , pokud typ má triviální operátor přiřazení generovaný kompilátorem.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *typ* `__has_trivial_constructor(` `)`

   Vrátí **hodnotu true** , pokud typ má triviální konstruktor generovaný kompilátorem.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *typ* `__has_trivial_copy(` `)`

   Vrátí **hodnotu true** , pokud má typ triviální konstruktor Copy generovaný kompilátorem.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *typ* `__has_trivial_destructor(` `)`

   Vrátí **hodnotu true** , pokud typ má triviální kompilátor generovaný kompilátorem.

    ``` cpp
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *typ* `__has_user_destructor(` `)`

   Vrátí **hodnotu true** , pokud má platforma nebo nativní typ destruktor deklarovaný uživatelem.

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

- *typ* `__has_virtual_destructor(` `)`

   Vrátí **hodnotu true** , pokud typ má virtuální destruktor.

   `__has_virtual_destructor` také funguje na typech platforem a jakýkoli uživatelem definovaný destruktor v typu platformy je virtuální destruktor.

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

- *typ* `__is_abstract(` `)`

   Vrátí **hodnotu true** , pokud je typ abstraktní typ. Další informace o nativních abstraktních typech naleznete v tématu [abstraktní třídy](../cpp/abstract-classes-cpp.md).

   `__is_abstract` také funguje pro typy platforem. Rozhraní s aspoň jedním členem je abstraktní typ, jako typ odkazu s alespoň jedním abstraktním členem. Další informace o abstraktních typech platforem naleznete v tématu [abstract](abstract-cpp-component-extensions.md).

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

- `__is_base_of(` `base` `,` `derived` `)`

   Vrátí **hodnotu true** , pokud je první typ základní třídou druhého typu, pokud jsou oba typy stejné.

   `__is_base_of` také funguje na typech platforem. Například vrátí **hodnotu true** , pokud je první typ [Třída rozhraní](interface-class-cpp-component-extensions.md) a druhý typ implementuje rozhraní.

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

- *typ* `__is_class(` `)`

   Vrátí **hodnotu true** , pokud je typ nativní třída nebo struktura.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,``to` `)`

   Vrátí **hodnotu true** , pokud je první typ možné převést na druhý typ.

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

- *typ* `__is_delegate(` `)`

   Vrátí **hodnotu true** , pokud `type` je delegát. Další informace najdete v tématu [delegate (C++/CLI a C++/CX)](delegate-cpp-component-extensions.md).

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- *typ* `__is_empty(` `)`

   Vrátí **hodnotu true** , pokud typ neobsahuje žádné datové členy instance.

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

- *typ* `__is_enum(` `)`

   Vrátí **hodnotu true** , pokud je typ nativní výčet.

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

- *typ* `__is_interface_class(` `)`

   Vrátí **hodnotu pravda** , pokud byla předána rozhraní platformy. Další informace naleznete v tématu [Třída rozhraní](interface-class-cpp-component-extensions.md).

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- *typ* `__is_pod(` `)`

   Vrátí **hodnotu true** , pokud je typ třída nebo sjednocení bez konstruktoru nebo privátních nebo chráněných nestatických členů, žádné základní třídy a žádné virtuální funkce. Další informace C++ o luskech najdete v oddílech Standard, 8.5.1/1, 9/4 a 3.9/10.

   `__is_pod` vrátí hodnotu false u základních typů.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- *typ* `__is_polymorphic(` `)`

   Vrátí **hodnotu true** , pokud má nativní typ virtuální funkce.

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

- *typ* `__is_ref_array(` `)`

   Vrátí **hodnotu pravda** , pokud byla předána pole platformy. Další informace naleznete v tématu [pole](arrays-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- *typ* `__is_ref_class(` `)`

   Vrátí **hodnotu true** , pokud byla předána třída reference. Další informace o uživatelsky definovaných typech odkazů naleznete v tématu [třídy a struktury](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- *typ* `__is_sealed(` `)`

   Vrátí **hodnotu true** , pokud byla předána platforma nebo nativní typ označený jako Sealed. Další informace naleznete v tématu [sealed](sealed-cpp-component-extensions.md).

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- *typ* `__is_simple_value_class(` `)`

   Vrátí **hodnotu true** , pokud předává typ hodnoty, který neobsahuje žádné odkazy na haldu uvolňování paměti. Další informace o uživatelsky definovaných typech hodnot naleznete v tématu [třídy a struktury](classes-and-structs-cpp-component-extensions.md).

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

- *typ* `__is_union(` `)`

   Vrátí **hodnotu true** , pokud je typ sjednocení.

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

- *typ* `__is_value_class(` `)`

   Vrátí **hodnotu true** , pokud byl předán typ hodnoty. Další informace o uživatelsky definovaných typech hodnot naleznete v tématu [třídy a struktury](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="remarks"></a>Poznámky

*Typ* `__has_finalizer(``)` typ vlastnosti není podporován, protože tato platforma nepodporuje finalizační metody.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

### <a name="remarks"></a>Poznámky

(Pro tuto funkci nejsou k dispozici žádné poznámky specifické pro platformu.)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

**Příklad**

Následující příklad kódu ukazuje, jak použít šablonu třídy k vystavení vlastností typu kompilátoru pro `/clr` kompilaci. Další informace najdete v tématu [prostředí Windows Runtime a spravované šablony](windows-runtime-and-managed-templates-cpp-component-extensions.md).

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

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
