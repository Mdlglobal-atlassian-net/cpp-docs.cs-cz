---
title: Přehled členů třídy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fa736315554786435ec8a8eca453df9de79e2bd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033898"
---
# <a name="class-member-overview"></a>Přehled členů třídy

Třídy nebo struktury se skládá z jejích členů. Práce, která nemá třídu provádí její členské funkce. Stav, který uchovává je uložen v její datové členy. Inicializace členů se provádí tak, že konstruktory a vyčištění práce, jako je například uvolnění paměti a uvolnění prostředků provádí destruktory. V C ++ 11 a novějším datové členy můžete (a obvykle by měl) inicializovat v bodě deklarace.

## <a name="kinds-of-class-members"></a>Typy členů třídy.

Úplný seznam kategorií člen vypadá takto:

- [Speciální členské funkce](special-member-functions.md).

- [Přehled členských funkcí](overview-of-member-functions.md).

- [Datové členy](static-members-cpp.md) včetně předdefinovaných typů a jiným uživatelem definované typy.

- Operátory

- [Deklarace vnořených tříd](nested-class-declarations.md) a.)

- [Sjednocení](unions.md)

- [Výčty](../cpp/enumerations-cpp.md).

- [Bitová pole](../cpp/cpp-bit-fields.md).

- [Přátelé](../cpp/friend-cpp.md).

- [Aliasy a definice TypeDef](../cpp/aliases-and-typedefs-cpp.md).

    > [!NOTE]
    >  Přátelé jsou zahrnuty v předchozím seznamu, protože jsou obsaženy v deklaraci třídy. Nejsou však skutečnými členy třídy, protože nejsou v oboru třídy.

## <a name="example-class-declaration"></a>Příklad deklarace třídy

Následující příklad ukazuje deklaraci třídy jednoduchý:

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

## <a name="member-accessibility"></a>Usnadnění přístupu člena

Členy třídy jsou deklarovány v seznamu členů. Seznam členů třídy může být rozdělen do libovolného počtu **privátní**, **chráněné** a **veřejné** oddíly, použití klíčových slov známá jako specifikátory přístupu.  Dvojtečka **:** musí následovat specifikátor přístupu.  Tyto části nemusejí být souvislé, to znamená, že některé z těchto klíčových slov se mohou v seznamu členů objevit několikrát.  Klíčové slovo určuje přístup všech členů, dokud se neobjeví další specifikátor přístupu nebo uzavírací složená závorka. Další informace najdete v tématu [ovládací prvek přístupu členů (C++)](../cpp/member-access-control-cpp.md).

## <a name="static-members"></a>Statické členy

Datový člen mohou být deklarovány jako statická, což znamená, že všechny objekty třídy mají přístup na stejnou kopii. Členské funkce mohou být deklarovány jako statická, v takovém případě může pouze přistupovat k statické datové členy třídy (a nemá žádné *to* ukazatele). Další informace najdete v tématu [statické datové členy](../cpp/static-members-cpp.md).

## <a name="special-member-functions"></a>Speciální členské funkce

Speciální členské funkce jsou funkce, které jsou automaticky poskytován kompilátorem, pokud není zadáno ve zdrojovém kódu.

1. Výchozí konstruktor

1. Kopírovací konstruktor

1. **(C ++ 11)**  Konstruktoru přesunu

1. Operátor přiřazení kopie

1. **(C ++ 11)**  Operátor přiřazení přesunutí

1. Destruktor

Další informace najdete v tématu [speciálních členských funkcí](../cpp/special-member-functions.md).

## <a name="memberwise-initialization"></a>Inicializace související se členy

V C ++ 11 a novějším nestatická členská deklarátory mohou obsahovat inicializátory.

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

Pokud člen není přiřazena hodnota v konstruktoru, tato hodnota přepíše hodnotu, se kterým byl člen inicializovat v bodě deklarace.

Existuje pouze jedna kopie sdílených statických datových členů pro všechny objekty typu dané třídy. Statické datové členy musejí být definovány a mohou být inicializovány v rozsahu souboru. (Další informace o statických datových členech naleznete v tématu [statické datové členy](../cpp/static-members-cpp.md).) Následující příklad ukazuje, jak provést tyto inicializace:

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

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)