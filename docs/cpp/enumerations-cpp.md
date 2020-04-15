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
ms.openlocfilehash: 2a1b3d33534887568c6a55e320e77e0a018cafff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366326"
---
# <a name="enumerations-c"></a>Výčty (C++)

Výčet je uživatelem definovaný typ, který se skládá ze sady pojmenovaných integrálních konstant, které jsou označovány jako čítače výčtu.

> [!NOTE]
> Tento článek popisuje typ **výčtu** jazyka STANDARD Standard C++ a typ **třídy výčtu** s vymezeným oborem (nebo silně typovaný), který je zaveden v jazyce C++11. Informace o **veřejné výčtu třídy** nebo soukromé typy **tříd výčtu** v C++/CLI a C++/CX, naleznete [v tématu výčtu třídy](../extensions/enum-class-cpp-component-extensions.md).

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

*Identifikátor*<br/>
Název typu daný výčtu.

*Typ*<br/>
Základní typ čítačů výčtu; všechny čítače výčtu mají stejný základní typ. Může být jakýkoli integrální typ.

*výčet-list*<br/>
Seznam výčtů oddělených čárkami ve výčtu. Každý název čítače nebo proměnné v oboru musí být jedinečný. Hodnoty však mohou být duplikovány. Ve výčtu bez oboru je obor okolní obor; ve výčtu s vymezeným oborem, obor je *samotný výčet.*  Ve výčtu s vymezeným oborem může být seznam prázdný, což ve skutečnosti definuje nový integrální typ.

*třída*<br/>
Pomocí tohoto klíčového slova v deklaraci zadáte výčtu je vymezena a *identifikátor* musí být poskytnuta. Můžete také použít **klávesu struct** místo **třídy**, protože jsou sémanticky ekvivalentní v tomto kontextu.

## <a name="enumerator-scope"></a>Obor výčtu

Výčet poskytuje kontext k popisu rozsah hodnot, které jsou reprezentovány jako pojmenované konstanty a jsou také nazývány čítače výčtu. V původní c a c++ výčtu typy neúplných výčtů jsou viditelné v celém oboru, ve kterém je deklarována výčtu. V oborech výčty výčtu název čítače musí být kvalifikován název typu výčtu. Následující příklad ukazuje tento základní rozdíl mezi dvěma druhy výčtů:

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

Každému názvu ve výčtu je přiřazena integrální hodnota, která odpovídá jeho místo v pořadí hodnot ve výčtu. Ve výchozím nastavení je první hodnota přiřazena 0, další je přiřazena 1 a tak dále, ale můžete explicitně nastavit hodnotu čítače výčtu, jak je znázorněno zde:

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

Čítač `Diamonds` je přiřazena `1`hodnota . Následné čítače výčtu, pokud nejsou uvedeny explicitní hodnotu, obdrží hodnotu předchozího čítače výčtu plus jeden. V předchozím příkladu `Hearts` by měl `Clubs` hodnotu 2, by 3 a tak dále.

Každý čítač výčtu je považován za konstantu a musí mít jedinečný název v rámci oboru, kde je definován **výčtu** (pro výčty bez oboru) nebo v rámci **výčtu** samotného (pro vymezené výčty). Hodnoty dané názvy nemusí být jedinečné. Například pokud deklarace výčtu neoboru `Suit` je toto:

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

Potom hodnoty `Diamonds`, `Hearts` `Clubs`, `Spades` a jsou 5, 6, 4 a 5, v uvedeném pořadí. Všimněte si, že 5 se používá více než jednou; to je povoleno, i když to nemusí být zamýšleno. Tato pravidla jsou stejná pro vymezené obory.

## <a name="casting-rules"></a>Pravidla odlévání

Konstanty výčtu bez oboru lze implicitně převést na **int**, ale **int** je nikdy implicitně převoditelný na hodnotu výčtu. Následující příklad ukazuje, co se `hand` stane, pokud se `Suit`pokusíte přiřadit hodnotu, která není :

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

Přetypová nit je nutné převést **int** na obornebo neoboru čítač výčtu. Můžete však povýšit neoboru čítač výčtu na hodnotu celé číslo bez přetypádnení.

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

Použití implicitní převody tímto způsobem může vést k nežádoucí vedlejší účinky. Chcete-li odstranit chyby programování spojené s unscoped výčty, rozsahem výčtu hodnoty jsou silně zadali. Výčty s rozsahem musí být kvalifikovány názvem typu výčtu (identifikátor) a nelze je implicitně převést, jak je znázorněno v následujícím příkladu:

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

Všimněte si, že řádek `hand = account_num;` stále způsobuje chybu, ke které dochází s unscoped výčty, jak je uvedeno výše. Je povoleno s explicitní obsazení. Však s rozsahem výčty, pokus o převod `account_num = Suit::Hearts;`v dalším příkazu , již není povoleno bez explicitní přetypované.

## <a name="enums-with-no-enumerators"></a><a name="no_enumerators"></a>Výčty bez čítačů

**Visual Studio 2017 verze 15.3 a novější** (k dispozici s [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Definováním výčtu (pravidelné nebo s vymezeným oborem) s explicitní základní typ a žádné výčtu, můžete ve skutečnosti zavést nový integrální typ, který nemá žádný implicitní převod na jiný typ. Pomocí tohoto typu namísto jeho vestavěné základní typ, můžete eliminovat potenciál pro drobné chyby způsobené neúmyslné implicitní převody.

```cpp
enum class byte : unsigned char { };
```

Nový typ je přesná kopie základnítyp a proto má stejné konvence volání, což znamená, že lze použít v rámci ABU bez snížení výkonu. Žádné přetypování je vyžadováno, pokud jsou proměnné typu inicializovány pomocí inicializace přímého seznamu. Následující příklad ukazuje, jak inicializovat výčty bez čítačů výčtů v různých kontextech:

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

[C Prohlášení o výčtu](../c-language/c-enumeration-declarations.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
