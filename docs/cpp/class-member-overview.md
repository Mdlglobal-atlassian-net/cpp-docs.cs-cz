---
title: Přehled členů třídy
ms.date: 11/04/2016
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
ms.openlocfilehash: cb978434707a9a7808b3388fc541ce4e0d996b0f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366679"
---
# <a name="class-member-overview"></a>Přehled členů třídy

Třída nebo struktura se skládá z jejích členů. Práce, kterou třída provádí, je prováděna jeho členskými funkcemi. Stav, který udržuje, je uložen v jeho datových členech. Inicializace členů se provádí konstruktory a čištění práce, jako je uvolnění paměti a uvolnění prostředků se provádí destruktory. V jazyce C++ 11 a novějších mohou být (a obvykle by měly) být členy dat inicializovány v okamžiku deklarace.

## <a name="kinds-of-class-members"></a>Druhy členů třídy

Úplný seznam kategorií členů je následující:

- [Zvláštní členské funkce](special-member-functions.md).

- [Přehled členských funkcí](overview-of-member-functions.md).

- [Datové členy](static-members-cpp.md) včetně předdefinovaných typů a dalších uživatelem definovaných typů.

- Operátory

- [Vnořené deklarace tříd a.)](nested-class-declarations.md)

- [Sjednocení](unions.md)

- [Výčty](../cpp/enumerations-cpp.md).

- [Bitová pole](../cpp/cpp-bit-fields.md).

- [Přátelé](../cpp/friend-cpp.md).

- [Aliasy a typedefs](../cpp/aliases-and-typedefs-cpp.md).

    > [!NOTE]
    >  Přátelé jsou zahrnuty v předchozím seznamu, protože jsou obsaženy v deklaraci třídy. Nejsou však skutečnými členy třídy, protože nejsou v oboru třídy.

## <a name="example-class-declaration"></a>Ukázková deklarace třídy

Následující příklad ukazuje jednoduchou deklaraci třídy:

```cpp
// TestRun.h

class TestRun
{
    // Start member list.

    //The class interface accessible to all callers.
public:
    // Use compiler-generated default constructor:
    TestRun() = default;
    // Don't generate a copy constructor:
    TestRun(const TestRun&) = delete;
    TestRun(std::string name);
    void DoSomething();
    int Calculate(int a, double d);
    virtual ~TestRun();
    enum class State { Active, Suspended };

    // Accessible to this class and derived classes only.
protected:
    virtual void Initialize();
    virtual void Suspend();
    State GetState();

    // Accessible to this class only.
private:
    // Default brace-initialization of instance members:
    State _state{ State::Suspended };
    std::string _testName{ "" };
    int _index{ 0 };

    // Non-const static member:
    static int _instances;
    // End member list.
};

// Define and initialize static member.
int TestRun::_instances{ 0 };
```

## <a name="member-accessibility"></a>Přístupnost členů

Členové třídy jsou deklarováni v seznamu členů. Seznam členů třídy lze rozdělit do libovolného počtu **soukromých**, **chráněných** a **veřejných** oddílů pomocí klíčových slov označovaných jako specifikátory přístupu.  Dvojtečka **:** musí následovat specifikátor přístupu.  Tyto části nemusejí být souvislé, to znamená, že některé z těchto klíčových slov se mohou v seznamu členů objevit několikrát.  Klíčové slovo určuje přístup všech členů, dokud se neobjeví další specifikátor přístupu nebo uzavírací složená závorka. Další informace naleznete [v tématu Řízení přístupu členů (C++)](../cpp/member-access-control-cpp.md).

## <a name="static-members"></a>Statické členy

Datový člen může být deklarován jako statický, což znamená, že všechny objekty třídy mají přístup ke stejné kopii. Členská funkce může být deklarována jako statická, v takovém případě může přistupovat pouze ke statickým datovým členům třídy (a nemá žádný *tento* ukazatel). Další informace naleznete v [tématu Static Data Members](../cpp/static-members-cpp.md).

## <a name="special-member-functions"></a>Zvláštní členské funkce

Speciální členské funkce jsou funkce, které jsou automaticky poskytovány kompilátorem, pokud je nezadáte ve zdrojovém kódu.

1. Výchozí konstruktor

1. Kopírovací konstruktor

1. **(Šp.++11)** Přesunout konstruktor

1. Kopírovat operátor přiřazení

1. **(Šp.++11)** Operátor přiřazení přesunutí

1. Destruktor

Další informace naleznete v [tématu Zvláštní členské funkce](../cpp/special-member-functions.md).

## <a name="memberwise-initialization"></a>Členské inicializace

V jazyce C++ 11 a novějším mohou deklarátory nestatických členů obsahovat inicializátory.

```cpp
class CanInit
{
public:
    long num {7};       // OK in C++11
    int k = 9;          // OK in C++11
    static int i = 9; // Error: must be defined and initialized
                      // outside of class declaration.

    // initializes num to 7 and k to 9
    CanInit(){}

    // overwrites original initialized value of num:
    CanInit(int val) : num(val) {}
};
int main()
{
}
```

Pokud člen je přiřazena hodnota v konstruktoru, tato hodnota přepíše hodnotu, s níž byl člen inicializován v bodě deklarace.

Existuje pouze jedna kopie sdílených statických datových členů pro všechny objekty typu dané třídy. Statické datové členy musejí být definovány a mohou být inicializovány v rozsahu souboru. (Další informace o statických datových členech naleznete v [tématu Static Data Members](../cpp/static-members-cpp.md).) Následující příklad ukazuje, jak provést tyto inicializace:

```cpp
// class_members2.cpp
class CanInit2
{
public:
    CanInit2() {} // Initializes num to 7 when new objects of type
                 //  CanInit are created.
    long     num {7};
    static int i;
    static int j;
};

// At file scope:

// i is defined at file scope and initialized to 15.
// The initializer is evaluated in the scope of CanInit.
int CanInit2::i = 15;

// The right side of the initializer is in the scope
// of the object being initialized
int CanInit2::j = i;
```

> [!NOTE]
> Název třídy `CanInit2` musí předcházet identifikátor `i`, čímž určíte, že definovaný identifikátor `i` je členem třídy `CanInit2`.

## <a name="see-also"></a>Viz také

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)
