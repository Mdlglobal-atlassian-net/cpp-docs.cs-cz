---
title: basic_string – třída
ms.date: 11/12/2019
f1_keywords:
- xstring/std::basic_string
- xstring/std::basic_string::allocator_type
- xstring/std::basic_string::const_iterator
- xstring/std::basic_string::const_pointer
- xstring/std::basic_string::const_reference
- xstring/std::basic_string::const_reverse_iterator
- xstring/std::basic_string::difference_type
- xstring/std::basic_string::iterator
- xstring/std::basic_string::npos
- xstring/std::basic_string::pointer
- xstring/std::basic_string::reference
- xstring/std::basic_string::reverse_iterator
- xstring/std::basic_string::size_type
- xstring/std::basic_string::traits_type
- xstring/std::basic_string::value_type
- xstring/std::basic_string::append
- xstring/std::basic_string::assign
- xstring/std::basic_string::at
- xstring/std::basic_string::back
- xstring/std::basic_string::begin
- xstring/std::basic_string::c_str
- xstring/std::basic_string::capacity
- xstring/std::basic_string::cbegin
- xstring/std::basic_string::cend
- xstring/std::basic_string::clear
- xstring/std::basic_string::compare
- xstring/std::basic_string::copy
- xstring/std::basic_string::crbegin
- xstring/std::basic_string::crend
- xstring/std::basic_string::_Copy_s
- xstring/std::basic_string::data
- xstring/std::basic_string::empty
- xstring/std::basic_string::end
- xstring/std::basic_string::erase
- xstring/std::basic_string::find
- xstring/std::basic_string::find_first_not_of
- xstring/std::basic_string::find_first_of
- xstring/std::basic_string::find_last_not_of
- xstring/std::basic_string::find_last_of
- xstring/std::basic_string::front
- xstring/std::basic_string::get_allocator
- xstring/std::basic_string::insert
- xstring/std::basic_string::length
- xstring/std::basic_string::max_size
- xstring/std::basic_string::pop_back
- xstring/std::basic_string::push_back
- xstring/std::basic_string::rbegin
- xstring/std::basic_string::rend
- xstring/std::basic_string::replace
- xstring/std::basic_string::reserve
- xstring/std::basic_string::resize
- xstring/std::basic_string::rfind
- xstring/std::basic_string::shrink_to_fit
- xstring/std::basic_string::size
- xstring/std::basic_string::substr
- xstring/std::basic_string::swap
helpviewer_keywords:
- std::basic_string [C++]
- std::basic_string [C++], allocator_type
- std::basic_string [C++], const_iterator
- std::basic_string [C++], const_pointer
- std::basic_string [C++], const_reference
- std::basic_string [C++], const_reverse_iterator
- std::basic_string [C++], difference_type
- std::basic_string [C++], iterator
- std::basic_string [C++], npos
- std::basic_string [C++], pointer
- std::basic_string [C++], reference
- std::basic_string [C++], reverse_iterator
- std::basic_string [C++], size_type
- std::basic_string [C++], traits_type
- std::basic_string [C++], value_type
- std::basic_string [C++], append
- std::basic_string [C++], assign
- std::basic_string [C++], at
- std::basic_string [C++], back
- std::basic_string [C++], begin
- std::basic_string [C++], c_str
- std::basic_string [C++], capacity
- std::basic_string [C++], cbegin
- std::basic_string [C++], cend
- std::basic_string [C++], clear
- std::basic_string [C++], compare
- std::basic_string [C++], copy
- std::basic_string [C++], crbegin
- std::basic_string [C++], crend
- std::basic_string [C++], _Copy_s
- std::basic_string [C++], data
- std::basic_string [C++], empty
- std::basic_string [C++], end
- std::basic_string [C++], erase
- std::basic_string [C++], find
- std::basic_string [C++], find_first_not_of
- std::basic_string [C++], find_first_of
- std::basic_string [C++], find_last_not_of
- std::basic_string [C++], find_last_of
- std::basic_string [C++], front
- std::basic_string [C++], get_allocator
- std::basic_string [C++], insert
- std::basic_string [C++], length
- std::basic_string [C++], max_size
- std::basic_string [C++], pop_back
- std::basic_string [C++], push_back
- std::basic_string [C++], rbegin
- std::basic_string [C++], rend
- std::basic_string [C++], replace
- std::basic_string [C++], reserve
- std::basic_string [C++], resize
- std::basic_string [C++], rfind
- std::basic_string [C++], shrink_to_fit
- std::basic_string [C++], size
- std::basic_string [C++], substr
- std::basic_string [C++], swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 0aca4e8b8a446eb773f6ba4efaeb4a0a6c9644af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376724"
---
# <a name="basic_string-class"></a>basic_string – třída

Sekvence řízené objektem typu `basic_string` jsou třídy řetězce Standard C++ a jsou obvykle označovány jako řetězce, ale neměly by být zaměňovány s řetězci s nulovým ukončeným stylem C používanými v celé standardní knihovně jazyka C++. Standardní řetězec C++ je kontejner, který umožňuje použití řetězců jako normální typy, jako jsou například operace porovnání a zřetězení, iterátory, algoritmy standardní knihovny C++ a kopírování a přiřazování se spravovanou pamětí alokátoru třídy. Pokud potřebujete převést řetězec Standard C++ na řetězec s nulovým ukončeným stylem Jazyka C, použijte člen [basic_string::c_str.](#c_str)

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_string;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Datový typ jednoho znaku, který má být uložen v řetězci. Standardní knihovna jazyka C++ poskytuje specializace této šablony třídy s [řetězcem](../standard-library/string-typedefs.md#string) definice typů pro prvky typu `char16_t` **char**, [wstring](../standard-library/string-typedefs.md#wstring), pro **wchar_t**, [u16string](../standard-library/string-typedefs.md#u16string) for a [u32string](../standard-library/string-typedefs.md#u32string) for `char32_t`.

*Vlastnosti*\
Různé důležité vlastnosti `CharType` prvků v basic_string specializaci jsou `Traits`popsány třídou . Výchozí hodnota `char_traits` <  `CharType` je>.

*Přidělování*\
Typ, který představuje uložený objekt přidělování, který zapouzdřuje podrobnosti o přidělení řetězce a přidělení paměti. Výchozí hodnota je **alokátor** <  `CharType`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_string](#basic_string)|Vytvoří řetězec, který je prázdný nebo inicializován určitými znaky nebo který je kopií celého nebo části jiného objektu řetězce nebo řetězce C.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ, který `allocator` představuje třídu pro objekt řetězce.|
|[const_iterator](#const_iterator)|Typ, který poskytuje iterátor s náhodným přístupem, který může přistupovat a číst **prvek const** v řetězci.|
|[const_pointer](#const_pointer)|Typ, který poskytuje ukazatel na **const** prvek v řetězci.|
|[const_reference](#const_reference)|Typ, který poskytuje odkaz na **const** prvek uložený v řetězci pro čtení a provádění **const** operací.|
|[const_reverse_iterator](#const_reverse_iterator)|Typ, který poskytuje iterátor náhodného přístupu, který může číst libovolný **prvek const** v řetězci.|
|[difference_type](#difference_type)|Typ, který poskytuje rozdíl mezi dvěma iterátory, které odkazují na prvky v rámci stejného řetězce.|
|[Iterace](#iterator)|Typ, který poskytuje iterátor s náhodným přístupem, který může číst nebo upravovat libovolný prvek v řetězci.|
|[npos](#npos)|Nepodepsaná integrální hodnota inicializovaná na -1, která označuje buď "nebyly nalezeny" nebo "všechny zbývající znaky", když se nezdaří vyhledávací funkce.|
|[ukazatel](#pointer)|Typ, který poskytuje ukazatel na element znaku v řetězci nebo poli znaků.|
|[Odkaz](#reference)|Typ, který poskytuje odkaz na prvek uložený v řetězci.|
|[reverse_iterator](#reverse_iterator)|Typ, který poskytuje iterátor s náhodným přístupem, který může číst nebo upravovat prvek v obráceném řetězci.|
|[size_type](#size_type)|Nepodepsaný integrální typ pro počet prvků v řetězci.|
|[traits_type](#traits_type)|Typ pro znakové znaky prvků uložených v řetězci.|
|[value_type](#value_type)|Typ, který představuje typ znaků uložených v řetězci.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Připojit](#append)|Přidá znaky na konec řetězce.|
|[Přiřadit](#assign)|Přiřadí nové hodnoty znaků k obsahu řetězce.|
|[Na](#at)|Vrátí odkaz na prvek v zadaném umístění v řetězci.|
|[Zpět](#back)||
|[Začít](#begin)|Vrátí iterátor adresující první prvek v řetězci.|
|[c_str](#c_str)|Převede obsah řetězce jako řetězec ve stylu C, ukončený nulou.|
|[capacity](#capacity)|Vrátí největší počet prvků, které by mohly být uloženy v řetězci bez zvýšení přidělení paměti řetězce.|
|[cbegin](#cbegin)|Vrátí const iterator adresování první prvek v řetězci.|
|[cend](#cend)|Vrátí const iterátor, který řeší umístění, které následuje poslední prvek v řetězci.|
|[Jasné](#clear)|Vymaže všechny prvky řetězce.|
|[Porovnat](#compare)|Porovná řetězec se zadaným řetězcem k určení, pokud jsou dva řetězce stejné nebo pokud jeden je lexicographically menší než ostatní.|
|[Kopírovat](#copy)|Zkopíruje maximálně zadaný počet znaků z indexované pozice ve zdrojovém řetězci do cílového pole znaků. Zastaralé Místo toho použijte [basic_string::_Copy_s.](#copy_s)|
|[crbegin](#crbegin)|Vrátí const iterator, který řeší první prvek v obráceném řetězci.|
|[crend](#crend)|Vrátí const iterátor, který řeší umístění, které následuje poslední prvek v obráceném řetězci.|
|[_Copy_s](#copy_s)|Zkopíruje maximálně zadaný počet znaků z indexované pozice ve zdrojovém řetězci do cílového pole znaků.|
|[Dat](#data)|Převede obsah řetězce na pole znaků.|
|[empty](#empty)|Testuje, zda řetězec obsahuje znaky.|
|[Konec](#end)|Vrátí iterátor, který řeší umístění, které následuje poslední prvek v řetězci.|
|[Vymazat](#erase)|Odebere prvek nebo rozsah prvků v řetězci ze zadané pozice.|
|[find](#find)|Prohledá řetězec ve směru dopředu pro první výskyt podřetězce, který odpovídá zadané posloupnosti znaků.|
|[find_first_not_of](#find_first_not_of)|Hledá řetězec pro první znak, který není žádný prvek zadaného řetězce.|
|[find_first_of](#find_first_of)|Hledá prostřednictvím řetězce pro první znak, který odpovídá libovolný prvek zadaného řetězce.|
|[find_last_not_of](#find_last_not_of)|Prohledá řetězec pro poslední znak, který není žádný prvek zadaného řetězce.|
|[find_last_of](#find_last_of)|Hledá řetězec pro poslední znak, který je prvek zadaného řetězce.|
|[Přední](#front)|Vrátí odkaz na první prvek v řetězci.|
|[get_allocator](#get_allocator)|Vrátí kopii `allocator` objektu použitého k vytvoření řetězce.|
|[Vložit](#insert)|Vloží prvek nebo počet prvků nebo rozsah prvků do řetězce v zadané pozici.|
|[Délka](#length)|Vrátí aktuální počet prvků v řetězci.|
|[max_size](#max_size)|Vrátí maximální počet znaků, které může řetězec obsahovat.|
|[pop_back](#pop_back)|Vymaže poslední prvek řetězce.|
|[push_back](#push_back)|Přidá prvek na konec řetězce.|
|[rbegin](#rbegin)|Vrátí iterátor prvnímu prvku v obráceném řetězci.|
|[rend](#rend)|Vrátí iterátor, který odkazuje těsně za poslední prvek v obráceném řetězci.|
|[Nahradit](#replace)|Nahradí prvky v řetězci na určené pozici zadanými znaky nebo znaky zkopírovanými z jiných oblastí nebo řetězců nebo řetězců C.|
|[Rezervy](#reserve)|Nastaví kapacitu řetězce na číslo alespoň tak velké jako zadané číslo.|
|[Změnit velikost](#resize)|Určuje novou velikost řetězce, připojení nebo vymazání prvků podle potřeby.|
|[rnajít](#rfind)|Prohledá řetězec v opačném směru pro první výskyt podřetězce, který odpovídá zadané posloupnosti znaků.|
|[shrink_to_fit](#shrink_to_fit)|Zahodí nadbytečnou kapacitu řetězce.|
|[Velikost](#size)|Vrátí aktuální počet prvků v řetězci.|
|[podřízený](#substr)|Zkopíruje podřetězec maximálně některého počtu znaků z řetězce začínajícího od zadané pozice.|
|[Swap](#swap)|Vyměňte obsah dvou řetězců.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor+=](#op_add_eq)|Připojí znaky k řetězci.|
|[operátor =](#op_eq)|Přiřadí nové hodnoty znaků k obsahu řetězce.|
|[operátor&#91;&#93;](#op_at)|Obsahuje odkaz na znak se zadaným indexem v řetězci.|

## <a name="remarks"></a>Poznámky

Pokud je funkce vyzvána ke generování sekvence delší než [max_size](#max_size) prvky, funkce hlásí chybu délky vyvoláním objektu typu [length_error](../standard-library/length-error-class.md).

Odkazy, ukazatele a iterátory, které označují prvky řízené sekvence může stát neplatným po každém volání funkce, která mění řízené sekvence nebo po prvním volání **non-const** členské funkce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<řetězec>

**Obor názvů:** std

## <a name="basic_stringallocator_type"></a><a name="allocator_type"></a>basic_string::allocator_type

Typ, který představuje třídu alokátoru pro objekt řetězce.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `Allocator`parametr šablony .

### <a name="example"></a>Příklad

```cpp
// basic_string_allocator_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="basic_stringappend"></a><a name="append"></a>basic_string::připojit

Přidá znaky na konec řetězce.

```cpp
basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& append(
    size_type count,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& append(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& append(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& append(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Řetězec C, který má být připojen.

*Str*\
Řetězec, jehož znaky mají být připojeny.

*Posun*\
Index části zdrojového řetězce, který poskytuje znaky, které mají být připojeny.

*Počet*\
Počet znaků, které mají být připojeny maximálně ze zdrojového řetězce.

*char_value*\
Hodnota znaku, který má být připojen.

*První*\
Vstupní iterátor adresování první prvek v oblasti, které mají být připojeny.

*Poslední*\
Vstupní iterátor, const_pointer nebo const_iterator adresování pozice jednoho za poslední prvek v rozsahu, který má být připojen.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt řetězce, který je připojen se znaky předanými členovou funkcí.

### <a name="remarks"></a>Poznámky

Znaky mohou být připojeny k řetězci pomocí [operátor+=](#op_add_eq) nebo členské funkce `append` nebo [push_back](#push_back). `operator+=`připojí hodnoty jednoho argumentu, zatímco `append` členská funkce s více argumenty umožňuje zadat určitou část řetězce pro přidání.

### <a name="example"></a>Příklad

```cpp
// basic_string_append.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a C-string to a string
   string str1a ( "Hello " );
   cout << "The original string str1 is: " << str1a << endl;
   const char *cstr1a = "Out There ";
   cout << "The C-string cstr1a is: " << cstr1a << endl;
   str1a.append ( cstr1a );
   cout << "Appending the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function
   // appending part of a C-string to a string
   string str1b ( "Hello " );
   cout << "The string str1b is: " << str1b << endl;
   const char *cstr1b = "Out There ";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.append ( cstr1b , 3 );
   cout << "Appending the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function
   // appending part of one string to another
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.append ( str2c , 5 , 5 );
   cout << "The appended string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World " );
   cout << "The  string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;

   // The fifth member function
   // appending characters to a string
   string str1e ( "Hello " );
   str1e.append ( 4 , '!' );
   cout << "The string str1 appended with exclamations is: "
        << str1e << endl << endl;

   // The sixth member function
   // appending a range of one string to another
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.append ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The appended string str1 is: "
        << str1f << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The C-string cstr1a is: Out There
Appending the C-string cstr1a to string str1 gives: Hello Out There .

The string str1b is: Hello
The C-string cstr1b is: Out There
Appending the 1st part of the C-string cstr1b to string str1 gives: Hello Out.

The string str2c is: Wide World
The appended string str1 is: Hello World.

The  string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World .

The string str1 appended with exclamations is: Hello !!!!

The string str2f is: Wide World
The appended string str1 is: Hello World.
```

## <a name="basic_stringassign"></a><a name="assign"></a>basic_string::přiřadit

Přiřadí nové hodnoty znaků k obsahu řetězce.

```cpp
basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type off,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& assign(
    size_type count,
    value_type char_value);

template <class InIt>
basic_string<CharType, Traits, Allocator>& assign(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& assign(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& assign(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Ukazatel na znaky řetězce C, které mají být přiřazeny k cílovému řetězci.

*Počet*\
Počet znaků, které mají být přiřazeny, ze zdrojového řetězce.

*Str*\
Zdrojový řetězec, jehož znaky mají být přiřazeny k cílovému řetězci.

*char_value*\
Hodnota znaku, která má být přiřazena.

*První*\
Vstupní iterátor, const_pointer nebo const_iterator adresování první znak v rozsahu zdrojového řetězce, které mají být přiřazeny k cílové oblasti.

*Poslední*\
Vstupní iterátor, const_pointer nebo const_iterator adresování jednoho za poslední znak v rozsahu zdrojového řetězce, který má být přiřazen k cílovéoblasti.

*vypnuto*\
Pozice, na které budou nové znaky přiřazovány.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt řetězce, kterému členská funkce přiřazuje nové znaky.

### <a name="remarks"></a>Poznámky

Řetězce mohou být přiřazeny nové hodnoty znaků. Nová hodnota může být řetězec a řetězec C nebo jeden znak. [Operátor =](#op_eq) může být použit, pokud lze novou hodnotu popsat jediným parametrem; v opačném `assign`případě členská funkce , která má více parametrů, lze určit, která část řetězce má být přiřazena k cílovému řetězci.

### <a name="example"></a>Příklad

```cpp
// basic_string_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning the
   // characters of a C-string to a string
   string str1a;
   const char *cstr1a = "Out There";
   cout << "The C-string cstr1a is: " << cstr1a <<  "." << endl;
   str1a.assign ( cstr1a );
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function assigning a specific
   // number of the of characters a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.assign ( cstr1b , 3 );
   cout << "Assigning the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function assigning a specific number
   // of the characters from one string to another string
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.assign ( str2c , 5 , 5 );
   cout << "The newly assigned string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1d ( "Hello" ), str2d ( "Wide" ), str3d ( "World" );
   cout << "The original string str1 is: " << str1d << "." << endl;
   cout << "The string str2d is: " << str2d << endl;
   str1d.assign ( str2d );
   cout << "The string str1 newly assigned with string str2d is: "
        << str1d << "." << endl;
   cout << "The string str3d is: " << str3d << "." << endl;
   str1d = str3d;
   cout << "The string str1 reassigned with string str3d is: "
        << str1d << "." << endl << endl;

   // The fifth member function assigning a specific
   // number of characters of a certain value to a string
   string str1e ( "Hello " );
   str1e.assign ( 4 , '!' );
   cout << "The string str1 assigned with eclamations is: "
        << str1e << endl << endl;

   // The sixth member function assigning the value from
   // the range of one string to another string
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.assign ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The string str1 assigned a range of string str2f is: "
        << str1f << "." << endl << endl;
}
```

```Output
The C-string cstr1a is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The C-string cstr1b is: Out There
Assigning the 1st part of the C-string cstr1b to string str1 gives: Out.

The string str2c is: Wide World
The newly assigned string str1 is: World.

The original string str1 is: Hello.
The string str2d is: Wide
The string str1 newly assigned with string str2d is: Wide.
The string str3d is: World.
The string str1 reassigned with string str3d is: World.

The string str1 assigned with eclamations is: !!!!

The string str2f is: Wide World
The string str1 assigned a range of string str2f is: World.
```

## <a name="basic_stringat"></a><a name="at"></a>basic_string::at

Obsahuje odkaz na znak se zadaným indexem v řetězci.

```cpp
const_reference at(size_type offset) const;

reference at(size_type offset);
```

### <a name="parameters"></a>Parametry

*Posun*\
Index pozice prvku, na který se má odkazovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na znak řetězce na pozici určené indexem parametru.

### <a name="remarks"></a>Poznámky

První prvek řetězce má index nula a následující prvky jsou postupně indexovány kladným icelovními čísly, takže řetězec length *n* má *n.* prvek indexovaný číslem *n -* 1.

Operátor člena [&#91;&#93;](#op_at) je rychlejší `at` než členské funkce pro poskytování přístupu pro čtení a zápis k prvkům řetězce.

Člen `operator[]` nekontroluje, zda je index předaný jako `at` parametr platný, ale členská funkce ano a proto by měla být použita, pokud platnost není jistá. Neplatný index, který je index menší než nula nebo větší nebo rovna `at` velikosti řetězce, předaný členské funkce vyvolá [výjimku out_of_range Class.](../standard-library/out-of-range-class.md) Neplatný index předán `operator[]` výsledkům v nedefinované chování, ale index rovnající se délce řetězce je platný index pro const řetězce a operátor vrátí znak null při předání tohoto indexu.

Vrácený odkaz může být zrušena přerozdělení řetězce nebo změny pro řetězce bez **const.**

### <a name="example"></a>Příklad

```cpp
// basic_string_at.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string  cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="basic_stringback"></a><a name="back"></a>basic_string::zpět

Vrátí odkaz na poslední prvek v řetězci.

```cpp
const_reference back() const;

reference back();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na poslední prvek řetězce, který musí být neprázdný.

### <a name="remarks"></a>Poznámky

## <a name="basic_stringbasic_string"></a><a name="basic_string"></a>basic_string::basic_string

Vytvoří řetězec, který je prázdný, inicializován určitými znaky nebo je kopií celého řetězce nebo části jiného řetězce nebo řetězce stylu C (ukončený null).

```cpp
basic_string();

explicit basic_string(
    const allocator_type& alloc_type);

basic_string(
    const basic_string& right);

basic_string(
    basic_string&& right);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count = npos);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr,
    size_type count);

basic_string(
    const value_type* ptr,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr);

basic_string(
    const value_type* ptr,
    const allocator_type& alloc_type);

basic_string(
    size_type count,
    value_type char_value);

basic_string(
    size_type count,
    value_type char_value,
    const allocator_type& alloc_type);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last,
    const allocator_type& alloc_type);

basic_string(
    const_pointer first,
    const_pointer last);

basic_string(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Řetězec C, jehož znaky mají být použity k inicializaci `string` právě konstruované. Tato hodnota nemůže být nulový ukazatel.

*alloc_type*\
Třída alokátoru úložiště pro objekt řetězce, který je vytvářen.

*Počet*\
Počet znaků, které mají být inicializovány.

*Právo*\
Řetězec pro inicializaci řetězce, který je konstruován.

*right_offset*\
Index znaku v řetězci, který je první, který se používá k inicializaci hodnot znaků pro řetězec, který je vytvářen.

*char_value*\
Hodnota znaku, která má být zkopírována do řetězce, který je vytvářen.

*První*\
Vstupní iterátor, const_pointer nebo const_iterator adresování první prvek ve zdrojové oblasti, které mají být vloženy.

*Poslední*\
Vstupní iterátor, const_pointer nebo const_iterator adresování pozice jednoho za poslední prvek ve zdrojové oblasti, které mají být vloženy.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt řetězce, který je vytvářen konstruktory.

### <a name="remarks"></a>Poznámky

Všechny konstruktory uložit [basic_string::allocator_type](#allocator_type) a inicializovat řízené sekvence. Alokátor objekt je argument `al`, pokud je k dispozici. Pro konstruktor kopie je `right.` [basic_string::get_allocator](#get_allocator)`()`. V opačném případě je `Alloc()`alokátor .

Řízená sekvence je inicializována na kopii operandské sekvence určené zbývajícími operandy. Konstruktor bez operandsekvence určuje prázdnou počáteční řízenou sekvenci. Pokud `InputIterator` je v konstruktoru šablony typ celého `first,  last` čísla, operandská `(size_type) first, (value_type) last`sekvence se chová stejně jako .

### <a name="example"></a>Příklad

```cpp
// basic_string_ctor.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function initializing with a C-string
   const char *cstr1a = "Hello Out There.";
   basic_string <char> str1a ( cstr1a , 5);
   cout << "The string initialized by C-string cstr1a is: "
        << str1a << "." << endl;

   // The second member function initializing with a string
   string  str2a ( "How Do You Do" );
   basic_string <char> str2b ( str2a , 7 , 7 );
   cout << "The string initialized by part of the string cstr2a is: "
        << str2b << "." << endl;

   // The third member function initializing a string
   // with a number of characters of a specific value
   basic_string <char> str3a ( 5, '9' );
   cout << "The string initialized by five number 9s is: "
        << str3a << endl;

   // The fourth member function creates an empty string
   // and string with a specified allocator
   basic_string <char> str4a;
   string str4b;
   basic_string <char> str4c ( str4b.get_allocator( ) );
   if (str4c.empty ( ) )
      cout << "The string str4c is empty." << endl;
   else
      cout << "The string str4c is not empty." << endl;

   // The fifth member function initializes a string from
   // another range of characters
   string str5a ( "Hello World" );
   basic_string <char> str5b ( str5a.begin ( ) + 5 , str5a.end ( ) );
   cout << "The string initialized by another range is: "
        << str5b << "." << endl;
}
```

## <a name="basic_stringbegin"></a><a name="begin"></a>basic_string::začátek

Vrátí iterátor adresující první prvek v řetězci.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Návratová hodnota

Iterátor náhodného přístupu, který řeší první prvek sekvence nebo těsně za koncem prázdné sekvence.

### <a name="example"></a>Příklad

```cpp
// basic_string_begin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator strp_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.begin ( );
   cout << "The first character of the string str1 is: "
        << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // The dereferenced iterator can be used to modify a character
*str1_Iter = 'G';
   cout << "The first character of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The full modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'g';

   // For an empty string, begin is equivalent to end
   if (  str2.begin ( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The string str2 is not empty." << endl;
}
```

## <a name="basic_stringc_str"></a><a name="c_str"></a>basic_string::c_str

Převede obsah řetězce jako řetězec s nulovým ukončem ve stylu C.

```cpp
const value_type *c_str() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na verzi řetězce s písmenem C.  Hodnota ukazatele není platná po volání funkce bez const, včetně destruktoru, v basic_string třídy na objektu.

### <a name="remarks"></a>Poznámky

Objekty typu řetězec patřící do\<šablony třídy basic_string char> nejsou nutně null ukončena. Znak null \ 0 ' se používá jako speciální znak v řetězci C k označení konce řetězce, ale nemá žádný zvláštní význam v objektu typu řetězce a může být součástí řetězce stejně jako jakýkoli jiný znak. Existuje automatický převod z **const char** <strong>\*</strong> na řetězce, ale třída string neposkytuje automatické převody z řetězců stylu C na objekty typu **basic_string\<char>**.

Vrácený řetězec stylu C by neměl být změněn, protože by to mohlo zneplatnit ukazatel na řetězec nebo odstraněno, protože řetězec má omezenou životnost a je vlastněn řetězcem třídy.

### <a name="example"></a>Příklad

```cpp
// basic_string_c_str.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="basic_stringcapacity"></a><a name="capacity"></a>basic_string::kapacita

Vrátí největší počet prvků, které by mohly být uloženy v řetězci bez zvýšení přidělení paměti řetězce.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost úložiště aktuálně přidělené v paměti pro uložení řetězce.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí úložiště aktuálně přidělené pro uložení řízené sekvence, což je hodnota alespoň tak velká jako [velikost](#size).

### <a name="example"></a>Příklad

```cpp
// basic_string_capacity.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringcbegin"></a><a name="cbegin"></a>basic_string::cbegin

Vrátí **const** iterator, který řeší první prvek v rozsahu.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

**Const** random-access iterátor, který odkazuje na první prvek rozsahu nebo umístění těsně za koncem prázdné oblasti `cbegin() == cend()`(pro prázdný rozsah).

### <a name="remarks"></a>Poznámky

S vrácenou `cbegin`hodnotou , prvky v rozsahu nelze změnit.

Tuto člennou funkci můžete použít `begin()` místo členské funkce k `const_iterator`zajištění, že vrácená hodnota je . Obvykle se používá ve spojení s klíčovým slovem [automatického](../cpp/auto-cpp.md) odpočtu typu, jak je znázorněno v následujícím příkladu. V příkladu `Container` zvažte upravitelné (non-const) kontejner jakéhokoli druhu, `cbegin()`který podporuje **const** `begin()` a .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="basic_stringcend"></a><a name="cend"></a>basic_string::cenzura

Vrátí **const** iterator, který řeší umístění těsně za poslední prvek v rozsahu.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Návratová hodnota

**Const** random-access iterator, který ukazuje těsně za koncem rozsahu.

### <a name="remarks"></a>Poznámky

`cend`se používá k testování, zda iterátor prošel koncem svého rozsahu.

Tuto člennou funkci můžete použít `end()` místo členské funkce k `const_iterator`zajištění, že vrácená hodnota je . Obvykle se používá ve spojení s klíčovým slovem [automatického](../cpp/auto-cpp.md) odpočtu typu, jak je znázorněno v následujícím příkladu. V příkladu `Container` zvažte upravitelné (non-const) kontejner jakéhokoli druhu, `cend()`který podporuje **const** `end()` a .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Hodnota vrácená `cend` podle by neměla být odkazována.

## <a name="basic_stringclear"></a><a name="clear"></a>basic_string::vymazat

Vymaže všechny prvky řetězce.

```cpp
void clear();
```

### <a name="remarks"></a>Poznámky

Řetězec, na kterém je volána členská funkce bude prázdný.

### <a name="example"></a>Příklad

```cpp
// basic_string_clear.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world"), str2;
   basic_string <char>::iterator str_Iter;
   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   str1.clear ( );
   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   //For an empty string, begin is equivalent to end
   if ( str1.begin ( ) == str1.end ( ) )
      cout << "Nothing printed above because "
           << "the string str1 is empty." << endl;
   else
      cout << "The string str1 is not empty." << endl;
}
```

```Output
The original string str1 is: Hello world
The modified string str1 is:
Nothing printed above because the string str1 is empty.
```

## <a name="basic_stringcompare"></a><a name="compare"></a>basic_string::porovnat

Provede porovnání rozlišování malých a velkých písmen se zadaným řetězcem k určení, zda jsou dva řetězce stejné nebo pokud jeden je lexicographically menší než ostatní.

```cpp
int compare(
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count) const;

int compare(
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr
    size_type number_2) const;
```

### <a name="parameters"></a>Parametry

*Str*\
Řetězec, který má být porovnán s operand řetězec.

*position_1*\
Index operand řetězce, ve kterém začíná porovnání.

*number_1*\
Maximální počet znaků z operand řetězce, který má být porovnán.

*number_2*\
Maximální počet znaků z řetězce parametru, který má být porovnán.

*Posun*\
Index řetězce parametru, ve kterém začíná porovnání.

*Počet*\
Maximální počet znaků z řetězce parametru, který má být porovnán.

*Ptr*\
Řetězec C, který má být porovnán s operand řetězce.

### <a name="return-value"></a>Návratová hodnota

Záporná hodnota, pokud je řetězec operandu menší než řetězec parametru; nula, pokud jsou dva řetězce stejné; nebo kladnou hodnotu, pokud je řetězec operandu větší než řetězec parametru.

### <a name="remarks"></a>Poznámky

Členské `compare` funkce porovnávají všechny nebo části řetězce parametrů a operandů v závislosti na použitém prvku.

Provedené porovnání rozlišuje malá a velká písmena.

### <a name="example"></a>Příklad

```cpp
// basic_string_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function compares
   // an operand string to a parameter string
   int comp1;
   string s1o ( "CAB" );
   string s1p ( "CAB" );
   cout << "The operand string is: " << s1o << endl;
   cout << "The parameter string is: " << s1p << endl;
   comp1 = s1o.compare ( s1p );
   if ( comp1 < 0 )
      cout << "The operand string is less than "
           << "the parameter string." << endl;
   else if ( comp1 == 0 )
      cout << "The operand string is equal to "
           << "the parameter string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The second member function compares part of
   // an operand string to a parameter string
   int comp2a, comp2b;
   string s2o ( "AACAB" );
   string s2p ( "CAB" );
   cout << "The operand string is: " << s2o << endl;
   cout << "The parameter string is: " << s2p << endl;
   comp2a = s2o.compare (  2 , 3 , s2p );
   if ( comp2a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;

   comp2b = s2o.compare (  0 , 3 , s2p );
   if ( comp2b < 0 )
      cout << "The first three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2b == 0 )
      cout << "The first three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The first three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The third member function compares part of
   // an operand string to part of a parameter string
   int comp3a;
   string s3o ( "AACAB" );
   string s3p ( "DCABD" );
   cout << "The operand string is: " << s3o << endl;
   cout << "The parameter string is: " << s3p << endl;
   comp3a = s3o.compare (  2 , 3 , s3p , 1 , 3 );
   if ( comp3a < 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are less than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else if ( comp3a == 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are equal to\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else
      cout << "The three characters from position 2 of "
           << "the operand string is greater than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   cout << endl;

   // The fourth member function compares
   // an operand string to a parameter C-string
   int comp4a;
   string s4o ( "ABC" );
   const char* cs4p = "DEF";
   cout << "The operand string is: " << s4o << endl;
   cout << "The parameter C-string is: " << cs4p << endl;
   comp4a = s4o.compare ( cs4p );
   if ( comp4a < 0 )
      cout << "The operand string is less than "
           << "the parameter C-string." << endl;
   else if ( comp4a == 0 )
      cout << "The operand string is equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The fifth member function compares part of
   // an operand string to a parameter C-string
   int comp5a;
   string s5o ( "AACAB" );
   const char* cs5p = "CAB";
   cout << "The operand string is: " << s5o << endl;
   cout << "The parameter string is: " << cs5p << endl;
   comp5a = s5o.compare (  2 , 3 , s2p );
   if ( comp5a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter C-string." << endl;
   else if ( comp5a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The sixth member function compares part of
   // an operand string to part of an equal length of
   // a parameter C-string
   int comp6a;
   string s6o ( "AACAB" );
   const char* cs6p = "ACAB";
   cout << "The operand string is: " << s6o << endl;
   cout << "The parameter C-string is: " << cs6p << endl;
   comp6a = s6o.compare (  1 , 3 , cs6p , 3 );
   if ( comp6a < 0 )
      cout << "The 3 characters from position 1 of "
           << "the operand string are less than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   else if ( comp6a == 0 )
      cout << "The 3 characters from position 2 of "
           << "the operand string are equal to\n "
           << "the first 3 characters of the parameter C-string."
           <<  endl;
   else
      cout << "The 3 characters from position 2 of "
           << "the operand string is greater than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   cout << endl;
}
```

```Output
The operand string is: CAB
The parameter string is: CAB
The operand string is equal to the parameter string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter string.
The first three characters of the operand string
are less than the parameter string.

The operand string is: AACAB
The parameter string is: DCABD
The three characters from position 2 of the operand string are equal to
the 3 characters parameter string from position 1.

The operand string is: ABC
The parameter C-string is: DEF
The operand string is less than the parameter C-string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter C-string.

The operand string is: AACAB
The parameter C-string is: ACAB
The 3 characters from position 2 of the operand string are equal to
the first 3 characters of the parameter C-string.
```

## <a name="basic_stringconst_iterator"></a><a name="const_iterator"></a>basic_string::const_iterator

Typ, který poskytuje iterátor s náhodným přístupem, který může přistupovat a číst **prvek const** v řetězci.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_iterator` nelze použít ke změně hodnoty znaku a slouží k iterátu prostřednictvím řetězce ve směru dopředu.

### <a name="example"></a>Příklad

Příklad [začátku](#begin) naleznete v příkladu, jak `const_iterator`deklarovat a používat .

## <a name="basic_stringconst_pointer"></a><a name="const_pointer"></a>basic_string::const_pointer

Typ, který poskytuje ukazatel na **const** prvek v řetězci.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `allocator_type::const_pointer`pro .

Pro `string`typ je ekvivalentní `char*`.

Ukazatele, které jsou deklarovány const musí být inicializovány, když jsou deklarovány. Const ukazatele vždy přejděte na stejné umístění paměti a může přejděte na konstantní nebo nekonstantní data.

### <a name="example"></a>Příklad

```cpp
// basic_string_const_ptr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::const_pointer pstr1a = "In Here";
   const char *cstr1c = "Out There";

   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1c is: " << cstr1c << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1c is: Out There.
```

## <a name="basic_stringconst_reference"></a><a name="const_reference"></a>basic_string::const_reference

Typ, který poskytuje odkaz na **const** prvek uložený v řetězci pro čtení a provádění **const** operací.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Typ `const_reference` nelze použít ke změně hodnoty prvku.

Typ je synonymem `allocator_type::const_reference`pro . Pro `type`řetězec je ekvivalentní const `char&`.

### <a name="example"></a>Příklad

Viz příklad pro [at](#at) pro příklad, jak `const_reference`deklarovat a používat .

## <a name="basic_stringconst_reverse_iterator"></a><a name="const_reverse_iterator"></a>basic_string::const_reverse_iterator

Typ, který poskytuje iterátor náhodného přístupu, který může číst libovolný **prvek const** v řetězci.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `const_reverse_iterator` nemůže změnit hodnotu znaku a používá se k iterátu prostřednictvím řetězce v opačném směru.

### <a name="example"></a>Příklad

Příklad pro [rbegin](#rbegin) naleznete v příkladu, `const_reverse_iterator`jak deklarovat a používat .

## <a name="basic_stringcopy"></a><a name="copy"></a>basic_string::kopírování

Zkopíruje maximálně zadaný počet znaků z indexované pozice ve zdrojovém řetězci do cílového pole znaků.

Tato metoda je potenciálně nebezpečné, protože spoléhá na volajícího zkontrolovat, že předané hodnoty jsou správné. Zvažte použití [basic_string::_Copy_s.](#copy_s)

```cpp
size_type copy(
    value_type* ptr,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*Ptr*\
Cílové pole znaků, do kterého mají být prvky zkopírovány.

*počet* Počet znaků, které mají být zkopírovány maximálně ze zdrojového řetězce.

*Posun*\
Počáteční pozice ve zdrojovém řetězci, ze kterého mají být provedeny kopie.

### <a name="return-value"></a>Návratová hodnota

Počet skutečně zkopírovaných znaků.

### <a name="remarks"></a>Poznámky

Znak null není připojen na konec kopie.

### <a name="example"></a>Příklad

```cpp
// basic_string_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello World" );
   basic_string <char>::iterator str_Iter;
   char array1 [ 20 ] = { 0 };
   char array2 [ 10 ] = { 0 };
   basic_string <char>:: pointer array1Ptr = array1;
   basic_string <char>:: value_type *array2Ptr = array2;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   basic_string <char>:: size_type nArray1;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray1 = str1.copy ( array1Ptr , 12 );  // C4996
   cout << "The number of copied characters in array1 is: "
        << nArray1 << endl;
   cout << "The copied characters array1 is: " << array1 << endl;

   basic_string <char>:: size_type nArray2;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray2 = str1.copy ( array2Ptr , 5 , 6  );  // C4996
   cout << "The number of copied characters in array2 is: "
           << nArray2 << endl;
   cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="basic_stringcrbegin"></a><a name="crbegin"></a>basic_string::crbegin

Vrátí const iterator, který řeší první prvek v obráceném řetězci.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Návratová hodnota

Zpětný iterátor, který ukazuje těsně za koncem řetězce. Pozice označuje začátek zpětného řetězce.

## <a name="basic_stringcrend"></a><a name="crend"></a>basic_string::crend

Vrátí const iterátor, který řeší umístění, které následuje poslední prvek v obráceném řetězci.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní iterátor, který řeší umístění následuje poslední prvek v obráceném řetězci (umístění, které předcházelo první prvek v unreverse řetězec).

### <a name="remarks"></a>Poznámky

## <a name="basic_string_copy_s"></a><a name="copy_s"></a>basic_string::_Copy_s

Zkopíruje maximálně zadaný počet znaků z indexované pozice ve zdrojovém řetězci do cílového pole znaků.

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*Dest*\
Cílové pole znaků, do kterého mají být prvky zkopírovány.

*dest_size*\
Velikost *dest*.

*počet* Počet znaků, které mají být zkopírovány maximálně ze zdrojového řetězce.

*Posun*\
Počáteční pozice ve zdrojovém řetězci, ze kterého mají být provedeny kopie.

### <a name="return-value"></a>Návratová hodnota

Počet skutečně zkopírovaných znaků.

### <a name="remarks"></a>Poznámky

Znak null není připojen na konec kopie.

### <a name="example"></a>Příklad

```cpp
// basic_string__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;
    string str1("Hello World");
    basic_string<char>::iterator str_Iter;
    const int array1_size = 20;
    char array1[array1_size] = { 0 };
    const int array2_size = 10;
    char array2[array2_size] = { 0 };
    basic_string<char>:: pointer array1Ptr = array1;
    basic_string<char>:: value_type *array2Ptr = array2;

    cout << "The original string str1 is: ";
    for (str_Iter = str1.begin(); str_Iter != str1.end(); str_Iter++)
        cout << *str_Iter;
    cout << endl;

    basic_string<char>::size_type nArray1;
    nArray1 = str1._Copy_s(array1Ptr, array1_size, 12);
    cout << "The number of copied characters in array1 is: "
         << nArray1 << endl;
    cout << "The copied characters array1 is: " << array1 << endl;

    basic_string<char>:: size_type nArray2;
    nArray2 = str1._Copy_s(array2Ptr, array2_size, 5, 6);
    cout << "The number of copied characters in array2 is: "
         << nArray2 << endl;
    cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="basic_stringdata"></a><a name="data"></a>basic_string::data

Převede obsah řetězce na pole znaků ukončené nulou.

```cpp
const value_type *data() const noexcept;
value_type *data() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první prvek pole ukončeného hodnotou null obsahující obsah řetězce. U prázdného řetězce ukazatel odkazuje na jeden `value_type()`znak null, který se rovná znaku .

### <a name="remarks"></a>Poznámky

Ukazatel vrácený `data` body v `[data(), data() + size()]`platném rozsahu . Každý prvek v rozsahu odpovídá aktuální data v řetězci. To znamená pro každý *n* platný posun `data() + n == addressof(operator[](n))`n v rozsahu .

Pokud změníte obsah řetězce vráceného **přetížení const** `data`, chování není definováno. Můžete také získat nedefinované chování, pokud terminál null znak se změní na jinou hodnotu. Vrácený ukazatel může být zrušena, pokud je neconst odkaz na řetězec předán standardní funkce knihovny. Může být také zrušena voláním členské funkce, která není const. Volání členů `at` `back`, `begin` `end`, `front` `rbegin`, `rend`, `operator[]` , a nezneplatňují ukazatel.

Před C ++ 11 nezaručuje, `data` že vrácený řetězec byl ukončen null. Vzhledem k tomu, `data` `c_str` C ++ 11 a oba vrátit řetězec ukončennul nula a jsou účinně stejné.

Přetížení bez const je nové v jazyce C++17. Chcete-li jej použít, zadejte parametr **/std:c++17** nebo **/std:c++latest** compiler.

### <a name="example"></a>Příklad

```cpp
// basic_string_data.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="basic_stringdifference_type"></a><a name="difference_type"></a>basic_string::difference_type

Typ, který poskytuje rozdíl mezi dvěma iterátory, které odkazují na prvky v rámci stejného řetězce.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typ podepsaného celého čísla popisuje objekt, který může představovat rozdíl mezi adresami libovolných dvou prvků v řízené sekvenci.

Pro `string`typ je ekvivalentní `ptrdiff_t`.

### <a name="example"></a>Příklad

```cpp
// basic_string_diff_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "quintillion" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexChFi, indexChLi;

   indexChFi = str1.find_first_of ( "i" );
   indexChLi = str1.find_last_of ( "i" );
   basic_string<char>::difference_type diffi = indexChLi - indexChFi;

   cout << "The first character i is at position: "
        << indexChFi << "." << endl;
   cout << "The last character i is at position: "
        << indexChLi << "." << endl;
   cout << "The difference is: " << diffi << "." << endl;
}
```

```Output
The original string str1 is: quintillion
The first character i is at position: 2.
The last character i is at position: 8.
The difference is: 6.
```

## <a name="basic_stringempty"></a><a name="empty"></a>basic_string::prázdný

Testuje, zda řetězec obsahuje znaky nebo ne.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud objekt řetězce neobsahuje žádné znaky; **false,** pokud má alespoň jeden znak.

### <a name="remarks"></a>Poznámky

Členská funkce je ekvivalentní [velikost ==](#size) 0.

### <a name="example"></a>Příklad

```cpp
// basic_string_empty.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   bool b1, b2;

   string str1 ("Hello world");
   cout << "The original string object str1 is: " << str1 << endl;
   b1 = str1.empty();
   if (b1)
      cout << "The string object str1 is empty." << endl;
   else
      cout << "The string object str1 is not empty." << endl;
   cout << endl;

   // An example of an empty string object
   string str2;
   b2 = str2.empty();
   if (b2)
      cout << "The string object str2 is empty." << endl;
   else
      cout << "The string object str2 is not empty." << endl;
}
```

## <a name="basic_stringend"></a><a name="end"></a>basic_string::konec

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v řetězci.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor náhodného přístupu, který řeší umístění, které následuje poslední prvek v řetězci.

### <a name="remarks"></a>Poznámky

`end`se často používá k testování, zda iterátor dosáhl konce svého řetězce. Hodnota vrácená `end` podle by neměla být odkazována.

Pokud `end` je vrácená hodnota `const_iterator`přiřazena aplikaci , nelze objekt řetězce změnit. Pokud `end` je vrácená hodnota `iterator`přiřazena objektu , lze objekt řetězce změnit.

### <a name="example"></a>Příklad

```cpp
// basic_string_end.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator str_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.end ( );
   str1_Iter--;
   str1_Iter--;
   cout << "The last character-letter of the string str1 is: " << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // end used to test when an iterator has reached the end of its string
   cout << "The string is now: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_Iter = 'T';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.begin( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the string str1 is: t
The full original string str1 is: No way out.
The string is now: No way out.
The last character-letter of the modified str1 is now: T
The modified string str1 is now: No way ouT.
The string str2 is empty.
```

## <a name="basic_stringerase"></a><a name="erase"></a>basic_string::vymazat

Odebere prvek nebo rozsah prvků v řetězci ze zadané pozice.

```cpp
iterator erase(
    iterator first,
    iterator last);

iterator erase(
    iterator iter);

basic_string<CharType, Traits, Allocator>& erase(
    size_type offset = 0,
    size_type count = npos);
```

### <a name="parameters"></a>Parametry

*První*\
Iterátor adresování pozici prvního prvku v rozsahu, který má být vymazán.

*Poslední*\
Iterátor adresování pozice jeden za poslední prvek v rozsahu, který má být vymazán.

*Iter*\
Iterátor adresování pozici prvku v řetězci, které mají být vymazány.

*Posun*\
Index prvního znaku v řetězci, který má být odebrán.

*Počet*\
Počet prvků, které budou odebrány, pokud existuje tolik v rozsahu řetězce začínající *posun*.

### <a name="return-value"></a>Návratová hodnota

Pro první dvě členské funkce iterátor adresování první znak po poslední znak odebrán členské funkce. Pro třetí členské funkce odkaz na objekt řetězce, ze kterého byly prvky vymazány.

### <a name="remarks"></a>Poznámky

Třetí členská ** \*** funkce vrátí tuto funkci .

### <a name="example"></a>Příklad

```cpp
// basic_string_erase.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The 1st member function using a range demarcated
   // by iterators
   string str1 ( "Hello world" );
   basic_string <char>::iterator str1_Iter;
   cout << "The original string object str1 is: "
        << str1 << "." << endl;
   str1_Iter = str1.erase ( str1.begin ( ) + 3 , str1.end ( ) - 1 );
   cout << "The first element after those removed is: "
        << *str1_Iter << "." << endl;
   cout << "The modified string object str1 is: " << str1
           << "." << endl << endl;

   // The 2nd member function erasing a char pointed to
   // by an iterator
   string str2 ( "Hello World" );
   basic_string <char>::iterator str2_Iter;
   cout << "The original string object str2 is: " << str2
        << "." << endl;
   str2_Iter = str2.erase ( str2.begin ( ) + 5 );
   cout << "The first element after those removed is: "
        << *str2_Iter << "." << endl;
   cout << "The modified string object str2 is: " << str2
        << "." << endl << endl;

   // The 3rd member function erasing a number of chars
   // after a char
   string str3 ( "Hello computer" ), str3m;
   basic_string <char>::iterator str3_Iter;
   cout << "The original string object str3 is: "
        << str3 << "." << endl;
   str3m = str3.erase ( 6 , 8 );
   cout << "The modified string object str3m is: "
        << str3m << "." << endl;
}
```

```Output
The original string object str1 is: Hello world.
The first element after those removed is: d.
The modified string object str1 is: Held.

The original string object str2 is: Hello World.
The first element after those removed is: W.
The modified string object str2 is: HelloWorld.

The original string object str3 is: Hello computer.
The modified string object str3m is: Hello .
```

## <a name="basic_stringfind"></a><a name="find"></a>basic_string::najít

Prohledá řetězec ve směru dopředu pro první výskyt podřetězce, který odpovídá zadané posloupnosti znaků.

```cpp
size_type find(
    value_type char_value,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index pozice, na které má vyhledávání začít.

*Ptr*\
Řetězec znaků, který má členská funkce vyhledat.

*Počet*\
Počet znaků, počítaných vpřed od prvního znaku v řetězci znaků, které má členská funkce vyhledat.

*Str*\
Řetězec, který má členská funkce vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

### <a name="example"></a>Příklad

```cpp
// basic_string_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;

   indexCh1a = str1.find ( "e" , 3 );
   if (indexCh1a != string::npos )
      cout << "The index of the 1st 'e' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.find ( "x" );
   if (indexCh1b != string::npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.find ( cstr2 , 5 );
   if ( indexCh2a != string::npos )
      cout << "The index of the 1st element of 'perfect' "
           << "after\n the 5th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.find ( cstr2b , 0 );
   if (indexCh2b != string::npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "after\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "This is a sample string for this program" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "sample";
   indexCh3a = str3.find ( cstr3a );
   if ( indexCh3a != string::npos )
      cout << "The index of the 1st element of sample "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'perfect' was not found in str3 ."
           << endl;

   const char *cstr3b = "for";
   indexCh3b = str3.find ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != string::npos )
      cout << "The index of the next occurrence of 'for' is in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'for' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "clearly this perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.find ( str4a , 5 );
   if ( indexCh4a != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "after\n the 5th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl;

   string str4b ( "clear" );
   indexCh4b = str4.find ( str4b );
   if (indexCh4b != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found after the 3rd position in str1 is: 8
The Character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' after
the 5th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: This is a sample string for this program
The index of the 1st element of sample in str3 is: 10
The index of the next occurrence of 'for' is in str3 begins at: 24

The original string str4 is: clearly this perfectly unclear.
The index of the 1st element of 'clear' after
the 5th position in str4 is: 25
The index of the 1st element of 'clear' in str4 is: 0
```

## <a name="basic_stringfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string::find_first_not_of

Hledá řetězec pro první znak, který není prvek zadaného řetězce.

```cpp
size_type find_first_not_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index pozice, na které má vyhledávání začít.

*Ptr*\
Řetězec znaků, který má členská funkce vyhledat.

*Počet*\
Počet znaků, počítaných vpřed od prvního znaku v řetězci znaků, které má členská funkce vyhledat.

*Str*\
Řetězec, který má členská funkce vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

### <a name="example"></a>Příklad

```cpp
// basic_string_find_first_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "xddd-1234-abcd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_not_of ( "d" , 2 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_not_of  ( "x" );
   if (indexCh1b != npos )
      cout << "The index of the 'non x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_not_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not"
           << "\n found in str2 after the 6th position."
           << endl;

   const char *cstr2b = "B2";
   indexCh2b = str2.find_first_not_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'B2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'B2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_first_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_first_not_of ( cstr3b , indexCh3a + 1 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '45G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_not_of ( str4a , 5 );
   if (indexCh4a != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'ba3' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_first_not_of ( str4b  );
   if (indexCh4b != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of '12' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12' were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: xddd-1234-abcd
The index of the 1st 'd' found after the 3rd position in str1 is: 4
The index of the 'non x' found in str1 is: 1

The original string str2 is: BBB-1111
Elements of the substring 'B1' were not
found in str2 after the 6th position.
The index of the 1st element of 'B2' after
the 0th position in str2 is: 3

The original string str3 is: 444-555-GGG
The index of the 1st occurrence of an element in str3
other than one of the characters in '45G' is: 3
The index of the second occurrence of an element of '45G' in str3
after the 0th position is: 7

The original string str4 is: 12-ab-12-ab
The index of the 1st non occurrence of an element of 'ba3' in str4 after
the 5th position is: 5
The index of the 1st non occurrence of an element of '12' in str4 after
the 0th position is: 2
```

## <a name="basic_stringfind_first_of"></a><a name="find_first_of"></a>basic_string::find_first_of

Hledá prostřednictvím řetězce pro první znak, který odpovídá libovolný prvek zadaného řetězce.

```cpp
size_type find_first_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index pozice, na které má vyhledávání začít.

*Ptr*\
Řetězec znaků, který má členská funkce vyhledat.

*Počet*\
Počet znaků, počítaných vpřed od prvního znaku v řetězci znaků, které má členská funkce vyhledat.

*Str*\
Řetězec, který má členská funkce vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

### <a name="example"></a>Příklad

```cpp
// basic_string_find_first_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_of ( "d" , 5 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 5th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for any element of a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 after the 10th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_first_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for any element of a substring as specified by a C-string
   string str3 ( "123-abc-123-abc-456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "5G";
   indexCh3a = str3.find_first_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of '5G' in str3 after\n the 0th "
           << "position is: " << indexCh3a << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the 0th position."
           << endl;

   const char *cstr3b = "5GF";
   indexCh3b = str3.find_first_of  ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '5G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the first occurrrence."
           << endl << endl;

   // The fourth member function searches a string
   // for any element of a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_of ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_first_of ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'a2' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the 1st 'd' found after the 5th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the 1st occurrence of an element of 'B1' in str2 after
the 6th position is: 11
The index of the 1st element of 'D2' after
the 0th position in str2 is: 3

The original string str3 is: 123-abc-123-abc-456-EFG-456-EFG
The index of the 1st occurrence of an element of '5G' in str3 after
the 0th position is: 17
The index of the second occurrence of an element of '5G' in str3
after the 0th position is: 22

The original string str4 is: 12-ab-12-ab
The index of the 1st occurrence of an element of 'ba3' in str4 after
the 5th position is: 9
The index of the 1st occurrence of an element of 'a2' in str4 after
the 0th position is: 1
```

## <a name="basic_stringfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string::find_last_not_of

Prohledá řetězec pro poslední znak, který není žádný prvek zadaného řetězce.

```cpp
size_type find_last_not_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index pozice, na které má být hledání dokončeno.

*Ptr*\
Řetězec znaků, který má členská funkce vyhledat.

*Počet*\
Počet znaků, počítaných vpřed od prvního znaku v řetězci znaků, které má členská funkce vyhledat.

*Str*\
Řetězec, který má členská funkce vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

### <a name="example"></a>Příklad

```cpp
// basic_string_find_last_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "dddd-1dd4-abdd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_not_of ( "d" , 7 );
   if ( indexCh1a != npos )
      cout << "The index of the last non 'd'\n found before the "
           << "7th position in str1 is: " << indexCh1a << endl;
   else
      cout << "The non 'd' character was not found ." << endl;

   indexCh1b = str1.find_last_not_of  ( "d" );
   if ( indexCh1b != npos )
      cout << "The index of the non 'd' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_not_of  ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the last occurrence of a "
           << "element\n not of 'B1' in str2 before the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements not of the substring 'B1' were not "
           << "\n found in str2 before the 6th position."
           << endl;

   const char *cstr2b = "B-1";
   indexCh2b = str2.find_last_not_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element not "
           << "in 'B-1'\n is: "
           << indexCh2b << endl << endl;
   else
      cout << "The elements of the substring 'B-1' were "
           << "not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_last_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_last_not_of ( cstr3b , 6 , indexCh3a - 1 );
   if (indexCh3b != npos )
      cout << "The index of the penultimate occurrence of an "
           << "element\n not in '45G' in str3 is: "
           << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "b-a" );
   indexCh4a = str4.find_last_not_of  ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element not\n in 'b-a' in str4 before the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'b-a' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_last_not_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element not in '12'\n in str4 before the end "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12'\n were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: dddd-1dd4-abdd
The index of the last non 'd'
found before the 7th position in str1 is: 5
The index of the non 'd' found in str1 is: 11

The original string str2 is: BBB-1111
The index of the last occurrence of a element
not of 'B1' in str2 before the 6th position is: 3
The elements of the substring 'B-1' were not found in str2 .

The original string str3 is: 444-555-GGG
The index of the last occurrence of an element in str3
other than one of the characters in '45G' is: 7
The index of the penultimate occurrence of an element
not in '45G' in str3 is: 3

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element not
in 'b-a' in str4 before the 5th position is: 1
The index of the last occurrence of an element not in '12'
in str4 before the end position is: 10
```

## <a name="basic_stringfind_last_of"></a><a name="find_last_of"></a>basic_string::find_last_of

Prohledá řetězec pro poslední znak, který odpovídá libovolný prvek zadaného řetězce.

```cpp
size_type find_last_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index pozice, na které má být hledání dokončeno.

*Ptr*\
Řetězec znaků, který má členská funkce vyhledat.

*Počet*\
Počet znaků, počítaných vpřed od prvního znaku v řetězci znaků, které má členská funkce vyhledat.

*Str*\
Řetězec, který má členská funkce vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index posledního znaku podřetězce hledaného při úspěšném zobrazení; v `npos`opačném případě .

### <a name="example"></a>Příklad

```cpp
// basic_string_find_last_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_of ( "d" , 14 );
   if ( indexCh1a != npos )
      cout << "The index of the last 'd' found before the 14th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_of  ( cstr2 , 12 );
   if (indexCh2a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'B1' in str2 before\n the 12th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 before the 12th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_last_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a;

   const char *cstr3a = "5E";
   indexCh3a = str3.find_last_of ( cstr3a , 8 , 8 );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element of '5E' in str3 before\n the 8th "
           << "position is: " << indexCh3a << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n before the 8th position."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_last_of  ( str4a , 8 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'ba3' in str4 before\n the 8th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_last_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'a2' in str4 before\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the last 'd' found before the 14th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the last occurrence of an element of 'B1' in str2 before
the 12th position is: 11
The index of the last element of 'D2' after
the 0th position in str2 is: 16

The original string str3 is: 456-EFG-456-EFG
The index of the last occurrence of an element of '5E' in str3 before
the 8th position is: 4

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element of 'ba3' in str4 before
the 8th position is: 4
The index of the last occurrence of an element of 'a2' in str4 before
the 0th position is: 9
```

## <a name="basic_stringfront"></a><a name="front"></a>basic_string::přední

Vrátí odkaz na první prvek v řetězci.

```cpp
const_reference front() const;

reference front();
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na první prvek řetězce, který musí být neprázdný.

### <a name="remarks"></a>Poznámky

## <a name="basic_stringget_allocator"></a><a name="get_allocator"></a>basic_string::get_allocator

Vrátí kopii objektu alokátoru použitého k vytvoření řetězce.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Alokátor používaný řetězcem.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložený objekt přidělování.

Alokátory pro třídu řetězce určují, jak třída spravuje úložiště. Výchozí alokátory dodávané s třídami kontejnerů jsou dostatečné pro většinu potřeb programování. Psaní a používání vlastní třídy přidělování je pokročilé téma jazyka C++.

### <a name="example"></a>Příklad

```cpp
// basic_string_get_allocator.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char> s2;
   basic_string <char, char_traits< char >, allocator< char > > s3;

   // s4 will use the same allocator class as s1
   basic_string <char> s4( s1.get_allocator ( ) );

   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="basic_stringinsert"></a><a name="insert"></a>basic_string::vložit

Vloží prvek nebo počet prvků nebo rozsah prvků do řetězce v zadané pozici.

```cpp
basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    size_type count,
    value_type char_value);

iterator insert(
    iterator iter);

iterator insert(
    iterator iter,
    value_type char_value)l
template <class InputIterator>
void insert(
    iterator iter,
    InputIterator first,
    InputIterator last);

void insert(
    iterator iter,
    size_type count,
    value_type char_value);

void insert(
    iterator iter,
    const_pointer first,
    const_pointer last);

void insert(
    iterator iter,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

*Pozici*\
Index pozice za bodem vložení nové znaky.

*Ptr*\
Řetězec C zcela nebo částečně vložen do řetězce.

*Počet*\
Počet znaků, které mají být vloženy.

*Str*\
Řetězec, který má být zcela nebo částečně vložen do cílového řetězce.

*Posun*\
Index části zdrojového řetězce, který poskytuje znaky, které mají být připojeny.

*char_value*\
Hodnota znaku prvků, které mají být vloženy.

*Iter*\
Iterátor adresování pozice, za kterou má být vložen znak.

*První*\
Vstupní iterátor, const_pointer nebo const_iterator adresování první prvek ve zdrojové oblasti, které mají být vloženy.

*Poslední*\
Vstupní iterátor, const_pointer nebo const_iterator adresování pozice jednoho za poslední prvek ve zdrojové oblasti, které mají být vloženy.

### <a name="return-value"></a>Návratová hodnota

Buď odkaz na objekt řetězce, který je přiřazen nové znaky členská funkce nebo v případě jednotlivých znaků vložení iterátor adresování pozici vloženého znaku nebo žádný, v závislosti na konkrétní členské funkce.

### <a name="example"></a>Příklad

```cpp
// basic_string_insert.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function inserting a C-string
   // at a given position
   basic_string <char> str1a ( "way" );
   const char *cstr1a = "a";
   str1a.insert ( 0, cstr1a );
   cout << "The string with a C-string inserted at position 0 is: "
        << str1a << "." << endl;

   // The second member function inserting a C-string
   // at a given position for a specified number of elements
   basic_string <char> str2a ( "Good" );
   const char *cstr2a = "Bye Bye Baby";
   str2a.insert ( 4, cstr2a ,3 );
   cout << "The string with a C-string inserted at the end is: "
        << str2a << "." << endl;

   // The third member function inserting a string
   // at a given position
   basic_string <char> str3a ( "Bye" );
   string str3b ( "Good" );
   str3a.insert ( 0, str3b );
   cout << "The string with a string inserted at position 0 is: "
        << str3a << "." << endl;

   // The fourth member function inserting part of
   // a string at a given position
   basic_string <char> str4a ( "Good " );
   string str4b ( "Bye Bye Baby" );
   str4a.insert ( 5, str4b , 8 , 4 );
   cout << "The string with part of a string inserted at position 4 is: "
        << str4a << "." << endl;

   // The fifth member function inserts a number of characters
   // at a specified position in the string
   string str5 ( "The number is: ." );
   str5.insert ( 15 , 3 , '3' );
   cout << "The string with characters inserted is: "
        << str5 << endl;

   // The sixth member function inserts a character
   // at a specified position in the string
   string str6 ( "ABCDFG" );
   basic_string <char>::iterator str6_Iter = ( str6.begin ( ) + 4 );
   str6.insert ( str6_Iter , 'e' );
   cout << "The string with a character inserted is: "
        << str6 << endl;

   // The seventh member function inserts a range
   // at a specified position in the string
   string str7a ( "ABCDHIJ" );
   string str7b ( "abcdefgh" );
   basic_string <char>::iterator str7a_Iter = (str7a.begin ( ) + 4 );
   str7a.insert ( str7a_Iter , str7b.begin ( ) + 4 , str7b.end ( ) -1 );
   cout << "The string with a character inserted from a range is: "
        << str7a << endl;

   // The eighth member function inserts a number of
   // characters at a specified position in the string
   string str8 ( "ABCDHIJ" );
   basic_string <char>::iterator str8_Iter = ( str8.begin ( ) + 4 );
   str8.insert ( str8_Iter , 3 , 'e' );
   cout << "The string with a character inserted from a range is: "
        << str8 << endl;
}
```

```Output
The string with a C-string inserted at position 0 is: away.
The string with a C-string inserted at the end is: GoodBye.
The string with a string inserted at position 0 is: GoodBye.
The string with part of a string inserted at position 4 is: Good Baby.
The string with characters inserted is: The number is: 333.
The string with a character inserted is: ABCDeFG
The string with a character inserted from a range is: ABCDefgHIJ
The string with a character inserted from a range is: ABCDeeeHIJ
```

## <a name="basic_stringiterator"></a><a name="iterator"></a>basic_string::iterátor

Typ, který poskytuje iterátor s náhodným přístupem, který může přistupovat a číst **prvek const** v řetězci.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Poznámky

Typ `iterator` lze použít k úpravě hodnoty znaku a slouží k iterátu prostřednictvím řetězce ve směru dopředu.

### <a name="example"></a>Příklad

Příklad [začátku](#begin) naleznete v příkladu, jak `iterator`deklarovat a používat .

## <a name="basic_stringlength"></a><a name="length"></a>basic_string::délka

Vrátí aktuální počet prvků v řetězci.

```cpp
size_type length() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce je stejná jako [velikost](#size).

### <a name="example"></a>Příklad

```cpp
// basic_string_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringmax_size"></a><a name="max_size"></a>basic_string::max_size

Vrátí maximální počet znaků, které může řetězec obsahovat.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet znaků, které může řetězec obsahovat.

### <a name="remarks"></a>Poznámky

Výjimka typu [length_error Class](../standard-library/length-error-class.md) je vyvolána, když operace vytvoří řetězec s délkou větší než maximální velikost.

### <a name="example"></a>Příklad

```cpp
// basic_string_max_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringnpos"></a><a name="npos"></a>basic_string::npos

Nepodepsaná integrální hodnota inicializovaná na -1, která označuje buď "nebyly nalezeny" nebo "všechny zbývající znaky", když se nezdaří vyhledávací funkce.

```cpp
static const size_type npos = -1;
```

### <a name="remarks"></a>Poznámky

Pokud má být vrácená hodnota `npos` zkontrolována pro hodnotu, nemusí fungovat, pokud není vrácená hodnota typu [size_type](#size_type) a není ani **int** nebo **nepodepsaná**.

### <a name="example"></a>Příklad

Viz příklad [najít](#find) příklad, jak deklarovat a používat `npos`.

## <a name="basic_stringoperator"></a><a name="op_add_eq"></a>basic_string::operátor+=

Připojí znaky k řetězci.

```cpp
basic_string<CharType, Traits, Allocator>& operator+=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator+=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator+=(
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*char_value*\
Znak, který má být připojen.

*Ptr*\
Znaky c-řetězec, který má být připojen.

*Právo*\
Znaky řetězce, který má být připojen.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt řetězce, který je připojen se znaky předanými členovou funkcí.

### <a name="remarks"></a>Poznámky

Znaky mohou být připojeny k `operator+=` řetězci pomocí nebo členské funkce [připojit](#append) nebo [push_back](#push_back). Připojí `operator+=` hodnoty jednoho argumentu, zatímco členská funkce více argumentů umožňuje zadat určitou část řetězce pro přidání.

### <a name="example"></a>Příklad

```cpp
// basic_string_op_app.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a single character to a string
   string str1a ( "Hello" );
   cout << "The original string str1 is: " << str1a << endl;
   str1a +=  '!' ;
   cout << "The string str1 appended with an exclamation is: "
        << str1a << endl << endl;

   // The second member function
   // appending a C-string to a string
   string  str1b ( "Hello " );
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b +=  cstr1b;
   cout << "Appending the C-string cstr1b to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World" );
   cout << "The string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The string str1 appended with an exclamation is: Hello!

The C-string cstr1b is: Out There
Appending the C-string cstr1b to string str1 gives: Hello Out There.

The string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World.
```

## <a name="basic_stringoperator"></a><a name="op_eq"></a>basic_string::operátor=

Přiřadí nové hodnoty znaků k obsahu řetězce.

```cpp
basic_string<CharType, Traits, Allocator>& operator=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>& right);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>Parametry

*char_value*\
Hodnota znaku, která má být přiřazena.

*Ptr*\
Ukazatel na znaky řetězce C, které mají být přiřazeny k cílovému řetězci.

*Právo*\
Zdrojový řetězec, jehož znaky mají být přiřazeny k cílovému řetězci.

### <a name="return-value"></a>Návratová hodnota

Odkaz na objekt řetězce, kterému členská funkce přiřazuje nové znaky.

### <a name="remarks"></a>Poznámky

Řetězce mohou být přiřazeny nové hodnoty znaků. Nová hodnota může být řetězec a řetězec C nebo jeden znak. Lze `operator=` použít, pokud lze novou hodnotu popsat jedním parametrem, jinak může být [přiřazena](#assign)členská funkce , která má více parametrů, k určení, která část řetězce má být přiřazena cílovému řetězci.

### <a name="example"></a>Příklad

```cpp
// basic_string_op_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning a
   // character of a certain value to a string
   string str1a ( "Hello " );
   str1a = '0';
   cout << "The string str1 assigned with the zero character is: "
        << str1a << endl << endl;

   // The second member function assigning the
   // characters of a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b <<  "." << endl;
   str1b = cstr1b;
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1c ( "Hello" ), str2c ( "Wide" ), str3c ( "World" );
   cout << "The original string str1 is: " << str1c << "." << endl;
   cout << "The string str2c is: " << str2c << "." << endl;
   str1c.assign ( str2c );
   cout << "The string str1 newly assigned with string str2c is: "
        << str1c << "." << endl;
   cout << "The string str3c is: " << str3c << "." << endl;
   str1c = str3c;
   cout << "The string str1 reassigned with string str3c is: "
        << str1c << "." << endl << endl;
}
```

```Output
The string str1 assigned with the zero character is: 0

The C-string cstr1b is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The original string str1 is: Hello.
The string str2c is: Wide.
The string str1 newly assigned with string str2c is: Wide.
The string str3c is: World.
The string str1 reassigned with string str3c is: World.
```

## <a name="basic_stringoperator"></a><a name="op_at"></a>basic_string::operátor[]

Obsahuje odkaz na znak se zadaným indexem v řetězci.

```cpp
const_reference operator[](size_type offset) const;
reference operator[](size_type offset);
```

### <a name="parameters"></a>Parametry

*Posun*\
Index pozice prvku, na který se má odkazovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na znak řetězce na pozici určené indexem parametru.

### <a name="remarks"></a>Poznámky

První prvek řetězce má nulový index a následující prvky jsou postupně indexovány kladným icelovními čísly, takže řetězec length *n* má *n.* prvek indexovaný číslem *n* - 1.

`operator[]`je rychlejší než členské funkce [na](#at) pro poskytování přístupu pro čtení a zápis k prvkům řetězce.

`operator[]`nekontroluje, zda je index předaný jako parametr `at` platný, ale členská funkce ano a proto by měla být použita v platnosti není jistá. Neplatný index (index menší než nula nebo větší nebo roven velikosti `at` řetězce) předaný členské funkci vyvolá výjimku [out_of_range Class.](../standard-library/out-of-range-class.md) Neplatný index `operator[]` předaný výsledkům v nedefinovaném chování, ale index rovnající se délce řetězce je platný index pro řetězce const a operátor vrátí znak null při předání tohoto indexu.

Vrácený odkaz může být zrušena přerozdělení řetězce nebo změny pro řetězce bez **const.**

Při kompilaci s [ \_\_ITERATOR\_LADĚNÍ ÚROVEŇ](../standard-library/iterator-debug-level.md) nastavena na 1 nebo 2, dojde k chybě za běhu, pokud se pokusíte o přístup k prvku mimo hranice řetězce. Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Příklad

```cpp
// basic_string_op_ref.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non-const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index of 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="basic_stringpointer"></a><a name="pointer"></a>basic_string::pointer

Typ, který poskytuje ukazatel na element znaku v řetězci nebo poli znaků.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `allocator_type::pointer`pro .

Pro `string`typ , je to ekvivalentní **char**<strong>\*</strong>.

### <a name="example"></a>Příklad

```cpp
// basic_string_pointer.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::pointer pstr1a = "In Here";
   char *cstr1b = "Out There";
   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1b is: " << cstr1b << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1b is: Out There.
```

## <a name="basic_stringpop_back"></a><a name="pop_back"></a>basic_string::pop_back

Vymaže poslední prvek řetězce.

```cpp
void pop_back();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce `erase(size() - 1)` efektivně volá vymazat poslední prvek sekvence, která musí být neprázdná.

## <a name="basic_stringpush_back"></a><a name="push_back"></a>basic_string::push_back

Přidá prvek na konec řetězce.

```cpp
void push_back(value_type char_value);
```

### <a name="parameters"></a>Parametry

*char_value*\
Znak, který má být přidán na konec řetězce.

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [insert](#insert)( [konec](#end), *char_value* ).

### <a name="example"></a>Příklad

```cpp
// basic_string_push_back.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "abc" );
   basic_string <char>::iterator str_Iter, str1_Iter;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // str1.push_back ( 'd' );
   str1_Iter = str1.end ( );
   str1_Iter--;
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;

   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;
}
```

```Output
The original string str1 is: abc
The last character-letter of the modified str1 is now: c
The modified string str1 is: abc
```

## <a name="basic_stringrbegin"></a><a name="rbegin"></a>basic_string::rbegin

Vrátí iterátor prvnímu prvku v obráceném řetězci.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor náhodného přístupu k prvnímu prvku v obráceném řetězci, adresování, co by byl poslední prvek v odpovídající unreversed řetězec.

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obráceným řetězcem stejně jako [begin](#begin) se používá s řetězcem.

Pokud `rbegin` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze objekt řetězce změnit. Pokud `rbegin` je vrácená hodnota `reverse_iterator`přiřazena objektu , lze objekt řetězce změnit.

`rbegin`lze inicializovat iteraci prostřednictvím řetězce zpět.

### <a name="example"></a>Příklad

```cpp
// basic_string_rbegin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Able was I ere I saw Elba" ), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rbegin ( );
   // str1_rIter--;
   cout << "The first character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_rIter = 'A';
   cout << "The first character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'A';

   // For an empty string, begin is equivalent to end
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The first character-letter of the reversed string str1 is: a
The full reversed string str1 is:
ablE was I ere I saw elbA
The first character-letter of the modified str1 is now: A
The full modified reversed string str1 is now:
AblE was I ere I saw elbA
The string str2 is empty.
```

## <a name="basic_stringreference"></a><a name="reference"></a>basic_string::odkaz

Typ, který poskytuje odkaz na prvek uložený v řetězci.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="remarks"></a>Poznámky

Typ `reference` lze změnit hodnotu prvku.

Typ je synonymem `allocator_type::reference`pro .

Pro `string`typ je ekvivalentní `chr&`.

### <a name="example"></a>Příklad

Viz příklad pro [at](#at) pro příklad, jak `reference`deklarovat a používat .

## <a name="basic_stringrend"></a><a name="rend"></a>basic_string::rend

Vrátí iterátor, který řeší umístění, které následuje poslední prvek v obráceném řetězci.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Návratová hodnota

Reverzní random-access iterátor, který řeší umístění následuje poslední prvek v obráceném řetězci.

### <a name="remarks"></a>Poznámky

`rend`se používá s obráceným řetězcem stejně jako [end](#end) se používá s řetězcem.

Pokud `rend` je vrácená hodnota `const_reverse_iterator`přiřazena aplikaci , nelze objekt řetězce změnit. Pokud `rend` je vrácená hodnota `reverse_iterator`přiřazena objektu , lze objekt řetězce změnit.

`rend`lze použít k testování, zda zpětný iterátor dosáhl konce svého řetězce.

Hodnota vrácená `rend` podle by neměla být odkazována.

### <a name="example"></a>Příklad

```cpp
// basic_string_rend.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Able was I ere I saw Elba"), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rend ( );
   str1_rIter--;
   cout << "The last character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_rIter = 'o';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the reversed string str1 is: A
The full reversed string str1 is:
ablE was I ere I saw elbA
The last character-letter of the modified str1 is now: o
The full modified reversed string str1 is now:
ablE was I ere I saw elbo
The string str2 is empty.
```

## <a name="basic_stringreplace"></a><a name="replace"></a>basic_string::nahradit

Nahradí prvky v řetězci na určené pozici zadanými znaky nebo znaky zkopírovanými z jiných oblastí nebo řetězců nebo řetězců C.

```cpp
basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type position_2,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    size_type count,
    value_type char_value);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    size_type number_2,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parametry

*Str*\
Řetězec, který má být zdrojem znaků pro řetězec operand.

*position_1*\
Index operand řetězce, ve kterém začíná nahrazení.

*number_1*\
Maximální počet znaků, které mají být nahrazeny v operand řetězci.

*position_2*\
Index řetězce parametru, ve kterém začíná kopírování.

*number_2*\
Maximální počet znaků, které mají být použity z parametru C-string.

*Ptr*\
Řetězec C, který má být zdrojem znaků pro řetězec operand.

*char_value*\
Znak, který má být zkopírován do operandového řetězce.

*první0*\
Iterátor adresování první znak, který má být odebrán v operand řetězec.

*last0*\
Iterátor adresování poslední znak, který má být odebrán v operand řetězec.

*První*\
Iterátor, const_pointer nebo const_iterator adresování první znak, který má být zkopírován v řetězci parametru.

*Poslední*\
Iterátor, const_pointer nebo const_iterator adresování poslední znak, který má být zkopírován v řetězci parametru.

*Počet*\
Počet, *char_value* kolikrát char_value je zkopírován do operandového řetězce.

### <a name="return-value"></a>Návratová hodnota

Řetězec operandu s vyrobenou náhradou.

### <a name="example"></a>Příklad

```cpp
// basic_string_replace.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first two member functions replace
   // part of the operand string with
   // characters from a parameter string or C-string
   string result1a, result1b;
   string s1o ( "AAAAAAAA" );
   string s1p ( "BBB" );
   const char* cs1p = "CCC";
   cout << "The operand string s1o is: " << s1o << endl;
   cout << "The parameter string s1p is: " << s1p << endl;
   cout << "The parameter C-string cs1p is: " << cs1p << endl;
   result1a = s1o.replace ( 1 , 3 , s1p );
   cout << "The result of s1o.replace ( 1 , 3 , s1p )\n is "
        << "the string: " << result1a << "." << endl;
   result1b = s1o.replace ( 5 , 3 , cs1p );
   cout << "The result of s1o.replace ( 5 , 3 , cs1p )\n is "
        << "the string: " << result1b << "." << endl;
   cout << endl;

   // The third & fourth member function replace
   // part of the operand string with characters
   // form part of a parameter string or C-string
   string result2a, result2b;
   string s2o ( "AAAAAAAA" );
   string s2p ( "BBB" );
   const char* cs2p = "CCC";
   cout << "The operand string s2o is: " << s2o << endl;
   cout << "The parameter string s1p is: " << s2p << endl;
   cout << "The parameter C-string cs2p is: " << cs2p << endl;
   result2a = s2o.replace ( 1 , 3 , s2p , 1 , 2 );
   cout << "The result of s2o.replace (1, 3, s2p, 1, 2)\n is "
        << "the string: " << result2a << "." << endl;
   result2b = s2o.replace ( 4 , 3 , cs2p , 1 );
   cout << "The result of s2o.replace (4 ,3 ,cs2p)\n is "
        << "the string: " << result2b << "." << endl;
   cout << endl;

   // The fifth member function replaces
   // part of the operand string with characters
   string result3a;
   string s3o ( "AAAAAAAA" );
   char ch3p = 'C';
   cout << "The operand string s3o is: " << s3o << endl;
   cout << "The parameter character c1p is: " << ch3p << endl;
   result3a = s3o.replace ( 1 , 3 , 4 , ch3p );
   cout << "The result of s3o.replace(1, 3, 4, ch3p)\n is "
        << "the string: " << result3a << "." << endl;
   cout << endl;

   // The sixth & seventh member functions replace
   // part of the operand string, delineated with iterators,
   // with a parameter string or C-string
   string s4o ( "AAAAAAAA" );
   string s4p ( "BBB" );
   const char* cs4p = "CCC";
   cout << "The operand string s4o is: " << s4o << endl;
   cout << "The parameter string s4p is: " << s4p << endl;
   cout << "The parameter C-string cs4p is: " << cs4p << endl;
   basic_string<char>::iterator IterF0, IterL0;
   IterF0 = s4o.begin ( );
   IterL0 = s4o.begin ( ) + 3;
   string result4a, result4b;
   result4a = s4o.replace ( IterF0 , IterL0 , s4p );
   cout << "The result of s1o.replace (IterF0, IterL0, s4p)\n is "
        << "the string: " << result4a << "." << endl;
   result4b = s4o.replace ( IterF0 , IterL0 , cs4p );
   cout << "The result of s4o.replace (IterF0, IterL0, cs4p)\n is "
        << "the string: " << result4b << "." << endl;
   cout << endl;

   // The 8th member function replaces
   // part of the operand string delineated with iterators
   // with a number of characters from a parameter C-string
   string s5o ( "AAAAAAAF" );
   const char* cs5p = "CCCBB";
   cout << "The operand string s5o is: " << s5o << endl;
   cout << "The parameter C-string cs5p is: " << cs5p << endl;
   basic_string<char>::iterator IterF1, IterL1;
   IterF1 = s5o.begin ( );
   IterL1 = s5o.begin ( ) + 4;
   string result5a;
   result5a = s5o.replace ( IterF1 , IterL1 , cs5p , 4 );
   cout << "The result of s5o.replace (IterF1, IterL1, cs4p ,4)\n is "
        << "the string: " << result5a << "." << endl;
   cout << endl;

   // The 9th member function replaces
   // part of the operand string delineated with iterators
   // with specified characters
   string s6o ( "AAAAAAAG" );
   char ch6p = 'q';
   cout << "The operand string s6o is: " << s6o << endl;
   cout << "The parameter character ch6p is: " << ch6p << endl;
   basic_string<char>::iterator IterF2, IterL2;
   IterF2 = s6o.begin ( );
   IterL2 = s6o.begin ( ) + 3;
   string result6a;
   result6a = s6o.replace ( IterF2 , IterL2 , 4 , ch6p );
   cout << "The result of s6o.replace (IterF1, IterL1, 4, ch6p)\n is "
        << "the string: " << result6a << "." << endl;
   cout << endl;

   // The 10th member function replaces
   // part of the operand string delineated with iterators
   // with part of a parameter string delineated with iterators
   string s7o ( "OOOOOOO" );
   string s7p ( "PPPP" );
   cout << "The operand string s7o is: " << s7o << endl;
   cout << "The parameter string s7p is: " << s7p << endl;
   basic_string<char>::iterator IterF3, IterL3, IterF4, IterL4;
   IterF3 = s7o.begin ( ) + 1;
   IterL3 = s7o.begin ( ) + 3;
   IterF4 = s7p.begin ( );
   IterL4 = s7p.begin ( ) + 2;
   string result7a;
   result7a = s7o.replace ( IterF3 , IterL3 , IterF4 , IterL4 );
   cout << "The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)\n is "
        << "the string: " << result7a << "." << endl;
   cout << endl;
}
```

```Output
The operand string s1o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs1p is: CCC
The result of s1o.replace ( 1 , 3 , s1p )
is the string: ABBBAAAA.
The result of s1o.replace ( 5 , 3 , cs1p )
is the string: ABBBACCC.

The operand string s2o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs2p is: CCC
The result of s2o.replace (1, 3, s2p, 1, 2)
is the string: ABBAAAA.
The result of s2o.replace (4 ,3 ,cs2p)
is the string: ABBAC.

The operand string s3o is: AAAAAAAA
The parameter character c1p is: C
The result of s3o.replace(1, 3, 4, ch3p)
is the string: ACCCCAAAA.

The operand string s4o is: AAAAAAAA
The parameter string s4p is: BBB
The parameter C-string cs4p is: CCC
The result of s1o.replace (IterF0, IterL0, s4p)
is the string: BBBAAAAA.
The result of s4o.replace (IterF0, IterL0, cs4p)
is the string: CCCAAAAA.

The operand string s5o is: AAAAAAAF
The parameter C-string cs5p is: CCCBB
The result of s5o.replace (IterF1, IterL1, cs4p ,4)
is the string: CCCBAAAF.

The operand string s6o is: AAAAAAAG
The parameter character ch6p is: q
The result of s6o.replace (IterF1, IterL1, 4, ch6p)
is the string: qqqqAAAAG.

The operand string s7o is: OOOOOOO
The parameter string s7p is: PPPP
The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)
is the string: OPPOOOO.
```

## <a name="basic_stringreserve"></a><a name="reserve"></a>basic_string::rezerva

Nastaví kapacitu řetězce na číslo alespoň tak velké jako zadané číslo.

```cpp
void reserve(size_type count = 0);
```

### <a name="parameters"></a>Parametry

*Počet*\
Počet znaků, pro které je vyhrazena paměť.

### <a name="remarks"></a>Poznámky

S dostatečnou kapacitu je důležité, protože přerozdělení je časově náročný proces a zruší platnost všech odkazů, ukazatelů a iterátorů, které odkazují na znaky v řetězci.

Koncept kapacity pro objekty typu řetězce je stejný jako pro objekty typu vektoru. Na rozdíl od `reserve` vector může být volána členská funkce zmenšit kapacitu objektu. Požadavek je nezávazný a může nebo nemusí dojít. Jako výchozí hodnota parametru je nula, volání `reserve` je nezávazný požadavek na zmenšení kapacity řetězce, aby se vešly počet znaků aktuálně v řetězci. Kapacita se nikdy nesníží pod aktuální počet znaků.

Volání `reserve` je jediný možný způsob, jak zmenšit kapacitu řetězce. Nicméně, jak je uvedeno výše, tento požadavek je nezávazný a nemusí dojít.

### <a name="example"></a>Příklad

```cpp
// basic_string_reserve.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1, sizerStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1, caprStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with added capacity
   str1.reserve ( 40 );
   sizerStr1 = str1.size ( );
   caprStr1 = str1.capacity ( );

   cout << "The string str1with augmented capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizerStr1 << "." << endl;
   cout << "The new capacity of string str1 is: "
        << caprStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with downsized capacity
   str1.reserve ( );
   basic_string <char>::size_type sizedStr1;
   basic_string <char>::size_type capdStr1;
   sizedStr1 = str1.size ( );
   capdStr1 = str1.capacity ( );

   cout << "The string str1 with downsized capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizedStr1 << "." << endl;
   cout << "The reduced capacity of string str1 is: "
        << capdStr1 << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The string str1with augmented capacity is: Hello world
The current size of string str1 is: 11.
The new capacity of string str1 is: 47.

The string str1 with downsized capacity is: Hello world
The current size of string str1 is: 11.
The reduced capacity of string str1 is: 47.
```

## <a name="basic_stringresize"></a><a name="resize"></a>basic_string::změna velikosti

Určuje novou velikost řetězce, připojení nebo vymazání prvků podle potřeby.

```cpp
void resize(
    size_type count,);

void resize(
    size_type count,
    value_type char_value);
```

### <a name="parameters"></a>Parametry

*Počet*\
Nová velikost řetězce.

*char_value*\
Hodnota, která připojené znaky jsou inicializovány s, pokud jsou požadovány další prvky.

### <a name="remarks"></a>Poznámky

Pokud výsledná velikost překročí maximální počet znaků, formulář `length_error`vyvolá .

### <a name="example"></a>Příklad

```cpp
// basic_string_resize.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ( "Hello world" );
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 2 elements: exclamations
   str1.resize ( str1.size ( ) + 2 , '!' );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   cout << "The current size of resized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of resized string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 20 elements:
   str1.resize ( str1.size ( ) + 20 );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   // note capacity increases automatically as required
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to downsize by 28 elements:
   str1.resize ( str1.size ( ) - 28 );
   cout << "The downsized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   // Compare size & capacity of a string after downsizing
   cout << "The current size of downsized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of downsized string str1 is: "
        << capStr1 << "." << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of resized string str1 is: 13.
The capacity of resized string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of modified string str1 is: 33.
The capacity of modified string str1 is: 47.

The downsized string str1 is: Hello
The current size of downsized string str1 is: 5.
The capacity of downsized string str1 is: 47.
```

## <a name="basic_stringreverse_iterator"></a><a name="reverse_iterator"></a>basic_string::reverse_iterator

Typ, který poskytuje odkaz na prvek uložený v řetězci.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Poznámky

Typ `reverse_iterator` lze použít k úpravě hodnoty znaku a slouží k iterátu prostřednictvím řetězce v opačném směru.

### <a name="example"></a>Příklad

Příklad pro [rbegin](#rbegin) naleznete v příkladu, `reverse_iterator`jak deklarovat a používat .

## <a name="basic_stringrfind"></a><a name="rfind"></a>basic_string::rfind

Prohledá řetězec v opačném směru pro první výskyt podřetězce, který odpovídá zadané posloupnosti znaků.

```cpp
size_type rfind(
    value_type char_value,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type rfind(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*char_value*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index pozice, na které má vyhledávání začít.

*Ptr*\
Řetězec znaků, který má členská funkce vyhledat.

*Počet*\
Počet znaků, počítaných vpřed od prvního znaku v řetězci znaků, které má členská funkce vyhledat.

*Str*\
Řetězec, který má členská funkce vyhledat.

### <a name="return-value"></a>Návratová hodnota

Index posledního výskytu prvního znaku podřetězce při zpětném prohledání při úspěšném zobrazení; v `npos`opačném případě .

### <a name="example"></a>Příklad

```cpp
// basic_string_rfind.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.rfind ( "e" , 9 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'e' found before the 9th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.rfind ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.rfind ( cstr2 , 30 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st element of 'perfect' "
           << "before\n the 30th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.rfind ( cstr2b , 30 );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "before\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "It is a nice day. I am happy." );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "nice";
   indexCh3a = str3.rfind ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st element of 'nice' "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'nice' was not found in str3 ."
           << endl;

   const char *cstr3b = "am";
   indexCh3b = str3.rfind ( cstr3b , indexCh3a + 25 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the next occurrence of 'am' in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'am' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "This perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.rfind ( str4a , 15 );
   if (indexCh4a != npos )
      cout << "The index of the 1st element of 'clear' "
           << "before\n the 15th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 "
           << "before the 15th position." << endl;

   string str4b ( "clear" );
   indexCh4b = str4.rfind ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found before the 9th position in str1 is: 8
The character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' before
the 30th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: It is a nice day. I am happy.
The index of the 1st element of 'nice' in str3 is: 8
The index of the next occurrence of 'am' in str3 begins at: 20

The original string str4 is: This perfectly unclear.
The substring 'clear' was not found in str4 before the 15th position.
The index of the 1st element of 'clear' in str4 is: 17
```

## <a name="basic_stringshrink_to_fit"></a><a name="shrink_to_fit"></a>basic_string::shrink_to_fit

Zahodí nadbytečnou kapacitu řetězce.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce eliminuje jakékoli nepotřebné úložiště v kontejneru.

## <a name="basic_stringsize"></a><a name="size"></a>basic_string::velikost

Vrátí aktuální počet prvků v řetězci.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka řetězce.

### <a name="example"></a>Příklad

```cpp
// basic_string_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringsize_type"></a><a name="size_type"></a>basic_string::size_type

Nepodepsaný podnosný typ, který může představovat počet prvků a indexů v řetězci.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="remarks"></a>Poznámky

je to ekvivalentní `allocator_type::size_type`.

Pro `string`typ je ekvivalentní `size_t`.

### <a name="example"></a>Příklad

```cpp
// basic_string_size_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" );

   basic_string <char>::size_type sizeStr1, capStr1;
   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   cout << "The current size of string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of string str1 is: " << capStr1
         << "." << endl;
}
```

```Output
The current size of string str1 is: 11.
The capacity of string str1 is: 15.
```

## <a name="basic_stringsubstr"></a><a name="substr"></a>basic_string::substr

Zkopíruje podřetězec maximálně některého počtu znaků z řetězce začínajícího od zadané pozice.

```cpp
basic_string<CharType, Traits, Allocator> substr(
    size_type offset = 0,
    size_type count = npos) const;
```

### <a name="parameters"></a>Parametry

*Posun*\
Index vyhledávající prvek na pozici, ze kterého je provedena kopie řetězce, s výchozí hodnotou 0.

*Počet*\
Počet znaků, které mají být zkopírovány, pokud jsou k dispozici.

### <a name="return-value"></a>Návratová hodnota

Podřetězec objekt, který je kopií prvků operandu řetězce začínající na pozici určené prvním argumentem.

### <a name="example"></a>Příklad

```cpp
// basic_string_substr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ("Heterological paradoxes are persistent.");
   cout << "The original string str1 is: \n " << str1
        << endl << endl;

   basic_string <char> str2 = str1.substr ( 6 , 7 );
   cout << "The substring str1 copied is: " << str2
        << endl << endl;

   basic_string <char> str3 = str1.substr (  );
   cout << "The default substring str3 is: \n " << str3
        <<  "\n which is the entire original string." << endl;
}
```

```Output
The original string str1 is:
Heterological paradoxes are persistent.

The substring str1 copied is: logical

The default substring str3 is:
Heterological paradoxes are persistent.
which is the entire original string.
```

## <a name="basic_stringswap"></a><a name="swap"></a>basic_string::swap

Vyměňte obsah dvou řetězců.

```cpp
void swap(
    basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

*Str*\
Zdrojový řetězec, jehož prvky mají být vyměněny s těmi v cílovém řetězci.

### <a name="remarks"></a>Poznámky

Pokud řetězce, které jsou prokládané mají stejný `swap` objekt alokátoru, členská funkce:

- Vyskytuje se v konstantním čase.

- Vyvolá žádné výjimky.

- Zruší platnost žádné odkazy, ukazatele nebo iterátory, které označují prvky ve dvou řetězců.

V opačném případě provádí počet přiřazení prvků a volání konstruktoru úměrná počtu prvků ve dvou řízených sekvencích.

### <a name="example"></a>Příklad

```cpp
// basic_string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;

   s1.swap ( s2 );
   cout << "After swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.
After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="basic_stringtraits_type"></a><a name="traits_type"></a>basic_string::traits_type

Typ pro znakové znaky prvků uložených v řetězci.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro druhý `Traits`parametr šablony .

Pro `string`typ je ekvivalentní **char_traits\<char>**.

### <a name="example"></a>Příklad

Příklad pro [kopii](../standard-library/char-traits-struct.md#copy) naleznete v příkladu, `traits_type`jak deklarovat a používat .

## <a name="basic_stringvalue_type"></a><a name="value_type"></a>basic_string::value_type

Typ, který představuje typ znaků uložených v řetězci.

```cpp
typedef typename allocator_type::value_type value_type;
```

### <a name="remarks"></a>Poznámky

Je ekvivalentní `traits_type::char_type` a je ekvivalentní **char** pro `string`objekty typu .

### <a name="example"></a>Příklad

```cpp
// basic_string_value_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   basic_string<char>::value_type ch1 = 'G';

   char ch2 = 'H';

   cout << "The character ch1 is: " << ch1 << "." << endl;
   cout << "The character ch2 is: " << ch2 << "." << endl;
}
```

```Output
The character ch1 is: G.
The character ch2 is: H.
```

## <a name="see-also"></a>Viz také

[\<řetězec>](../standard-library/string.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
