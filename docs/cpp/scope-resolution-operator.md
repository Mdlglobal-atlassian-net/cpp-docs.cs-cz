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
ms.openlocfilehash: e601bed976009a72a43545d8d38a38d75e93a137
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452270"
---
# <a name="scope-resolution-operator-"></a>Operátor řešení rozsahu: ::

Operátor rozlišení rozsahu **::** slouží k identifikaci a rozlišení identifikátory použitými v různých rozsazích. Další informace o oboru, naleznete v tématu [oboru](../cpp/scope-visual-cpp.md).

## <a name="syntax"></a>Syntaxe

```
:: identifier
class-name :: identifier
namespace :: identifier
enum class :: identifier
enum struct :: identifier
```

## <a name="remarks"></a>Poznámky

`identifier` Může být proměnné, funkce nebo hodnoty výčtu.

## <a name="with-classes-and-namespaces"></a>Pomocí třídy a obory názvů

Následující příklad ukazuje, jak se operátor rozlišení rozsahu používá obory názvů a třídy:

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

Operátor rozlišení rozsahu bez kvalifikátoru oboru odkazuje na globální obor názvů.

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

Operátor rozlišení rozsahu můžete použít k identifikaci členem oboru názvů, nebo k identifikaci oboru názvů, který se jmenuje člena oboru názvů pomocí směrnice. V následujícím příkladu můžete použít `NamespaceC` kvalifikovat `ClassB`, i když `ClassB` byl deklarován v oboru názvů `NamespaceB`, protože `NamespaceB` byl jmenovaný v `NamespaceC` pomocí směrnice.

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

Můžete použít řetězy operátory oboru rozlišení. V následujícím příkladu `NamespaceD::NamespaceD1` identifikuje vnořené obory názvů `NamespaceD1`, a `NamespaceE::ClassE::ClassE1` identifikuje vnořené třídy `ClassE1`.

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

Operátor rozlišení oboru musí použít k volání statické členy třídy.

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

## <a name="with-scoped-enumerations"></a>S výčty s vymezeným oborem

Operátoru rozsahu rozlišení slouží také s hodnotami výčet s oborem [deklarace výčtů](../cpp/enumerations-cpp.md), jako v následujícím příkladu:

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

## <a name="see-also"></a>Viz také:

[Integrované operátory C++, jejich priorita a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Obory názvů](../cpp/namespaces-cpp.md)