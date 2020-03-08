---
title: Výčty (C++)
ms.date: 06/01/2018
f1_keywords:
- enum_cpp
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
ms.openlocfilehash: caec9ea7ac5482ff23b73676a3fd7b3d25ad293f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884148"
---
# <a name="enumerations-c"></a>Výčty (C++)

Výčet je uživatelsky definovaný typ, který se skládá ze sady pojmenovaných integrálních konstant, které jsou známé jako enumerátory.

> [!NOTE]
>  Tento článek popisuje typ **výčtu** standard C++ jazyka ISO a typ **třídy výčtu** s oborem (nebo silně typované), který je představený v c++ 11. Informace o **veřejné třídě výčtu** nebo typech **tříd typu Private enum** v C++/CLI a C++/CX naleznete v tématu [enum class](../extensions/enum-class-cpp-component-extensions.md).

## <a name="syntax"></a>Syntaxe

```
// unscoped enum:
enum [identifier] [: type]
{enum-list};

// scoped enum:
enum [class|struct]
[identifier] [: type]
{enum-list};
```

```cpp
// Forward declaration of enumerations  (C++11):
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```

## <a name="parameters"></a>Parametry

*RID*<br/>
Název typu předaný výčtu.

*type*<br/>
Základní typ enumerátorů; všechny enumerátory mají stejný základní typ. Může být libovolný integrální typ.

*výčet – seznam*<br/>
Čárkami oddělený seznam enumerátorů ve výčtu. Každý název enumerátoru nebo proměnné v oboru musí být jedinečný. Hodnoty však mohou být duplikovány. V nevymezeném výčtu je rozsah okolním oborem; v oboru výčtu je oborem samotný *seznam výčtu* .  V oboru výčtu může být seznam prázdný, což v důsledku toho definuje nový integrální typ.

*class*<br/>
Pomocí tohoto klíčového slova v deklaraci zadáte rozsah výčtu a je nutné zadat *identifikátor* . Klíčové slovo **struct** můžete také použít místo **třídy**, protože jsou sémanticky ekvivalentní v tomto kontextu.

## <a name="enumerator-scope"></a>Rozsah enumerátoru

Výčet poskytuje kontext pro popis rozsahu hodnot, které jsou reprezentovány jako pojmenované konstanty a jsou označovány také jako enumerátory. V původních typech C a C++ enum jsou nekvalifikované výčty viditelné v rámci oboru, ve kterém je výčet deklarován. V oboru výčtů musí být název enumerátoru kvalifikován názvem typu výčtu. Následující příklad ukazuje tento základní rozdíl mezi dvěma druhy výčtů:

```cpp
namespace CardGame_Scoped
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Suit::Clubs) // Enumerator must be qualified by enum type
        { /*...*/}
    }
}

namespace CardGame_NonScoped
{
    enum Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Clubs) // Enumerator is visible without qualification
        { /*...*/
        }
    }
}
```

Každému názvu ve výčtu je přiřazena celočíselná hodnota odpovídající jeho umístění v pořadí hodnot ve výčtu. Ve výchozím nastavení je první hodnota přiřazena 0, další je přiřazena 1 a tak dále, ale můžete explicitně nastavit hodnotu čítače výčtu, jak je znázorněno zde:

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

`Diamonds` výčtu je přiřazena hodnota `1`. Další enumerátory, pokud nemají přiřazenou explicitní hodnotu, obdrží hodnotu předchozího výčtu plus jedna. V předchozím příkladu má `Hearts` hodnotu 2, `Clubs` by měla být 3 atd.

Každý enumerátor je považován za konstantu a musí mít jedinečný název v rámci oboru, ve kterém je definován **výčet** (pro výčty bez oboru) nebo v rámci samotného **výčtu** (pro vymezené výčty). Hodnoty zadané pro názvy nemusí být jedinečné. Například pokud deklarace výčtu bez oboru `Suit` je tato:

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

Hodnoty `Diamonds`, `Hearts`, `Clubs`a `Spades` jsou tedy 5, 6, 4 a 5 v uvedeném pořadí. Všimněte si, že 5 se používá více než jednou; Tato možnost je povolená, i když nemusí být zamýšlená. Tato pravidla jsou stejná pro vymezené výčty.

## <a name="casting-rules"></a>Pravidla přetypování

Konstanty výčtu bez oboru lze implicitně převést na typ **int**, ale hodnota **int** není nikdy implicitně převoditelná na hodnotu výčtu. Následující příklad ukazuje, co se stane, když se pokusíte přiřadit `hand` hodnotu, která není `Suit`:

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

K převodu **int** na rozsah nebo nevymezený enumerátor se vyžaduje přetypování. Můžete ale zvýšit úroveň výčtu bez oboru na celočíselnou hodnotu bez přetypování.

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

Použití implicitních převodů tímto způsobem může vést k nezamýšleným vedlejším účinkům. Chcete-li zabránit chybám při programování přidružených k výčtům bez oboru, jsou typově silné hodnoty výčtu silně typované. Enumerátory vymezené oborem musí být kvalifikovány názvem typu výčtu (identifikátor) a nelze je implicitně převést, jak je znázorněno v následujícím příkladu:

```cpp
namespace ScopedEnumConversions
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void AttemptConversions()
    {
        Suit hand;
        hand = Clubs; // error C2065: 'Clubs' : undeclared identifier
        hand = Suit::Clubs; //Correct.
        int account_num = 135692;
        hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
        hand = static_cast<Suit>(account_num); // OK, but probably a bug!!!

        account_num = Suit::Hearts; // error C2440: '=' : cannot convert from 'Suit' to 'int'
        account_num = static_cast<int>(Suit::Hearts); // OK
    }
}
```

Všimněte si, že řádek `hand = account_num;` stále způsobuje chybu, ke které dochází v rámci výčtů bez oboru, jak je uvedeno výše. Je povolená s explicitním přetypováním. Nicméně s vymezenými výčty, pokus o převod v dalším příkazu `account_num = Suit::Hearts;`, již není povolen bez explicitního přetypování.

## <a name="no_enumerators"></a>Výčty bez enumerátorů

**Visual Studio 2017 verze 15,3 a novější** (k dispozici s [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): definováním výčtu (pravidelný nebo vymezený) pomocí explicitního základního typu a žádného enumerátoru v tomto efektu můžete zavést nový integrální typ, který nemá implicitní převod na žádný jiný typ. Pomocí tohoto typu namísto předdefinovaného základního typu můžete eliminovat potenciál drobných chyb způsobených neúmyslnými implicitními převody.

```cpp
enum class byte : unsigned char { };
```

Nový typ je přesná kopie základního typu, a proto má stejnou konvenci volání, což znamená, že se dá použít napříč instrukce ABI bez jakékoliv penalizace výkonu. Pokud jsou proměnné typu inicializovány pomocí inicializace přímého seznamu, není vyžadováno žádné přetypování. Následující příklad ukazuje, jak inicializovat výčty bez enumerátorů v různých kontextech:

```cpp
enum class byte : unsigned char { };

enum class E : int { };
E e1{ 0 };
E e2 = E{ 0 };

struct X
{
    E e{ 0 };
    X() : e{ 0 } { }
};

E* p = new E{ 0 };

void f(E e) {};

int main()
{
    f(E{ 0 });
    byte i{ 42 };
    byte j = byte{ 42 };

    // unsigned char c = j; // C2440: 'initializing': cannot convert from 'byte' to 'unsigned char'
    return 0;
}
```

## <a name="see-also"></a>Viz také

[Deklarace výčtů v jazyce C](../c-language/c-enumeration-declarations.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)