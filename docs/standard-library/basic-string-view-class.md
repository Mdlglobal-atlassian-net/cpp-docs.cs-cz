---
title: basic_string_view třídy
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
ms.openlocfilehash: 0ac5e3d528881f7b1caa0a1dcdae0161a6777e57
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346635"
---
# <a name="basicstringview-class"></a>basic_string_view třídy

Šablona třídy `basic_string_view<charT>` bylo přidáno v C ++ 17, která bude sloužit jako bezpečný a účinný způsob, jakým funkce tak, aby přijímal různými typy řetězců nesouvisející aniž by museli být založena na těchto typů funkce. Třída drží ukazatel vlastnící souvislý sekvence znaková data mezery a délkou, která určuje počet znaků v sekvenci. Žádné předpokladů se provádí s ohledem na, jestli je sekvence zakončená hodnotou null.

Standardní knihovna definuje několik specializace podle typu prvků:

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

V tomto dokumentu termín "string_view" obvykle odkazuje na všechny tyto funkce TypeDef.

String_view popisuje minimální společné rozhraní nezbytné číst data řetězce. Poskytuje přístup const v podkladových datech; Díky žádná kopie (s výjimkou `copy` funkce). Data může nebo nemusí obsahovat hodnoty null ('\0') v jakékoliv pozici. String_view nemá žádnou kontrolu nad životnosti objektu. Je odpovědností volajícího k zajištění, že podkladová data řetězce je platný.

Funkce, která přijímá parametr typu string_view provádět fungovat s jakýmkoli typem jako řetězec bez provedení funkce do šablony a omezení funkce na určitou podskupinu typy řetězců. Jediným požadavkem je, implicitní převod z typu řetězec na string_view existuje. Všechny standardní řetězec typy jsou implicitně převést na string_view, který obsahuje stejný typ elementu. Jinými slovy `std::string` lze převést na `string_view` , ale nikoli k `wstring_view`.

Následující příklad ukazuje nešablonové funkce `f` , která přebírá parametr typu `wstring_view`. Může být volána s argumenty typu `std::wstring`, `wchar_t*`, a `winrt::hstring`.

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

*CharType*<br/>
Zadejte znaky, které jsou uloženy v string_view. C++ Standardní knihovna obsahuje následující definice TypeDef pro specializace této šablony.
- [string_view](../standard-library/string-view-typedefs.md#string_view) pro prvky typu **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), for **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) for **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) pro **char32_t**.

*Osobnostní rysy*<br/>
Výchozí hodnota je [char_traits](char-traits-struct.md)<*CharType*>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_string_view](#basic_string_view)|Sestaví string_view, který je prázdný, jinak se odkazuje na všechny nebo část dat, některé další řetězec objektu nebo na pole znaků C-style.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|**const_iterator**|Iterátor pro náhodný přístup, který může číst **const** elementy.|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**iterator**|`using iterator = const_iterator;`|
|**nPos –**|`static constexpr size_type npos = size_type(-1);`|
|**pointer**|`using pointer = value_type*;`|
|**Referenční dokumentace**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Operátory členů

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Objekt string string_view nebo převoditelné přiřadí jiný string_view.|
|[– Operátor\[\]](#op_at)|Vrátí hodnotu prvku na zadaném indexu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[at](#at)|Vrátí const_reference na prvek v zadaném umístění.|
|[Zpět](#back)|Vrátí const_reference na poslední prvek.|
|[začít](#begin)|Vrátí konstantní iterátor adresující první prvek. (string_views jsou neměnné).|
|[cbegin](#cbegin)|Stejné jako [začít](#begin).|
|[cend](#cend)|Vrátí konstantní iterátor, který odkazuje na jedno místo za posledním prvkem.|
|[kopírování](#copy)|Zkopíruje maximálně zadaný počet znaků z indexovaného místa ve string_view zdroje do cílového pole znaků. (Není doporučeno. _Copy_s – místo toho použijte.)|
|[_Copy_s](#_copy_s)|Zabezpečení funkce CRT kopírování.|
|[compare](#compare)|Porovná string_view pomocí zadaného string_view k určení, jestli jsou shodné, nebo pokud je jeden méně lexikografický, než ten druhý.|
|[crbegin](#crbegin)|Stejné jako [rbegin –](#rbegin).|
|[crend](#crend)|Stejné jako [rend](#rend).|
|[data](#data)|Vrátí ukazatel raw-vlastnící sekvence znaků.|
|[prázdný](#empty)|Ověřuje, zda string_view obsahuje znaky.|
|[ukončení](#end)|Stejné jako [cend](#cend).|
|[Najít](#find)|Hledání ve směru dopředu pro první výskyt podřetězce, který odpovídá zadané posloupnosti znaků.|
|[find_first_not_of](#find_first_not_of)|Vyhledá první znak, který není libovolný prvek zadaného string_view nebo převést řetězec objektu.|
|[find_first_of](#find_first_of)|Vyhledá první znak, který se shoduje s libovolným prvkem zadaného string_view nebo převést řetězec objektu.|
|[find_last_not_of](#find_last_not_of)|Vyhledá poslední znak, který není libovolný prvek zadaného string_view nebo převést řetězec objektu.|
|[find_last_of](#find_last_of)|Vyhledá poslední znak, který je element string_view zadaným nebo převést řetězec objektu.|
|[Přední](#front)|Vrátí const_reference na první prvek.|
|[Délka](#length)|Vrátí aktuální počet prvků.|
|[max_size](#max_size)|Vrátí maximální počet znaků, které by mohla obsahovat string_view.|
|[rbegin](#rbegin)|Vrátí konstantní iterátor adresující první prvek v obráceném objektu string_view.|
|[remove_prefix](#remove_prefix)|Přesune ukazatel myši dopředu zadaný počet prvků.|
|[remove_suffix](#remove_suffix)|Zadaný počet prvků počínaje od zálohování snižuje velikost zobrazení.|
|[rend –](#rend)|Vrátí konstantní iterátor, který odkazuje na jedno místo za posledním prvkem v obráceném objektu string_view.|
|[rfind –](#rfind)|Vyhledá string_view v opačném pořadí pro první výskyt podřetězce, který odpovídá zadané posloupnosti znaků.|
|[Velikost](#size)|Vrátí aktuální počet prvků.|
|[substr](#substr)|Vrátí podřetězec počínaje zadaným indexem zadané délky.|
|[swap](#swap)|Výměna obsahu dvou string_views.|

## <a name="remarks"></a>Poznámky

Pokud ke generování sekvence delší, než se zobrazí výzva, funkce [max_size](#max_size) prvky, funkce oznámí chybu délky vyvoláním objektu typu [length_error –](../standard-library/length-error-class.md).

## <a name="requirements"></a>Požadavky

[std: c ++ 17](../build/reference/std-specify-language-standard-version.md) nebo novější

**Záhlaví:** \<string_view >

**Namespace:** std

## <a name="at"></a>  basic_string_view::AT

Vrátí znak na pozici zadaného indexu na základě 0 const_reference.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parametry

*Posun*<br/>
Index prvku, který chcete odkazovat.

### <a name="return-value"></a>Návratová hodnota

Const_reference znak na pozici určené index parametru.

### <a name="remarks"></a>Poznámky

První prvek má index 0 a tyto prvky jsou postupně indexovat pomocí kladná celá čísla, tak, aby string_view délky *n* má *n*tý prvek indexovat pomocí čísel *n -* 1. **na** vrací chybovou výjimku neplatná indexů, na rozdíl od [operátor\[\]](#op_at). 

Obecně doporučujeme, aby **na** pro pořadí, jako `std::vector` a string_view byste nikdy neměli používat. Neplatný index předaný do pořadí je logická chyba, kterou by měla zjistit a oprava během vývoje. Není-li program naprosto jisti, že jeho indexy jsou platné, ho by neměl otestujete, zavolejte at() a výjimky se chránit před nepozorný programování.

Zobrazit [basic_string_view::operator\[ \] ](#op_at) Další informace.

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

## <a name="back"></a>  basic_string_view::back

Vrátí const_reference na poslední prvek.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

Const_reference na poslední prvek string_view.

### <a name="remarks"></a>Poznámky

Vyvolá výjimku, pokud string_view je prázdný.

Mějte na paměti, která po string_view změně, například voláním `remove_suffix`, pak element vrácená touto funkcí už nejsou po posledním prvku v podkladových datech.

### <a name="example"></a>Příklad

String_view, který je vytvořený pomocí literálu C nezahrnuje ukončující znak null a proto v následujícím příkladu `back` vrátí 'p' ne '\0'.

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p 
```

Vložené znaky Null jsou považovány za jakýkoli jiný znak:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_view"></a>  basic_string_view::basic_string_view

Vytvoří string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ukazatel na hodnoty znaků.

*Délka*<br/>
Počet znaků, které mají zahrnout do zobrazení.

## <a name="remarks"></a>Poznámky

Konstruktory s parametrem grafu * předpokládají, že je vstup zakončený hodnotou null, ale ukončujícího znaku null není součástí string_view.

Můžete také sestavit string_view s literál. Zobrazit [operátor "" sv](string-view-operators.md#op_sv).

## <a name="begin"></a>  basic_string_view::begin

Stejné jako [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota
Vrátí const_iterator adresující první prvek.

## <a name="cbegin"></a>  basic_string_view::cbegin

Vrátí const_iterator, který adresuje první prvek v rozsahu.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

A **const** iterátor s náhodným přístupem, který ukazuje na první prvek rozsahu nebo na umístění hned za koncem prázdného rozsahu (pro prázdný rozsah `cbegin() == cend()`).

## <a name="cend"></a>  basic_string_view::cend

Vrátí const_iterator, který řeší umístění hned za posledním prvkem v rozsahu.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

A **const** iterátor s náhodným přístupem, který ukazuje přesně za konec rozsahu.

### <a name="remarks"></a>Poznámky

Hodnota vrácená `cend` by neměla být dereferencována.

## <a name="compare"></a> basic_string_view::Compare

Provádí porovnání velká a malá písmena pomocí zadaného string_view (nebo typu lze převést řetězec) určete, jestli jsou oba objekty stejné, nebo pokud je jeden méně lexikografický, než ten druhý. [ \<String_view > operátory](string-view-operators.md) tuto funkci člena lze použít k provádění porovnání.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Parametry

*strv*<br/>
String_view, který je k porovnání s této string_view.

*pos*<br/>
Index tohoto string_view, při kterém začíná porovnání.

*počet*<br/>
Maximální počet znaků z této string_view k porovnání.

*Num2*<br/>
Maximální počet znaků od *strv* k porovnání.

*Posun*<br/>
Index *strv* na kterém začne porovnání.

*ptr*<br/>
Řetězec jazyka C k porovnání s této string_view.

### <a name="return-value"></a>Návratová hodnota

Záporná hodnota, pokud je tato string_view menší než *strv* nebo *ptr*; nula, pokud dvě znakové sekvence rovná; nebo kladnou hodnotu, pokud je větší než tento string_view *strv*nebo *ptr*.

### <a name="remarks"></a>Poznámky

`compare` Členské funkce provést porovnání velká a malá písmena všech nebo součástí každé sekvence znaků. 

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

## <a name="copy"></a>  basic_string_view::copy

Zkopíruje maximálně zadaný počet znaků z indexovaného místa ve string_view zdroje do cílového pole znaků. Doporučujeme použít funkci zabezpečeného [basic_string_view::_Copy_s](#_copy_s) místo.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Znak cílového pole, do kterého mají být zkopírovány prvky.

*Počet*<br/>
Počet znaků, které se mají zkopírovat, maximálně z string_view zdroje.

*Posun*<br/>
Počáteční pozice v string_view zdroj, ze kterého mají být provedeny kopie.

### <a name="return-value"></a>Návratová hodnota

Počet znaků, které skutečně zkopírovány.

### <a name="remarks"></a>Poznámky

Konec kopírování není připojen znak null.

## <a name="_copy_s"></a>  basic_string_view::_Copy_s

Zabezpečení funkce CRT kopírování se použije namísto [kopírování](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Znak cílového pole, do kterého mají být zkopírovány prvky.

*dest_size*<br/>
Velikost *dest*.

_ *Počet* počet znaků, které se mají zkopírovat, maximálně z zdrojový řetězec.

*_Off*<br/>
Počáteční pozice ve zdrojovém řetězci, ze kterého mají být provedeny kopie.

### <a name="return-value"></a>Návratová hodnota

Počet znaků, které skutečně zkopírovány.

### <a name="remarks"></a>Poznámky

Konec kopírování není připojen znak null.

 Další informace najdete v tématu [c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md).

## <a name="crbegin"></a>  basic_string_view::crbegin

Vrátí const_reverse_iterator, který adresuje první prvek v obráceném objektu string_view.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Const_reverse_iterator, který adresuje první prvek v obráceném objektu string_view. 

## <a name="crend"></a>  basic_string_view::crend

Stejné jako [rend](#rend). 

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí const_reverse_iterator, který reaguje na jeden za koncem obrácený string_view.

## <a name="data"></a>  basic_string_view::data

Vrátí ukazatel raw-vlastnící const sekvence znaků objektu, který byl použit k sestavení kompletních string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na konstantní na první prvek je sekvence znaků.

### <a name="remarks"></a>Poznámky

Ukazatel nejde upravit znaky.

Posloupnost znaků string_view není nutně ukončena hodnotou null. Návratový typ pro `data` není platný řetězec C, protože žádný znak null získá připojen. Znak null '\0' nemá žádný speciální význam v objektu typu string_view a může být součástí objektu string_view stejně jako jakýkoli jiný znak.

## <a name="empty"></a>  basic_string_view::Empty

Ověřuje, zda string_view obsahuje znaky, nebo ne.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud string_view objekt neobsahuje žádné znaky; **false** , pokud je alespoň jeden znak.

### <a name="remarks"></a>Poznámky

Členská funkce je ekvivalentní [velikost](#size)() == 0.

## <a name="end"></a>  basic_string_view::end

Vrátí const_iterator náhodného přístupu, který odkazuje na jedno místo za posledním prvkem.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí const_iterator náhodného přístupu, který odkazuje na jedno místo za posledním prvkem.

### <a name="remarks"></a>Poznámky

`end` slouží k otestování, jestli const_iterator bylo dosaženo konce jeho string_view. Hodnota vrácená `end` by neměla být dereferencována.

## <a name="find"></a>  basic_string_view::Find

Vyhledá string_view ve směru dopředu pro první výskyt znaku nebo podřetězce, který odpovídá zadané posloupnosti znaků.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
String_view, pro kterou má členská funkce je k vyhledání.

*chVal*<br/>
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*<br/>
Index, na které má vyhledávání začít.

*ptr*<br/>
Řetězec jazyka C, pro kterou má členská funkce je k vyhledání.

*Počet*<br/>
Počet znaků v *ptr*, počítaných vpřed od prvního znaku.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

## <a name="find_first_not_of"></a>  basic_string_view::find_first_not_of

Vyhledá první znak, který nepředstavuje element string_view zadaným nebo převést řetězec objektu.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
String_view, pro kterou má členská funkce je k vyhledání.

*chVal*<br/>
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*<br/>
Index, na které má vyhledávání začít.

*ptr*<br/>
Řetězec jazyka C, pro kterou má členská funkce je k vyhledání.

*Počet*<br/>
Počet znaků, počítaných vpřed od prvního znaku v řetězci jazyka C, pro kterou má členská funkce je k vyhledání.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

## <a name="find_first_of"></a>  basic_string_view::find_first_of

Vyhledá první znak, který se shoduje s libovolným prvkem zadaného string_view.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*chVal*<br/>
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*<br/>
Index, na které má vyhledávání začít.

*ptr*<br/>
Řetězec jazyka C, pro kterou má členská funkce je k vyhledání.

*Počet*<br/>
Počet znaků, počítaných vpřed od prvního znaku v řetězci jazyka C, pro kterou má členská funkce je k vyhledání.

*str*<br/>
String_view, pro kterou má členská funkce je k vyhledání.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

## <a name="find_last_not_of"></a>  basic_string_view::find_last_not_of

Vyhledá poslední znak, který není libovolný prvek zadaného string_view.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
String_view, pro kterou má členská funkce je k vyhledání.

*chVal*<br/>
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*<br/>
Index, na které má dokončit vyhledávání.

*ptr*<br/>
Řetězec jazyka C, pro kterou má členská funkce je k vyhledání.

*Počet*<br/>
Počet znaků, počítaných vpřed od prvního znaku v *ptr*.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `string_view::npos`.

## <a name="find_last_of"></a>  basic_string_view::find_last_of

Vyhledá poslední znak, který se shoduje s libovolným prvkem zadaného string_view.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*str*<br/>
String_view, pro kterou má členská funkce je k vyhledání.

*chVal*<br/>
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*<br/>
Index, na které má dokončit vyhledávání.

*ptr*<br/>
Řetězec jazyka C, pro kterou má členská funkce je k vyhledání.

*Počet*<br/>
Počet znaků, počítaných vpřed od prvního znaku v řetězci jazyka C, pro kterou má členská funkce je k vyhledání.

### <a name="return-value"></a>Návratová hodnota

Index posledního znaku podřetězec hledá v případě úspěchu; v opačném případě `npos`.

## <a name="front"></a>  basic_string_view::front

Vrátí const_reference na první prvek.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Const_reference na první prvek.

### <a name="remarks"></a>Poznámky

Vyvolá výjimku, pokud string_view je prázdný.

## <a name="length"></a> basic_string_view::length

Vrátí aktuální počet prvků.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce je stejná jako [velikost](#size).

## <a name="max_size"></a>  basic_string_view::max_size

Vrátí maximální počet znaků, které mohou obsahovat string_view.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet znaků a string_view může obsahovat.

### <a name="remarks"></a>Poznámky

Výjimka typu [length_error –](../standard-library/length-error-class.md) je vyvolána, když operace vytvoří string_view s délkou větší než `max_size()`.

## <a name="op_eq"></a>  basic_string_view::Operator =

Objekt string string_view nebo převoditelné přiřadí jiný string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```
### <a name="example"></a>Příklad

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```
## <a name="op_at"></a>  [] basic_string_view::Operator

Poskytuje const_reference na znak se zadaným indexem.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parametry

*Posun*<br/>
Index prvku, který chcete odkazovat.

### <a name="return-value"></a>Návratová hodnota

Const_reference znak na pozici určené index parametru.

### <a name="remarks"></a>Poznámky

První prvek má index 0, a tyto prvky jsou postupně indexovat pomocí kladná celá čísla, tak, aby string_view délky *n* má *n*tý prvek indexovat pomocí čísel *n* - 1.

`operator[]` je rychlejší než členskou funkci [na](#at) pro poskytnutí přístupu pro čtení k prvkům string_view.

`operator[]` nekontroluje, zda index předaný jako argument je platný. Předán neplatný index `operator[]` způsobí nedefinované chování.

Reference vrácená může zruší, pokud je změněného nebo odstraněného vlastnící objekt podkladová data řetězce.

Při kompilaci s [ \_ITERÁTORU\_ladění\_úroveň](../standard-library/iterator-debug-level.md) nastavena na 1 nebo 2, dojde k chybě při pokusu o přístup k prvku mimo hranice string_view. Další informace najdete v tématu [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="rbegin"></a>  basic_string_view::rbegin

Vrátí konstantní iterátor na první prvek v obráceném objektu string_view.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor s náhodným přístupem na první prvek v obráceném objektu string_view, co by po posledním prvku v odpovídající neobráceném string_view adresování.

### <a name="remarks"></a>Poznámky

`rbegin` se používá s obrácený string_view stejně jako [začít](#begin) se používá s string_view. `rbegin` je možné zpětně inicializovat iterace.

## <a name="remove_prefix"></a> basic_string_view::remove_prefix

Přesune ukazatel myši dopředu zadaný počet prvků.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Poznámky

Ponechá beze změny podkladová data. Přesune ukazatel string_view vpřed n prvků a nastaví privátní `size` datový člen velikost - n.

## <a name="remove_suffix"></a> basic_string_view::remove_suffix

Zadaný počet prvků počínaje od zálohování snižuje velikost zobrazení.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Poznámky

Opustí podkladová data a ukazatel na ni beze změny. Nastaví privátní `size` datový člen velikost - n.

## <a name="rend"></a>  basic_string_view::rend

Vrátí konstantní iterátor, který odkazuje na jedno místo za posledním prvkem v obráceném objektu string_view.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Const reverse iterátor s náhodným přístupem, který odkazuje na jedno místo za posledním prvkem v obráceném objektu string_view.

### <a name="remarks"></a>Poznámky

`rend` se používá s obrácený string_view stejně jako [end](#end) se používá s string_view. `rend` slouží k ověření, zda zpětný iterátor dosáhl konce jeho string_view. Hodnota vrácená `rend` by neměla být dereferencována.

## <a name="rfind"></a>  basic_string_view::rfind

Vyhledá string_view pozpátku podřetězce, který odpovídá zadané posloupnosti znaků.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*chVal*<br/>
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*<br/>
Index, na které má vyhledávání začít.

*ptr*<br/>
Řetězec jazyka C, pro kterou má členská funkce je k vyhledání.

*Počet*<br/>
Počet znaků, počítaných vpřed od prvního znaku v řetězci jazyka C, pro kterou má členská funkce je k vyhledání.

*str*<br/>
String_view, pro kterou má členská funkce je k vyhledání.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku podřetězce v případě úspěchu; v opačném případě `npos`.

## <a name="size"></a>  basic_string_view::size

Vrátí počet prvků string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Délka string_view.

### <a name="remarks"></a>Poznámky

String_view můžete třeba upravit jeho délka tak `remove_prefix` a `remove_suffix`. Protože to neprovede žádné změny podkladových dat řetězce, velikost string_view není nutně velikost podkladová data.

## <a name="substr"></a>  basic_string_view::substr

Vrátí string_view, který představuje (maximálně) zadaný počet znaků od určené pozice.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parametry

*Posun*<br/>
Index vyhledávání element na pozici, ze kterého se kopie vytvoří s výchozí hodnotou 0.

*Počet*<br/>
Počet znaků, které mají zahrnout do dílčí řetězec, pokud jsou přítomna.

### <a name="return-value"></a>Návratová hodnota

String_view objekt, který představuje zadaný dílčí sekvence prvků.

## <a name="swap"></a>  basic_string_view::swap

Vymění dvě string_views, jinými slovy ukazatele na základní data řetězce a hodnoty velikosti.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parametry

*sv*<br/>
String_view zdroje, jejichž hodnoty ukazatele a velikost se mají vyměnit s ním string_view cíl.

## <a name="see-also"></a>Viz také:

[\<string_view>](../standard-library/string-view.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
