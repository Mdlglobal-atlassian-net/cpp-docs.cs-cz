---
title: 'Operátor řešení rozsahu: ::'
ms.date: 11/04/2016
f1_keywords:
- '::'
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
ms.openlocfilehash: 07c2884ed0ba114c22a0c71bbaf7268d6f6931a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178883"
---
# <a name="scope-resolution-operator-"></a>Operátor řešení rozsahu: ::

Operátor rozlišení oboru **::** slouží k identifikaci a jednoznačnému použití identifikátorů používaných v různých oborech. Další informace o oboru naleznete v tématu [Scope](../cpp/scope-visual-cpp.md).

## <a name="syntax"></a>Syntaxe

```
:: identifier
class-name :: identifier
namespace :: identifier
enum class :: identifier
enum struct :: identifier
```

## <a name="remarks"></a>Poznámky

`identifier` může být proměnná, funkce nebo hodnota výčtu.

## <a name="with-classes-and-namespaces"></a>S třídami a obory názvů

Následující příklad ukazuje, jak se operátor rozlišení oboru používá s obory názvů a třídami:

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

Operátor rozlišení oboru bez kvalifikátoru oboru odkazuje na globální obor názvů.

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

Můžete použít operátor rozlišení oboru k identifikaci člena oboru názvů nebo k identifikaci oboru názvů, který je jmenován v oboru názvů člena v direktivě using. V následujícím příkladu můžete použít `NamespaceC` k získání `ClassB`, i když `ClassB` byl deklarován v oboru názvů `NamespaceB`, protože `NamespaceB` byl jmenován `NamespaceC` pomocí direktivy using.

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

Můžete použít řetězce operátorů rozlišení oboru. V následujícím příkladu `NamespaceD::NamespaceD1` identifikuje vnořený obor názvů `NamespaceD1`a `NamespaceE::ClassE::ClassE1` identifikuje `ClassE1`vnořené třídy.

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

## <a name="with-static-members"></a>Se statickými členy

Je nutné použít operátor rozlišení oboru pro volání statických členů třídy.

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

## <a name="with-scoped-enumerations"></a>S vymezenými výčty

Operátor rozlišení s oborem se používá také s hodnotami [deklarací](../cpp/enumerations-cpp.md)výčtu výčtu s vymezeným oborem, jak je uvedeno v následujícím příkladu:

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

[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Obory názvů](../cpp/namespaces-cpp.md)
