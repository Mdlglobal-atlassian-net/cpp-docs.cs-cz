---
title: basic_string_view – třída
ms.date: 04/20/2019
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::iterator
- xstring/std::basic_string_view::npos
- xstring/std::basic_string_view::pointer
- xstring/std::basic_string_view::reference
- xstring/std::basic_string_view::reverse_iterator
- xstring/std::basic_string_view::size_type
- xstring/std::basic_string_view::traits_type
- xstring/std::basic_string_view::value_type
- xstring/std::basic_string_view::append
- xstring/std::basic_string_view::assign
- xstring/std::basic_string_view::at
- xstring/std::basic_string_view::back
- xstring/std::basic_string_view::begin
- xstring/std::basic_string_view::c_str
- xstring/std::basic_string_view::capacity
- xstring/std::basic_string_view::cbegin
- xstring/std::basic_string_view::cend
- xstring/std::basic_string_view::clear
- xstring/std::basic_string_view::compare
- xstring/std::basic_string_view::copy
- xstring/std::basic_string_view::_Copy_s
- xstring/std::basic_string_view::crbegin
- xstring/std::basic_string_view::crend
- xstring/std::basic_string_view::data
- xstring/std::basic_string_view::empty
- xstring/std::basic_string_view::end
- xstring/std::basic_string_view::erase
- xstring/std::basic_string_view::find
- xstring/std::basic_string_view::find_first_not_of
- xstring/std::basic_string_view::find_first_of
- xstring/std::basic_string_view::find_last_not_of
- xstring/std::basic_string_view::find_last_of
- xstring/std::basic_string_view::front
- xstring/std::basic_string_view::get_allocator
- xstring/std::basic_string_view::insert
- xstring/std::basic_string_view::length
- xstring/std::basic_string_view::max_size
- xstring/std::basic_string_view::pop_back
- xstring/std::basic_string_view::push_back
- xstring/std::basic_string_view::rbegin
- xstring/std::basic_string_view::rend
- xstring/std::basic_string_view::remove_prefix
- xstring/std::basic_string_view::remove_suffix
- xstring/std::basic_string_view::replace
- xstring/std::basic_string_view::reserve
- xstring/std::basic_string_view::resize
- xstring/std::basic_string_view::rfind
- xstring/std::basic_string_view::shrink_to_fit
- xstring/std::basic_string_view::size
- xstring/std::basic_string_view::substr
- xstring/std::basic_string_view::swap
helpviewer_keywords:
- std::basic_string_view
- std::basic_string_view, allocator_type
- std::basic_string_view, const_iterator
- std::basic_string_view, const_pointer
- std::basic_string_view, const_reference
- std::basic_string_view, const_reverse_iterator
- std::basic_string_view, difference_type
- std::basic_string_view, iterator
- std::basic_string_view, npos
- std::basic_string_view, pointer
- std::basic_string_view, reference
- std::basic_string_view, reverse_iterator
- std::basic_string_view, size_type
- std::basic_string_view, traits_type
- std::basic_string_view, value_type
- std::basic_string_view, append
- std::basic_string_view, assign
- std::basic_string_view, at
- std::basic_string_view, back
- std::basic_string_view, begin
- std::basic_string_view, c_str
- std::basic_string_view, capacity
- std::basic_string_view, cbegin
- std::basic_string_view, cend
- std::basic_string_view, clear
- std::basic_string_view, compare
- std::basic_string_view, copy
- std::basic_string_view, crbegin
- std::basic_string_view, crend
- std::basic_string_view, data
- std::basic_string_view, empty
- std::basic_string_view, end
- std::basic_string_view, erase
- std::basic_string_view, find
- std::basic_string_view, find_first_not_of
- std::basic_string_view, find_first_of
- std::basic_string_view, find_last_not_of
- std::basic_string_view, find_last_of
- std::basic_string_view, front
- std::basic_string_view, get_allocator
- std::basic_string_view, insert
- std::basic_string_view, length
- std::basic_string_view, max_size
- std::basic_string_view, pop_back
- std::basic_string_view, push_back
- std::basic_string_view, rbegin
- std::basic_string_view, rend
- std::basic_string_view, remove_prefix
- std::basic_string_view, remove_suffix
- std::basic_string_view, replace
- std::basic_string_view, reserve
- std::basic_string_view, resize
- std::basic_string_view, rfind
- std::basic_string_view, shrink_to_fit
- std::basic_string_view, size
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 7a53a27e11088ab02f873613794d6799851ca373
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416172"
---
# <a name="basic_string_view-class"></a>basic_string_view – třída

Šablona třídy `basic_string_view<charT>` byla přidána do C++ 17, aby sloužila jako bezpečný a účinný způsob, jak funkce přijímat různé nesouvisející typy řetězců bez funkce, která by měla být založena na těchto typech. Třída obsahuje nevlastnící ukazatel na souvislou sekvenci znakových dat a délku, která určuje počet znaků v sekvenci. Bez ohledu na to, jestli je sekvence zakončená hodnotou null, se neprovádí žádný předpoklad.

Standardní knihovna definuje několik specializací na základě typu prvků:

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

V tomto dokumentu pojem "string_view" odkazuje obecně na některý z těchto definice typedef.

String_view popisuje minimální společné rozhraní nezbytné pro čtení řetězcových dat. Poskytuje přístup k podkladovým datům const; neprovede žádné kopie (s výjimkou funkce `copy`). Data mohou nebo nemusí obsahovat hodnoty null (' \ 0 ') na libovolné pozici. String_view nemá žádnou kontrolu nad životností objektu. Je zodpovědností volajícího, aby se zajistilo, že základní řetězcová data jsou platná.

Funkce, která přijímá parametr typu string_view, může být vytvořena pro práci s jakýmkoli řetězcovým typem, bez toho, aby se funkce nastavila na šablonu nebo omezila funkce na určitou podmnožinu typů řetězců. Jediným požadavkem je, že implicitní převod existuje z typu řetězce na string_view. Všechny standardní řetězcové typy jsou implicitně převoditelné na string_view, které obsahují stejný typ elementu. Jinými slovy `std::string` je převoditelné na `string_view`, ale ne na `wstring_view`.

Následující příklad ukazuje funkci, která není šablonou, `f`, která přebírá parametr typu `wstring_view`. Může být volána s argumenty typu `std::wstring`, `wchar_t*`a `winrt::hstring`.

```cpp
// compile with: /std:c++17
// string_view that uses elements of wchar_t
void f(wstring_view);

// pass a std::wstring:
const std::wstring& s { L"Hello" };
f(s);

// pass a C-style null-terminated string (string_view is not null-terminated):
const wchar_t* ns = L"Hello";
f(ns);

// pass a C-style character array of len characters (excluding null terminator):
const wchar_t* cs { L"Hello" };
size_t len { 5 };
f({cs,len});

// pass a WinRT string
winrt::hstring hs { L"Hello" };
f(hs);
```

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Traits = char_traits<CharType>>
class basic_string_view;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ znaků, které jsou uloženy v string_view. C++ Standardní knihovna poskytuje následující definice TypeDef pro specializace této šablony.
- [string_view](../standard-library/string-view-typedefs.md#string_view) pro elementy typu **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view)pro **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) pro **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) pro **char32_t**.

\ *vlastností*
Výchozí hodnota [char_traits](char-traits-struct.md)<*CharType*>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_string_view](#basic_string_view)|Vytvoří string_view, která je prázdná nebo jinak odkazuje na všechny nebo jen některé jiné datové objekty řetězce nebo na pole znaků ve stylu jazyka C.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|**const_iterator**|Iterátor náhodného přístupu, který může číst elementy **const** .|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**iterátor**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**ukazatele**|`using pointer = value_type*;`|
|**odkaz**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Členské operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí string_view nebo převoditelné objekty řetězce k jinému string_view.|
|[operátor\[\]](#op_at)|Vrátí prvek na zadaném indexu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Počínaje](#at)|Vrátí const_reference k elementu v zadaném umístění.|
|[návrat](#back)|Vrátí const_reference k poslednímu prvku.|
|[ifunctiondiscovery](#begin)|Vrátí konstantní iterátor adresující první prvek. (string_views jsou neměnné.)|
|[cbegin](#cbegin)|Totéž jako na [začátku](#begin).|
|[cend](#cend)|Vrátí konstantní iterátor, který odkazuje na jeden za poslední prvek.|
|[kopií](#copy)|Kopíruje maximálně zadaný počet znaků z indexované pozice ve zdrojovém string_view do cílového pole znaků. (Nedoporučuje se. Místo toho použijte _Copy_s.)|
|[_Copy_s](#_copy_s)|Zabezpečená funkce kopírování CRT|
|[porovnán](#compare)|Porovná string_view se zadaným string_view a určí, jestli jsou stejné, nebo pokud je jedna lexikograficky menší než druhá.|
|[crbegin –](#crbegin)|Stejné jako [rbegin](#rbegin).|
|[crend](#crend)|Stejné jako [rend](#rend).|
|[údajů](#data)|Vrací nezpracovaný nevlastnící ukazatel na posloupnost znaků.|
|[obsahovat](#empty)|Testuje, zda string_view obsahuje znaky.|
|[účelu](#end)|Stejné jako [cend](#cend).|
|[find](#find)|Vyhledá v směrem nahoru směr prvního výskytu podřetězce, který odpovídá zadané posloupnosti znaků.|
|[find_first_not_of](#find_first_not_of)|Vyhledá první znak, který není libovolný prvek zadaného string_view nebo převoditelné řetězcové objekty.|
|[find_first_of](#find_first_of)|Vyhledá první znak, který odpovídá jakémukoli prvku zadaného string_view nebo objektu s převoditelné řetězce.|
|[find_last_not_of](#find_last_not_of)|Vyhledá poslední znak, který není libovolný prvek zadaného string_view nebo převoditelné řetězcové objekty.|
|[find_last_of](#find_last_of)|Vyhledá poslední znak, který je prvkem zadaného string_view nebo převoditelné řetězcové objekty.|
|[dopředu](#front)|Vrátí const_reference k prvnímu prvku.|
|[časový](#length)|Vrátí aktuální počet prvků.|
|[max_size](#max_size)|Vrátí maximální počet znaků, které může string_view obsahovat.|
|[rbegin](#rbegin)|Vrátí konstantní iterátor, který adresuje první prvek v obráceném string_view.|
|[remove_prefix](#remove_prefix)|Přesune ukazatel směrem nahoru o zadaný počet prvků.|
|[remove_suffix](#remove_suffix)|Zmenší velikost zobrazení o zadaný počet prvků počínaje od zpátky.|
|[rend](#rend)|Vrátí konstantní iterátor, který odkazuje na jeden za poslední prvek v obráceném string_view.|
|[rfind](#rfind)|Vyhledá string_view v obráceném pořadí pro první výskyt podřetězce, který odpovídá zadané posloupnosti znaků.|
|[hodnota](#size)|Vrátí aktuální počet prvků.|
|[substr –](#substr)|Vrátí podřetězec zadané délky začínající zadaným indexem.|
|[adresu](#swap)|Výměna obsahu dvou string_views.|

## <a name="remarks"></a>Poznámky

Pokud je funkce požádána o vygenerování sekvence delší než [max_size](#max_size) prvky, funkce ohlásí chybu délky vyvoláním objektu typu [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Požadavky

[std: c++ 17](../build/reference/std-specify-language-standard-version.md) nebo novější

**Záhlaví:** \<string_view >

**Obor názvů:** std

## <a name="at"></a>basic_string_view:: at

Vrátí const_reference k znaku v zadaném indexu založeném na 0.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parametry

*posunutí*\
Index elementu, na který se má odkazovat

### <a name="return-value"></a>Návratová hodnota

Const_reference k znaku na pozici určené indexem parametru.

### <a name="remarks"></a>Poznámky

První prvek má index nula a následující prvky jsou následně indexovány po kladné celé číslo, takže string_view délky *n* má *n*-tý element indexovaný číslem *n-* 1. **v** vyvolá výjimku pro neplatné indexy, na rozdíl od [operátoru\[\]](#op_at). 

Obecně doporučujeme, aby **v** případě sekvencí, jako je například `std::vector` a string_view, neměly být nikdy použity. Neplatný index předaný sekvenci je logická chyba, která by měla být zjištěna a opravena během vývoje. Pokud program není naprosto jistý, že jeho indexy jsou platné, měli byste je otestovat, nevolat v () a spoléhat na výjimky pro obranu před nepozorný programováním.

Další informace naleznete v tématu [basic_string_view:: operator\[\]](#op_at) .

### <a name="example"></a>Příklad

```cpp
// basic_string_view_at.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>

int main()
{
    using namespace std;

    const string_view  str1("Hello world");
    string_view::const_reference refStr2 = str1.at(8); // 'r'
}
```

## <a name="back"></a>basic_string_view:: back

Vrátí const_reference k poslednímu prvku.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Const_reference k poslednímu prvku v string_view.

### <a name="remarks"></a>Poznámky

Vyvolá výjimku, pokud je string_view prázdné.

Mějte na paměti, že po změně string_view, například voláním `remove_suffix`, pak element vrácený touto funkcí již není posledním prvkem v podkladových datech.

### <a name="example"></a>Příklad

String_view, která je vytvořena pomocí řetězcového literálu jazyka C, nezahrnuje ukončující hodnotu null, takže v následujícím příkladu `back` vrátí ' p ' a ne ' \ 0 '.

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p 
```

Vložené hodnoty null se zpracují jako jakýkoli jiný znak:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_view"></a>basic_string_view:: basic_string_view

Vytvoří string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parametry

\ *str*
Ukazatel na hodnoty znaků.

*délka*\
Počet znaků, které mají být zahrnuty do zobrazení.

## <a name="remarks"></a>Poznámky

Konstruktory s parametrem charT * předpokládají, že vstup je zakončený hodnotou null, ale ukončovací hodnota null není zahrnuta v string_view.

Můžete také vytvořit string_view s literálem. Viz [Operator "" sv](string-view-operators.md#op_sv).

## <a name="begin"></a>basic_string_view:: begin

Stejné jako [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota
Vrací const_iterator adresování prvního prvku.

## <a name="cbegin"></a>basic_string_view:: cbegin

Vrátí const_iterator, který adresuje první prvek v rozsahu.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor **náhodného** přístupu, který odkazuje na první prvek rozsahu nebo umístění hned za konec prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

## <a name="cend"></a>basic_string_view:: cend

Vrátí const_iterator, který adresuje umístění hned za posledním prvkem v rozsahu.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor náhodného přístupu **const** , který odkazuje hned za konec rozsahu.

### <a name="remarks"></a>Poznámky

Hodnota vrácená `cend` by neměla být zpětně odkazovaná.

## <a name="compare"></a>basic_string_view:: Compare

Provede porovnání rozlišující malá a velká písmena se zadaným string_view (nebo typem konvertibilní řetězec) k určení, zda jsou dva objekty stejné nebo pokud je jedna lexikograficky menší než druhá. [Operátory\<string_view >](string-view-operators.md) používají tuto členskou funkci k provádění porovnání.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Parametry

*strv*\
String_view, které mají být porovnány s tímto string_view.

\ *POS*
Index tohoto string_view, ve kterém je zahájeno porovnání.

*počet*\
Maximální počet znaků z této string_view, které se mají porovnat.

*num2*\
Maximální počet znaků z *Strv* , které se mají porovnat.

*posunutí*\
Index *Strv* , na kterém začíná porovnávání.

\ *PTR*
Řetězec jazyka C, který má být porovnán s tímto string_view.

### <a name="return-value"></a>Návratová hodnota

Záporná hodnota, pokud je tato string_view menší než *Strv* nebo *PTR*; nula, pokud jsou dvě sekvence znaků stejné; nebo kladnou hodnotu, pokud je tato string_view větší než *Strv* nebo *PTR*.

### <a name="remarks"></a>Poznámky

Členské funkce `compare` provádějí porovnání rozlišovat velká a malá písmena obou sekvencí znaků. 

### <a name="example"></a>Příklad

```cpp
// basic_string_view_compare.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>
#include <string>

using namespace std;

string to_alpha(int result)
{
   if (result < 0) return " less than ";
   else if (result == 0) return " equal to ";
   else return " greater than ";
}

int main()
{
   // The first member function compares
   // two string_views
   string_view sv_A("CAB");
   string_view sv_B("CAB");
   cout << "sv_A is " << sv_A << endl;
   cout << "sv_B is " << sv_B << endl;
   int comp1 = sv_A.compare(sv_B);
   cout << "sv_A is" << to_alpha(comp1) << "sv_B.\n";

   // The second member function compares part of
   // an operand string_view to another string_view
   string_view sv_C("AACAB");
   string_view sv_D("CAB");
   cout << "sv_C is: " << sv_C << endl;
   cout << "sv_D is: " << sv_D << endl;
   int comp2a = sv_C.compare(2, 3, sv_D);
   cout << "The last three characters of sv_C are" 
       << to_alpha(comp2a) << "sv_D.\n";

   int comp2b = sv_C.compare(0, 3, sv_D);
   cout << "The first three characters of sv_C are" 
       << to_alpha(comp2b) << "sv_D.\n";

   // The third member function compares part of
   // an operand string_view to part of another string_view
   string_view sv_E("AACAB");
   string_view sv_F("DCABD");
   cout << "sv_E: " << sv_E << endl;
   cout << "sv_F is: " << sv_F << endl;
   int comp3a = sv_E.compare(2, 3, sv_F, 1, 3);
   cout << "The three characters from position 2 of sv_E are"
       << to_alpha(comp3a) 
       << "the 3 characters of sv_F from position 1.\n";

   // The fourth member function compares
   // an operand string_view to a C string
   string_view sv_G("ABC");
   const char* cs_A = "DEF";
   cout << "sv_G is: " << sv_G << endl;
   cout << "cs_A is: " << cs_A << endl;
   int comp4a = sv_G.compare(cs_A);
   cout << "sv_G is" << to_alpha(comp4a) << "cs_A.\n";

   // The fifth member function compares part of
   // an operand string_view to a C string
   string_view sv_H("AACAB");
   const char* cs_B = "CAB";
   cout << "sv_H is: " << sv_H << endl;
   cout << "cs_B is: " << cs_B << endl;
   int comp5a = sv_H.compare(2, 3, cs_B);
   cout << "The last three characters of sv_H are"
      << to_alpha(comp5a) << "cs_B.\n";

   // The sixth member function compares part of
   // an operand string_view to part of an equal length of
   // a C string
   string_view sv_I("AACAB");
   const char* cs_C = "ACAB";
   cout << "sv_I is: " << sv_I << endl;
   cout << "cs_C: " << cs_C << endl;
   int comp6a = sv_I.compare(1, 3, cs_C, 3);
   cout << "The 3 characters from position 1 of sv_I are"
      << to_alpha(comp6a) << "the first 3 characters of cs_C.\n";
}
```

```Output
sv_A is CAB
sv_B is CAB
sv_A is equal to sv_B.
sv_C is: AACAB
sv_D is: CAB
The last three characters of sv_C are equal to sv_D.
The first three characters of sv_C are less than sv_D.
sv_E: AACAB
sv_F is: DCABD
The three characters from position 2 of sv_E are equal to the 3 characters of sv_F from position 1.
sv_G is: ABC
cs_A is: DEF
sv_G is less than cs_A.
sv_H is: AACAB
cs_B is: CAB
The last three characters of sv_H are equal to cs_B.
sv_I is: AACAB
cs_C: ACAB
The 3 characters from position 1 of sv_I are equal to the first 3 characters of cs_C.
```

## <a name="copy"></a>basic_string_view:: Copy

Kopíruje maximálně zadaný počet znaků z indexované pozice ve zdrojovém string_view do cílového pole znaků. Doporučujeme místo toho použít funkci Secure [basic_string_view:: _Copy_s](#_copy_s) .

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

\ *PTR*
Cílové pole znaků, do kterého mají být kopírovány elementy.

*počet*\
Počet znaků, které mají být zkopírovány nejvíce ze zdrojového string_view.

*posunutí*\
Počáteční pozice ve zdrojovém string_view, ze které mají být kopie provedeny.

### <a name="return-value"></a>Návratová hodnota

Počet skutečně zkopírovaných znaků.

### <a name="remarks"></a>Poznámky

Znak null není připojen ke konci kopie.

## <a name="_copy_s"></a>basic_string_view:: _Copy_s

Zabezpečená funkce kopírování CRT, která se má použít místo [kopírování](#copy)

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parametry

*cílový*\
Cílové pole znaků, do kterého mají být kopírovány elementy.

*dest_size*\
Velikost *cíle.*

_ *Spočítat* počet znaků, které mají být zkopírovány nejvíce ze zdrojového řetězce.

*_Off*\
Počáteční pozice ve zdrojovém řetězci, ze které mají být provedeny kopie.

### <a name="return-value"></a>Návratová hodnota

Počet skutečně zkopírovaných znaků.

### <a name="remarks"></a>Poznámky

Znak null není připojen ke konci kopie.

Další informace naleznete v tématu [c-Runtime-Library/Security-Features-in-the-CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="crbegin"></a>basic_string_view:: crbegin –

Vrátí const_reverse_iterator, který adresuje první prvek v obráceném string_view.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Const_reverse_iterator, který adresuje první prvek v obráceném string_view. 

## <a name="crend"></a>basic_string_view:: crend

Stejné jako [rend](#rend). 

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí const_reverse_iterator, který adresuje po konci reverzního string_view.

## <a name="data"></a>basic_string_view::d ATA

Vrací nezpracovaný nevlastnící ukazatel na posloupnost znaků const objektu, který byl použit k vytvoření string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na konstantu na první prvek sekvence znaků.

### <a name="remarks"></a>Poznámky

Ukazatel nemůže měnit znaky.

Sekvence string_viewch znaků není nutně zakončená hodnotou null. Návratový typ pro `data` není platný řetězec jazyka C, protože není připojen žádný znak null. Znak null ' \ 0 ' nemá žádný zvláštní význam v objektu typu string_view a může být součástí objektu string_view stejným způsobem jako jakýkoli jiný znak.

## <a name="empty"></a>basic_string_view:: Empty

Testuje, zda string_view obsahuje znaky nebo ne.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud objekt string_view neobsahuje žádné znaky; **false** , pokud má alespoň jeden znak.

### <a name="remarks"></a>Poznámky

Členská funkce je ekvivalentní [velikosti](#size)() = = 0.

## <a name="end"></a>basic_string_view:: end

Vrátí const_iterator s náhodným přístupem, který odkazuje na jeden za poslední prvek.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí const_iterator s náhodným přístupem, který odkazuje na jeden za poslední prvek.

### <a name="remarks"></a>Poznámky

`end` slouží k otestování, zda const_iterator dosáhl konce jeho string_view. Hodnota vrácená `end` by neměla být zpětně odkazovaná.

## <a name="find"></a>basic_string_view:: Find

Vyhledá string_view v směrem nahoru pro první výskyt znaku nebo podřetězce, který odpovídá zadané posloupnosti znaků.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

\ *str*
String_view, pro kterou má členská funkce Hledat

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*posunutí*\
Index, na kterém má začít hledání.

\ *PTR*
Řetězec jazyka C, pro který má členská funkce Hledat.

*počet*\
Počet znaků v *PTR*, počítáno od prvního znaku.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

## <a name="find_first_not_of"></a>basic_string_view:: find_first_not_of

Vyhledá první znak, který není prvkem zadaného string_view nebo převoditelné řetězcové objekty.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

\ *str*
String_view, pro kterou má členská funkce Hledat

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*posunutí*\
Index, na kterém má začít hledání.

\ *PTR*
Řetězec jazyka C, pro který má členská funkce Hledat.

*počet*\
Počet znaků, který je počítán od prvního znaku v řetězci jazyka C, pro který má členská funkce Hledat.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

## <a name="find_first_of"></a>basic_string_view:: find_first_of

Vyhledá první znak, který odpovídá jakémukoli prvku zadaného string_view.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*posunutí*\
Index, na kterém má začít hledání.

\ *PTR*
Řetězec jazyka C, pro který má členská funkce Hledat.

*počet*\
Počet znaků, který je počítán od prvního znaku v řetězci jazyka C, pro který má členská funkce Hledat.

\ *str*
String_view, pro kterou má členská funkce Hledat

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

## <a name="find_last_not_of"></a>basic_string_view:: find_last_not_of

Vyhledá poslední znak, který není žádným prvkem zadaného string_view.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

\ *str*
String_view, pro kterou má členská funkce Hledat

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*posunutí*\
Index, ve kterém má být hledání dokončeno.

\ *PTR*
Řetězec jazyka C, pro který má členská funkce Hledat.

*počet*\
Počet znaků, který se počítá od prvního znaku v *PTR*.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `string_view::npos`.

## <a name="find_last_of"></a>basic_string_view:: find_last_of

Vyhledá poslední znak, který odpovídá jakémukoli prvku zadaného string_view.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

\ *str*
String_view, pro kterou má členská funkce Hledat

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*posunutí*\
Index, ve kterém má být hledání dokončeno.

\ *PTR*
Řetězec jazyka C, pro který má členská funkce Hledat.

*počet*\
Počet znaků, který je počítán od prvního znaku v řetězci jazyka C, pro který má členská funkce Hledat.

### <a name="return-value"></a>Návratová hodnota

Index posledního znaku podřetězce, který byl nalezen v případě úspěchu; jinak `npos`.

## <a name="front"></a>basic_string_view:: front

Vrátí const_reference k prvnímu prvku.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Const_reference k prvnímu prvku.

### <a name="remarks"></a>Poznámky

Vyvolá výjimku, pokud je string_view prázdné.

## <a name="length"></a>basic_string_view:: Length

Vrátí aktuální počet prvků.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce je stejná jako [Velikost](#size).

## <a name="max_size"></a>basic_string_view:: max_size

Vrátí maximální počet znaků, které může string_view obsahovat.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet znaků, které může string_view obsahovat.

### <a name="remarks"></a>Poznámky

Výjimka typu [length_error](../standard-library/length-error-class.md) je vyvolána, když operace vytvoří string_view s délkou větší než `max_size()`.

## <a name="op_eq"></a>basic_string_view:: operator =

Přiřadí string_view nebo převoditelné objekty řetězce k jinému string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```
### <a name="example"></a>Příklad

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```
## <a name="op_at"></a>basic_string_view:: operator [] – operátor

Poskytuje const_reference ke znaku se zadaným indexem.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parametry

*posunutí*\
Index elementu, na který se má odkazovat

### <a name="return-value"></a>Návratová hodnota

Const_reference k znaku na pozici určené indexem parametru.

### <a name="remarks"></a>Poznámky

První prvek má index nula a následující prvky jsou následně indexovány po kladné celé číslo, takže string_view délky *n* má *n*-tý element indexovaný číslem *n* -1.

`operator[]` je rychlejší než členská funkce [v](#at) pro poskytnutí přístupu pro čtení k prvkům string_view.

`operator[]` nekontroluje, zda je index předaný jako argument platný. Neplatný index předaný do `operator[]` má za následek nedefinované chování.

Vrácené odkazy mohou být zrušeny, pokud je podkladová data změněna nebo smazána vlastníkem objektu.

Při kompilaci s [\_iterátor\_úroveň\_ladění](../standard-library/iterator-debug-level.md) nastavenou na 1 nebo 2, dojde k chybě za běhu, pokud se pokusíte o přístup k prvku mimo hranice string_view. Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

## <a name="rbegin"></a>basic_string_view:: rbegin

Vrátí konstantní iterátor na první prvek v obráceném string_view.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor náhodného přístupu k prvnímu prvku v obráceném string_view a adresování, co by bylo posledním prvkem v odpovídající nereverzní string_view.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obráceným string_view stejně jako [Begin](#begin) se používá s string_view. `rbegin` lze použít k inicializaci iterace zpět.

## <a name="remove_prefix"></a>basic_string_view:: remove_prefix

Přesune ukazatel směrem nahoru o zadaný počet prvků.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Poznámky

Ponechá podkladová data beze změny. Přesune ukazatel string_view směrem nahoru o n prvků a nastaví soukromý `size` datový člen na velikost-n.

## <a name="remove_suffix"></a>basic_string_view:: remove_suffix

Zmenší velikost zobrazení o zadaný počet prvků počínaje od zpátky.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Poznámky

Ponechá podkladová data a ukazatel na ni beze změny. Nastaví soukromý datový člen `size` na velikost-n.

## <a name="rend"></a>basic_string_view:: rend

Vrátí konstantní iterátor, který odkazuje na jeden za poslední prvek v obráceném string_view.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Iterátor s náhodným přístupem const, který odkazuje na jeden za poslední prvek v obráceném string_view.

### <a name="remarks"></a>Poznámky

`rend` se používá s obráceným string_view stejně jako [End](#end) se používá s string_view. `rend` lze použít k otestování, zda reverzní iterátor dosáhl konce jeho string_view. Hodnota vrácená `rend` by neměla být zpětně odkazovaná.

## <a name="rfind"></a>basic_string_view:: rfind

Vyhledá string_view v obráceném pořadí pro podřetězec, který odpovídá zadané posloupnosti znaků.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*posunutí*\
Index, na kterém má začít hledání.

\ *PTR*
Řetězec jazyka C, pro který má členská funkce Hledat.

*počet*\
Počet znaků, který je počítán od prvního znaku v řetězci jazyka C, pro který má členská funkce Hledat.

\ *str*
String_view, pro kterou má členská funkce Hledat

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku podřetězce po úspěchu; jinak `npos`.

## <a name="size"></a>basic_string_view:: size

Vrátí počet prvků v string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Délka string_view

### <a name="remarks"></a>Poznámky

String_view může změnit jeho délku, například pomocí `remove_prefix` a `remove_suffix`. Vzhledem k tomu, že se nezmění základní řetězcová data, není velikost string_view nutně velikost podkladových dat.

## <a name="substr"></a>basic_string_view:: substr

Vrátí string_view, který představuje (nejvíce) zadaný počet znaků ze zadané pozice.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parametry

*posunutí*\
Index, který vyhledává prvek na pozici, ze které je vytvořena kopie, s výchozí hodnotou 0.

*počet*\
Počet znaků, které mají být zahrnuty v podřetězci, pokud jsou k dispozici.

### <a name="return-value"></a>Návratová hodnota

Objekt string_view, který představuje zadanou dílčí sekvenci prvků.

## <a name="swap"></a>basic_string_view:: swap

Vyměňuje dvě string_views, jinými slovy ukazatelé na podkladová řetězcová data a hodnoty velikosti.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parametry

*sv*\
Zdroj string_view, jehož hodnoty ukazatele a velikosti mají být vyměněny pomocí cílového string_view.

## <a name="see-also"></a>Viz také

[\<string_view >](../standard-library/string-view.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
