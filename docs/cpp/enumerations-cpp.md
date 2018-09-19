---
title: Výčty (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/01/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- enum_cpp
dev_langs:
- C++
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35aa004a2c4f47c476175ac500777ee8eb6efb07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028750"
---
# <a name="enumerations-c"></a>Výčty (C++)

Výčet je uživatelem definovaný typ, který se skládá z sadu pojmenovaných integrálních konstant nazývaných enumerátory.

> [!NOTE]
>  Tento článek se týká jazyka C++ podle standardu ISO **výčtu** typu a rozsahu (nebo silný) **výčet tříd** typ, který je uveden v C ++ 11. Informace o **veřejný výčet tříd** nebo **soukromý výčet tříd** typy v jazyce C + +/ CLI a C + +/ CX, naleznete v tématu [výčet tříd](../windows/enum-class-cpp-component-extensions.md).

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

*identifikátor*<br/>
Název typu daný pro výčet.

*Typ*<br/>
Základní typ čítačů; všechny čítače mají stejný základní typ. Může být libovolný integrální typ.

*seznam výčtu*<br/>
Čárkami oddělený seznam čítačů ve výčtu. Všechny čítače výčtu nebo název proměnné v oboru musí být jedinečný. Však mohou být duplicitní hodnoty. Ve výčtu mimo rozsah je rozsah obklopujícím rozsahem; ve výčtovém rozsahu je *seznam výčtu* samotný.  V rozsahu výčtového typu seznamu může být prázdný určující platit nový integrálního typu.

*class*<br/>
Pomocí tohoto klíčového slova v deklaraci zadáte obor výčtu a objekt *identifikátor* musí být zadaná. Můžete také použít **struktura** – klíčové slovo místo **třída**, jako jsou sémanticky rovnocenné v tomto kontextu.

## <a name="enumerator-scope"></a>Čítač rozsahu

Výčet poskytuje kontext k popisu rozsahu hodnot, které jsou reprezentovány jako pojmenované konstanty a se také nazývají enumerátory. V původní C a C++ typy výčtu jsou nekvalifikované enumerátory viditelné v celém oboru, ve kterém je tento výčet deklarován. V rámci oboru výčtů musí být název enumerátoru kvalifikován názvem typu výčtu. Následující příklad ukazuje tento základní rozdíl mezi dvěma druhy výčtů:

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

Každému názvu ve výčtu je přiřazena celočíselná hodnota odpovídající jeho umístění v pořadí hodnot ve výčtu. Ve výchozím nastavení první hodnotě přiřazena 0, další je přiřazena 1 a tak dále, ale můžete explicitně nastavit hodnotu čítače, jak je znázorněno zde:

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

Enumerátor `Diamonds` je přiřazena hodnota `1`. Následující čítače, pokud jim není uvedena explicitní hodnota, získávají hodnotu z předchozího výčtu navýšenou o jeden. V předchozím příkladu `Hearts` by měla hodnotu 2, `Clubs` by obsahovat 3 a tak dále.

Každý výčet je považován za konstantu a musí mít jedinečný název v rámci oboru kde **výčtu** definován (pro výčty bez oboru) nebo v rámci **výčtu** samotného (pro výčty v oboru). Hodnoty, použité pro názvy nemusí být jedinečný. Například pokud deklarace výčtu mimo obor `Suit` je toto:

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

Potom hodnoty `Diamonds`, `Hearts`, `Clubs`, a `Spades` jsou 5, 6, 4 a 5 v uvedeném pořadí. Všimněte si, že 5 je použita více než jednou; To je povoleno, i když nemusí být žádoucí. Tato pravidla jsou stejná pro výčty.

## <a name="casting-rules"></a>Pravidla přetypování

Konstanty typu nevymezeného výčtu lze implicitně převést na **int**, ale **int** není nikdy implicitně převést na hodnotu výčtu. Následující příklad ukazuje, co se stane, pokud se pokusíte přiřadit `hand` hodnotu, která není `Suit`:

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

Přetypování vyžaduje převedení **int** do oboru nebo typu nevymezeného výčtu. Můžete však povýšit čítač mimo obor na celočíselnou hodnotu bez přetypování.

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

Použití implicitních převodů tímto způsobem může způsobit nežádoucí vedlejší účinky. Chcete-li vyloučit programové chyby související s výčty bez oboru, jsou hodnoty výčtu s oborem psané tučně. Čítače v oboru musí být kvalifikován názvem typu výčtu (identifikátor) a nejde implicitně převést, jak je znázorněno v následujícím příkladu:

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
```

Všimněte si, že na řádku `hand = account_num;` stále způsobuje chybu, ke které dochází u výčtů bez oboru, jak je uvedeno výše. Je povoleno s explicitním přetypováním. Nicméně s oborem výčtů pokus o převod do dalšího příkazu `account_num = Suit::Hearts;`, již není povolen bez explicitního přetypování.

## <a name="no_enumerators"></a> Výčty pomocí žádné čítače

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): definuje výčet (pravidelných nebo s vymezeným oborem) s explicitní nadřazeného typu a žádné čítače, můžete platit zavést nový celočíselný typ, který nemá implicitní převod do jakéhokoli jiného typu. Pomocí tohoto typu namísto integrovaných základního typu může eliminovat riziko drobné chyby způsobené zvyšuje ochranu před nechtěnými implicitní převody.


```cpp
enum class byte : unsigned char { };
```

Nový typ je přesnou kopii základní typ a proto má stejnou volací konvenci, což znamená, že je možné použít napříč instrukce ABI bez žádné snížení výkonu. Nepoužívat přetypování je potřeba při proměnné typu jsou inicializovány pomocí seznamu přímé inicializaci. Následující příklad ukazuje způsob inicializace výčty pomocí žádné čítače v různých kontextech:

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

## <a name="see-also"></a>Viz také:

[Deklarace výčtů v jazyce C](../c-language/c-enumeration-declarations.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)