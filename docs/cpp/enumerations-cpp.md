---
title: "Výčty (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96b1b29baaa779fda1e1f076daf3d8bd9335403b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="enumerations-c"></a>Výčty (C++)
Výčet je typ definovaný uživatelem, který se skládá z sadu s názvem celočíselné konstanty, které jsou známé jako výčty.  
  
> [!NOTE]
>  Tento článek se zabývá jazyk C++ Standard ISO `enum` typu a oboru (nebo silného typu) `enum class` typ, který byl představen v C ++ 11. Informace o `public enum class` nebo `private enum class` typy v jazyce C + +/ CLI a C + +/ CX, najdete v části [výčet tříd](../windows/enum-class-cpp-component-extensions.md).  
  
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
  
```  
// Forward declaration of enumerations  (C++11):  
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```  
  
## <a name="parameters"></a>Parametry  
 `identifier`  
 Název typu výčtu zadané.  
  
 `type`  
 Základní typ výčty; všechny výčty mít stejného základního typu. Může být jakéhokoli typu integrální.  
  
 `enum-list`  
 Čárkami oddělený seznam výčty ve výčtu. Každý enumerátor nebo název proměnné v oboru musí být jedinečný. Však mohou být duplicitní hodnoty. V bez ohledu na obor výčtu rozsah je oboru okolního; v oboru výčtu, rozsah je `enum-list` sám sebe.  V oboru výčtu seznamu může být prázdná nový typ integrální určující platí.
  
 `class`  
 Pomocí této – klíčové slovo v deklaraci zadáte je výčet má obor a `identifier` musí být zadán. Můžete také `struct` – klíčové slovo místě `class`, protože se jedná o sémanticky ekvivalentní v tomto kontextu.  
  
## <a name="enumerator-scope"></a>Enumerátor oboru  
 Výčet poskytuje kontext k popisu rozsahu hodnot, které jsou reprezentovány jako pojmenované konstanty a jsou také označovány jako výčty. V původní C a C++ typy výčtu jsou viditelné v rámci rozsahu, ve které je výčet deklarována nekvalifikované výčty. V oboru výčty název enumerátor musí být kvalifikovaný název typu výčtu. Následující příklad ukazuje tento základní rozdíl mezi dva druhy výčty:  
  
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
  
 Každý název ve výčtu je přiřazen integrální hodnota, která odpovídá jeho místo v pořadí podle hodnot ve výčtu. Ve výchozím nastavení první hodnota je přiřazena 0, další jeden je přiřazen 1 a tak dále, ale můžete explicitně nastavit hodnotu čítače, jak je vidět tady:  
  
```cpp  
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };  
  
```  
  
 Enumerátor `Diamonds` je přiřazena hodnota `1`. Další výčty, pokud nejsou uvedeny explicitní hodnotu, zobrazí hodnota předchozí enumerátor plus jedna. V předchozím příkladu `Hearts` by měla hodnotu 2, `Clubs` by obsahovat 3 a tak dále.  
  
 Všechny čítače se považuje za konstanta a musí mít jedinečný název v rámci oboru kde `enum` (pro bez ohledu na obor výčty), není definována v rámci samotné výčtu (pro vymezená výčty). Hodnoty zadané názvy nemusí být jedinečný. Například pokud deklaraci bez ohledu na obor výčtu `Suit` je toto:  
  
```cpp  
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };  
```  
  
 Potom hodnoty `Diamonds`, `Hearts`, `Clubs`, a `Spades` jsou 5, 6, 4 a 5, v uvedeném pořadí. Všimněte si, že 5 se používá více než jednou; To je povoleno, i když nemusí být žádoucí. Tato pravidla jsou stejné pro vymezená výčty.  
  
 ## <a name="casting-rules"></a>Přetypování pravidla  
  
 Konstanty výčtu bez ohledu na obor může být implicitně převedena na `int`, ale `int` se nikdy implicitně převést na hodnotu výčtu. Následující příklad ukazuje, co se stane, pokud se pokusíte přiřadit `hand` hodnotu, která není `Suit`:  
  
```cpp  
int account_num = 135692;  
Suit hand;  
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'  
  
```  
  
 Přetypování je požadované pro převod `int` do oboru nebo bez ohledu na obor enumerátor. Však může zvýšit úroveň bez ohledu na obor enumerátor na celočíselnou hodnotu bez přetypování.  
  
```cpp  
int account_num = Hearts; //OK if Hearts is in a unscoped enum  
```  
  
 Použití implicitní převody tímto způsobem může vést k neočekávaným vedlejší účinky. Chcete-li vyloučit programovací chyby související s bez ohledu na obor výčty, jsou hodnoty oboru výčtu silného typu. Výčty oboru musí být kvalifikovaný název typu výčtu (identifier) a nelze implicitně převést, jak je znázorněno v následujícím příkladu:  
  
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
  
 Všimněte si, že na řádku `hand = account_num;` stále způsobuje chybu, která se vyskytuje v bez ohledu na obor výčty, jako je uvedené výše. Je povolená s explicitní přetypování. Avšak v případě oboru výčty, pokus o převodu příkazu Další `account_num = Suit::Hearts;`, již není povoleno bez explicitní přetypování. 

## <a name="enums-with-no-enumerators"></a>Výčty pomocí žádné výčty
**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): definováním výčet (regulární nebo oboru) s explicitní základní typ a žádné výčty lze v platnosti zavádět nové integrální typu nemá žádné implicitní převod na jiný typ. Pomocí tohoto typu místo jeho předdefinovaný základní typ, můžete eliminovat potenciální jemně chyby způsobené nechtěnému implicitní převody.  


```cpp
enum class byte : unsigned char { };
```

Nový typ je přesnou kopii základní typ a proto má stejné konvence volání, což znamená, že ho můžete používat napříč bis bez jakékoli snížení výkonu. Při proměnné typu se inicializují pomocí seznamu přímo inicializace, je potřeba žádné přetypování. Následující příklad ukazuje, jak k chybě při inicializaci výčty pomocí žádné výčty v různých kontextech:

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
 [Deklarace výčtů C](../c-language/c-enumeration-declarations.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)