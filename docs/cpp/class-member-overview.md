---
title: Přehled členů třídy
ms.date: 11/04/2016
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
ms.openlocfilehash: 7847de072b2c0d5b95597e88f9ebf7e2ad63e180
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180950"
---
# <a name="class-member-overview"></a>Přehled členů třídy

Třída nebo struktura se skládá z jejích členů. Práce, kterou třída provádí pomocí jejích členských funkcí. Stav, který je udržován, je uložen ve svých datových členech. Inicializace členů je prováděna konstruktory a čistící práce, jako je uvolnění paměti a uvolnění prostředků, jsou prováděny destruktory. V C++ 11 a novějších mohou být datové členy (a obvykle by) inicializovány v místě deklarace.

## <a name="kinds-of-class-members"></a>Druhy členů třídy

Úplný seznam kategorií členů je následující:

- [Speciální členské funkce](special-member-functions.md).

- [Přehled členských funkcí](overview-of-member-functions.md)

- [Datové členy](static-members-cpp.md) , včetně vestavěných typů a dalších uživatelsky definovaných typů.

- Operátory

- [Deklarace vnořených tříd](nested-class-declarations.md) a.)

- [Sjednocení](unions.md)

- [Výčty](../cpp/enumerations-cpp.md).

- [Bitová pole](../cpp/cpp-bit-fields.md).

- [Přátelé](../cpp/friend-cpp.md).

- [Aliasy a definice typedef](../cpp/aliases-and-typedefs-cpp.md).

    > [!NOTE]
    >  Přátelé jsou zahrnuty v předchozím seznamu, protože jsou obsaženy v deklaraci třídy. Nejsou však skutečnými členy třídy, protože nejsou v oboru třídy.

## <a name="example-class-declaration"></a>Příklad deklarace třídy

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

## <a name="member-accessibility"></a>Přístupnost člena

Členy třídy jsou deklarovány v seznamu členů. Seznam členů třídy může být rozdělen na libovolný počet **privátních**, **chráněných** a **veřejných** oddílů pomocí klíčových slov označovaných jako specifikátory přístupu.  Dvojtečka **:** musí následovat po specifikátoru přístupu.  Tyto části nemusejí být souvislé, to znamená, že některé z těchto klíčových slov se mohou v seznamu členů objevit několikrát.  Klíčové slovo určuje přístup všech členů, dokud se neobjeví další specifikátor přístupu nebo uzavírací složená závorka. Další informace naleznete v tématu [Member Access Control (C++)](../cpp/member-access-control-cpp.md).

## <a name="static-members"></a>Statické členy

Datový člen může být deklarován jako static, což znamená, že všechny objekty třídy mají přístup ke stejné kopii. Členská funkce může být deklarována jako statická, v takovém případě může přistupovat pouze ke statickým datovým členům třídy (a *nemá žádný ukazatel* ). Další informace naleznete v tématu [static data Members](../cpp/static-members-cpp.md).

## <a name="special-member-functions"></a>Zvláštní členské funkce

Speciální členské funkce jsou funkce, které kompilátor poskytuje automaticky, pokud je neurčíte ve zdrojovém kódu.

1. Výchozí konstruktor

1. Kopírovací konstruktor

1. **(C++ 11)** Přesunout konstruktor

1. Operátor přiřazení pro kopírování

1. **(C++ 11)** Operátor přiřazení přesunutí

1. Destruktor

Další informace najdete v tématu [zvláštní členské funkce](../cpp/special-member-functions.md).

## <a name="memberwise-initialization"></a>Inicializace kopírování členů

V jazyce C++ 11 a novějším může nestatický člen deklarátory obsahovat inicializátory.

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

Pokud je členovi přiřazena hodnota v konstruktoru, tato hodnota přepíše hodnotu, se kterou byl člen inicializován v bodě deklarace.

Existuje pouze jedna kopie sdílených statických datových členů pro všechny objekty typu dané třídy. Statické datové členy musejí být definovány a mohou být inicializovány v rozsahu souboru. (Další informace o statických datových členech naleznete v tématu [static data Members](../cpp/static-members-cpp.md).) Následující příklad ukazuje, jak provést tyto inicializace:

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
>  Název třídy `CanInit2` musí předcházet identifikátor `i`, čímž určíte, že definovaný identifikátor `i` je členem třídy `CanInit2`.

## <a name="see-also"></a>Viz také

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)
