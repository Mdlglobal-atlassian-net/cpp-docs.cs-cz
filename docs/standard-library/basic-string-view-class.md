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
ms.openlocfilehash: ac65dca931f821c717e9c081c8d3479fd0b3bb0e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364896"
---
# <a name="basic_string_view-class"></a>basic_string_view – třída

Šablona `basic_string_view<charT>` třídy byla přidána v jazyce C++ 17, aby sloužila jako bezpečný a efektivní způsob, jak funkce přijímat různé nesouvisející typy řetězců, aniž by funkce musela být u těchto typů templatizována. Třída obsahuje nevlastnící ukazatel souvislé posloupnosti znakových dat a délku, která určuje počet znaků v sekvenci. Žádný předpoklad je s ohledem na to, zda sekvence je null ukončena.

Standardní knihovna definuje několik specializací na základě typu prvků:

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

V tomto dokumentu termín "string_view" odkazuje obecně na některý z těchto typedefs.

String_view popisuje minimální společné rozhraní potřebné ke čtení dat řetězce. Poskytuje const přístup k podkladovým datům; nevytváří žádné kopie (s výjimkou `copy` funkce). Data mohou nebo nemusí obsahovat hodnoty null (\0) na libovolné pozici. String_view nemá žádnou kontrolu nad životností objektu. Je odpovědností volajícího zajistit, že podkladová data řetězce je platný.

Funkce, která přijímá parametr typu string_view lze provést pro práci s libovolným typem typu podobnému řetězci, bez provedení funkce do šablony nebo omezení funkce na určitou podmnožinu typů řetězců. Jediným požadavkem je, že implicitní převod existuje z typu řetězce na string_view. Všechny standardní typy řetězců jsou implicitně převoditelné na string_view, která obsahuje stejný typ prvku. Jinými slovy, `std::string` a je `string_view` konvertibilní na , ale ne na `wstring_view`.

Následující příklad ukazuje funkci `f` bez šablony, která `wstring_view`přebírá parametr typu . Lze jej volat s argumenty `wchar_t*`typu `winrt::hstring` `std::wstring`, a .

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

*Typ znaku*\
Typ znaků, které jsou uloženy v string_view. Standardní knihovna jazyka C++ poskytuje následující typedefs pro specializace této šablony.

- [string_view](../standard-library/string-view-typedefs.md#string_view) pro prvky typu **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), za **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) pro **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) pro **char32_t**.

*Vlastnosti*\
Výchozí hodnota [je char_traits](char-traits-struct.md)<*> CharType.*

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_string_view](#basic_string_view)|Vytvoří string_view, která je prázdná nebo odkazuje na všechna data nebo část dat jiného objektu řetězce nebo na pole znaků ve stylu C.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|**const_iterator**|Random-access iterátor, který může číst **const** prvky.|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**Iterace**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**ukazatel**|`using pointer = value_type*;`|
|**Odkaz**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Členské operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí objekt string_view nebo konvertibilní řetězec jinému string_view.|
|[Operátor\[\]](#op_at)|Vrátí prvek v zadaném indexu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Na](#at)|Vrátí const_reference prvku v zadaném umístění.|
|[Zpět](#back)|Vrátí const_reference na poslední prvek.|
|[Začít](#begin)|Vrátí const iterator adresování první prvek. (string_views jsou neměnné.)|
|[cbegin](#cbegin)|Stejné jako [begin](#begin).|
|[cend](#cend)|Vrátí const iterator, který odkazuje na jeden za poslední prvek.|
|[Kopírovat](#copy)|Zkopíruje maximálně zadaný počet znaků z indexované pozice ve zdrojovém string_view do cílového pole znaků. (Nedoporučuje se. Místo toho použijte _Copy_s.)|
|[_Copy_s](#_copy_s)|Funkce bezpečného kopírování CRT.|
|[Porovnat](#compare)|Porovná string_view se zadanou string_view k určení, zda jsou stejné nebo zda je jedna lexikograficky menší než druhá.|
|[crbegin](#crbegin)|Stejné jako [rbegin](#rbegin).|
|[crend](#crend)|Stejně jako [rend](#rend).|
|[Dat](#data)|Vrátí nezpracovaná nevlastnící ukazatel na posloupnost znaků.|
|[empty](#empty)|Testuje, zda string_view obsahuje znaky.|
|[Konec](#end)|Stejné jako [cend](#cend).|
|[find](#find)|Hledá ve směru dopředu pro první výskyt podřetězce, který odpovídá zadané posloupnosti znaků.|
|[find_first_not_of](#find_first_not_of)|Vyhledá první znak, který není žádný prvek zadaného string_view nebo konvertibilní řetězec objektu.|
|[find_first_of](#find_first_of)|Vyhledá první znak, který odpovídá libovolnému prvku zadaného string_view nebo konvertibilního objektu řetězce.|
|[find_last_not_of](#find_last_not_of)|Vyhledá poslední znak, který není žádný prvek zadaného string_view nebo konvertibilní řetězec objektu.|
|[find_last_of](#find_last_of)|Vyhledá poslední znak, který je prvkem zadaného string_view nebo konvertibilního objektu řetězce.|
|[Přední](#front)|Vrátí const_reference první prvek.|
|[Délka](#length)|Vrátí aktuální počet prvků.|
|[max_size](#max_size)|Vrátí maximální počet znaků, které by string_view mohl obsahovat.|
|[rbegin](#rbegin)|Vrátí const iterator, který řeší první prvek v obráceném string_view.|
|[remove_prefix](#remove_prefix)|Posune ukazatel dopředu o zadaný počet prvků.|
|[remove_suffix](#remove_suffix)|Zmenší velikost zobrazení o zadaný počet prvků počínaje zadní částí.|
|[rend](#rend)|Vrátí const iterator, který odkazuje na jeden za poslední prvek v obrácené masívní string_view.|
|[rnajít](#rfind)|Pro první výskyt podřetězce, který odpovídá zadané posloupnosti znaků, vyhledá string_view v opačném směru.|
|[Velikost](#size)|Vrátí aktuální počet prvků.|
|[podřízený](#substr)|Vrátí podřetězec zadané délky začínající na zadaném indexu.|
|[Swap](#swap)|Vyměňte obsah dvou string_views.|

## <a name="remarks"></a>Poznámky

Pokud je funkce vyzvána ke generování sekvence delší než [max_size](#max_size) prvky, funkce hlásí chybu délky vyvoláním objektu typu [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Požadavky

[std:c++17](../build/reference/std-specify-language-standard-version.md) nebo novější

**Záhlaví:** \<string_view>

**Obor názvů:** std

## <a name="basic_string_viewat"></a><a name="at"></a>basic_string_view::at

Vrátí const_reference znaku v zadaném indexu založeném na 0.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parametry

*Posun*\
Index prvku, na který se odkazuje.

### <a name="return-value"></a>Návratová hodnota

A const_reference znakna pozici určené indexparametr.

### <a name="remarks"></a>Poznámky

První prvek má index nula a následující prvky jsou postupně indexovány kladnými celočíselami, takže string_view délky *n* má *n*prvek indexovaný číslem *n -* 1. **na** vyvolá výjimku pro neplatné indexy, na rozdíl od [operátoru\[](#op_at).

Obecně doporučujeme, **aby v** pro `std::vector` sekvence, jako jsou a string_view by nikdy použít. Neplatný index předaný posloupnosti je logická chyba, která by měla být zjištěna a opravena během vývoje. Pokud program není zcela jistý, že jeho indexy jsou platné, měl by je testovat, ne volat at() a spoléhat se na výjimky na obranu proti nedbalé programování.

Další informace naleznete [v basic_string_view::operátor.\[ ](#op_at)

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

## <a name="basic_string_viewback"></a><a name="back"></a>basic_string_view::zpět

Vrátí const_reference na poslední prvek.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Návratová hodnota

A const_reference k poslednímu prvku v string_view.

### <a name="remarks"></a>Poznámky

Vyvolá výjimku, pokud je string_view prázdný.

Mějte na paměti, že po změně `remove_suffix`string_view, například voláním , pak prvek vrácený touto funkcí již není posledním prvkem v podkladových datech.

### <a name="example"></a>Příklad

String_view, který je vytvořen s literálem řetězce C, neobsahuje ukončující hodnotu null, a proto v následujícím příkladu `back` vrátí příkazy p a nikoli \0.

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

Vložené hodnoty null jsou považovány za jakýkoli jiný znak:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a>basic_string_view::basic_string_view

Vytvoří string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parametry

*Str*\
Ukazatel na hodnoty znaků.

*Len*\
Počet znaků, které mají být zahrnuty do zobrazení.

## <a name="remarks"></a>Poznámky

Konstruktory s parametrem charT* předpokládají, že vstup je ukončen nulou, ale ukončující null není součástí string_view.

Můžete také vytvořit string_view s literálem. Viz [operátor""sv](string-view-operators.md#op_sv).

## <a name="basic_string_viewbegin"></a><a name="begin"></a>basic_string_view::začátek

Stejné jako [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí const_iterator adresování první prvek.

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a>basic_string_view::cbegin

Vrátí const_iterator, která řeší první prvek v oblasti.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Const** random-access iterátor, který odkazuje na první prvek rozsahu nebo umístění těsně za koncem prázdné oblasti `cbegin() == cend()`(pro prázdný rozsah).

## <a name="basic_string_viewcend"></a><a name="cend"></a>basic_string_view::cenzura

Vrátí const_iterator, která řeší umístění těsně za poslední prvek v oblasti.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Const** random-access iterator, který ukazuje těsně za koncem rozsahu.

### <a name="remarks"></a>Poznámky

Hodnota vrácená `cend` by neměla být odkazována.

## <a name="basic_string_viewcompare"></a><a name="compare"></a>basic_string_view::porovnat

Provede porovnání rozlišování malých a velkých písmen se zadaným string_view (nebo konvertibilní typ řetězce) k určení, zda jsou dva objekty stejné nebo zda jeden je lexicographically menší než ostatní. Operátory string_view [ \<>](string-view-operators.md) používají tuto členskou funkci k provádění porovnání.

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
String_view, který je třeba srovnávat s tímto string_view.

*Pos*\
Index tohoto string_view, ve kterém začíná porovnání.

*Num*\
Maximální počet znaků z tohoto string_view k porovnání.

*číslo2*\
Maximální počet znaků z *strv,* které mají být porovnány.

*Posun*\
Index *strv,* ve kterém začíná porovnání.

*Ptr*\
Řetězec C, který má být porovnán s tímto string_view.

### <a name="return-value"></a>Návratová hodnota

Záporná hodnota, pokud je tato string_view menší než *strv* nebo *ptr*; nula, pokud jsou dvě sekvence znaků stejné; nebo kladnou hodnotu, pokud je tato string_view větší než *strv* nebo *ptr*.

### <a name="remarks"></a>Poznámky

Členské `compare` funkce provádět porovnání rozlišování velkých a malých písmen všech nebo části každé sekvence znaků.

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

## <a name="basic_string_viewcopy"></a><a name="copy"></a>basic_string_view::kopírování

Zkopíruje maximálně zadaný počet znaků z indexované pozice ve zdrojovém string_view do cílového pole znaků. Doporučujeme místo toho použít zabezpečenou funkci [basic_string_view::_Copy_s.](#_copy_s)

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*Ptr*\
Cílové pole znaků, do kterého mají být prvky zkopírovány.

*Počet*\
Počet znaků, které mají být zkopírovány maximálně ze zdrojového string_view.

*Posun*\
Počáteční pozice ve zdrojové matné string_view, ze kterého mají být kopie vytvářeny.

### <a name="return-value"></a>Návratová hodnota

Počet skutečně zkopírovaných znaků.

### <a name="remarks"></a>Poznámky

Znak null není připojen na konec kopie.

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a>basic_string_view::_Copy_s

Secure CRT copy funkce, která má být použita namísto [kopírování](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parametry

*Dest*\
Cílové pole znaků, do kterého mají být prvky zkopírovány.

*dest_size*\
Velikost *dest*.

_ *Spočítat* počet znaků, které mají být zkopírovány nejvýše ze zdrojového řetězce.

*_Off*\
Počáteční pozice ve zdrojovém řetězci, ze kterého mají být provedeny kopie.

### <a name="return-value"></a>Návratová hodnota

Počet skutečně zkopírovaných znaků.

### <a name="remarks"></a>Poznámky

Znak null není připojen na konec kopie.

Další informace naleznete v [tématu c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md).

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a>basic_string_view::crbegin

Vrátí const_reverse_iterator, která řeší první prvek v obráceném string_view.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Const_reverse_iterator, který řeší první prvek v obrácené mašity string_view.

## <a name="basic_string_viewcrend"></a><a name="crend"></a>basic_string_view::crend

Stejně jako [rend](#rend).

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí const_reverse_iterator, která řeší jeden za koncem stornované string_view.

## <a name="basic_string_viewdata"></a><a name="data"></a>basic_string_view::data

Vrátí nezpracovaná nevlastnící ukazatel na posloupnost znaků const objektu, který byl použit k vytvoření string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na const na první prvek sekvence znaků.

### <a name="remarks"></a>Poznámky

Ukazatel nemůže změnit znaky.

Posloupnost string_view znaků nemusí být nutně ukončena nulou. Návratový typ `data` pro není platný řetězec C, protože není připojen žádný znak null. Znak null \0 nemá žádný zvláštní význam v objektu typu string_view a může být součástí string_view objektu stejně jako jakýkoli jiný znak.

## <a name="basic_string_viewempty"></a><a name="empty"></a>basic_string_view::prázdný

Testuje, zda string_view obsahuje znaky nebo ne.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud string_view objekt neobsahuje žádné znaky; **false,** pokud má alespoň jeden znak.

### <a name="remarks"></a>Poznámky

Členská funkce je ekvivalentní [velikosti](#size)() == 0.

## <a name="basic_string_viewend"></a><a name="end"></a>basic_string_view::konec

Vrátí const_iterator náhodného přístupu, který odkazuje na jeden za poslední prvek.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí const_iterator náhodného přístupu, který odkazuje na jeden za poslední prvek.

### <a name="remarks"></a>Poznámky

`end`se používá k testování, zda const_iterator dosáhl konce svého string_view. Hodnota vrácená `end` by neměla být odkazována.

## <a name="basic_string_viewfind"></a><a name="find"></a>basic_string_view::najít

Prohledá string_view ve směru dopředu pro první výskyt znaku nebo podřetězce, který odpovídá zadané posloupnosti znaků.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*Str*\
String_view, pro které je členská funkce hledat.

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index, ve kterém má hledání začít.

*Ptr*\
Řetězec C, pro který je členská funkce hledat.

*Počet*\
Počet znaků v *ptr*, počítání vpřed od prvního znaku.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string_view::find_first_not_of

Vyhledá první znak, který není prvkem zadaného string_view nebo konvertibilního objektu řetězce.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*Str*\
String_view, pro které je členská funkce hledat.

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index, ve kterém má hledání začít.

*Ptr*\
Řetězec C, pro který je členská funkce hledat.

*Počet*\
Počet znaků, počítání dopředu od prvního znaku, v řetězci C, pro které je členská funkce hledat.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a>basic_string_view::find_first_of

Vyhledá první znak, který odpovídá libovolnému prvku zadaného string_view.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parametry

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index, ve kterém má hledání začít.

*Ptr*\
Řetězec C, pro který je členská funkce hledat.

*Počet*\
Počet znaků, počítání dopředu od prvního znaku, v řetězci C, pro které je členská funkce hledat.

*Str*\
String_view, pro které je členská funkce hledat.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `npos`.

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string_view::find_last_not_of

Vyhledá poslední znak, který není žádný prvek zadané ho string_view.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*Str*\
String_view, pro které je členská funkce hledat.

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index, ve kterém má být hledání dokončeno.

*Ptr*\
Řetězec C, pro který je členská funkce hledat.

*Počet*\
Počet znaků, počítání dopředu od prvního znaku, v *ptr*.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku nalezeného podřetězce, v opačném případě `string_view::npos`.

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a>basic_string_view::find_last_of

Vyhledá poslední znak, který odpovídá libovolnému prvku zadaného string_view.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*Str*\
String_view, pro které je členská funkce hledat.

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index, ve kterém má být hledání dokončeno.

*Ptr*\
Řetězec C, pro který je členská funkce hledat.

*Počet*\
Počet znaků, počítání dopředu od prvního znaku, v řetězci C, pro které je členská funkce hledat.

### <a name="return-value"></a>Návratová hodnota

Index posledního znaku podřetězce hledaného při úspěšném zobrazení; v `npos`opačném případě .

## <a name="basic_string_viewfront"></a><a name="front"></a>basic_string_view::přední

Vrátí const_reference první prvek.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Návratová hodnota

Const_reference k prvnímu prvku.

### <a name="remarks"></a>Poznámky

Vyvolá výjimku, pokud je string_view prázdný.

## <a name="basic_string_viewlength"></a><a name="length"></a>basic_string_view::délka

Vrátí aktuální počet prvků.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Poznámky

Členská funkce je stejná jako [velikost](#size).

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a>basic_string_view::max_size

Vrátí maximální počet znaků, které může string_view obsahovat.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet znaků, které může string_view obsahovat.

### <a name="remarks"></a>Poznámky

Výjimka typu [length_error](../standard-library/length-error-class.md) je vyvolána, když operace vytvoří string_view `max_size()`s délkou větší než .

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a>basic_string_view::operátor=

Přiřadí objekt string_view nebo konvertibilní řetězec jinému string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>Příklad

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a>basic_string_view::operátor[]

Poskytuje const_reference znaku se zadaným indexem.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parametry

*Posun*\
Index prvku, na který se odkazuje.

### <a name="return-value"></a>Návratová hodnota

A const_reference znakna pozici určené indexparametr.

### <a name="remarks"></a>Poznámky

První prvek má index nula a následující prvky jsou postupně indexovány kladnými celočíselami, takže string_view délky *n* má *n*prvek indexovaný číslem *n* - 1.

`operator[]`je rychlejší než členské funkce [na](#at) pro poskytování přístupu pro čtení k prvkům string_view.

`operator[]`nekontroluje, zda je index předaný jako argument platný. Neplatný index `operator[]` předávaný výsledkům v nedefinovaném chování.

Vrácený odkaz může být zrušena, pokud podkladová data řetězce je změněnnebo odstraněn vlastnící objekt.

Při kompilaci s [ \_\_ITERATOR\_LADĚNÍ ÚROVEŇ](../standard-library/iterator-debug-level.md) nastavena na 1 nebo 2, dojde k chybě za běhu, pokud se pokusíte o přístup k prvku mimo hranice string_view. Další informace naleznete [v tématu Checked Iterators](../standard-library/checked-iterators.md).

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a>basic_string_view::rbegin

Vrátí const iterator na první prvek v obrácené min. string_view.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí iterátor náhodného přístupu k prvnímu prvku v obráceném string_view, adresování, co by byl poslední prvek v odpovídající unreversed string_view.

### <a name="remarks"></a>Poznámky

`rbegin`se používá s obráceným string_view stejně jako [začátek](#begin) se používá s string_view. `rbegin`lze inicializovat iterace zpět.

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a>basic_string_view::remove_prefix

Posune ukazatel dopředu o zadaný počet prvků.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Poznámky

Ponechá podkladová data beze změny. Posune ukazatel string_view vpřed o n `size` prvků a nastaví soukromý datový člen na velikost - n.

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a>basic_string_view::remove_suffix

Zmenší velikost zobrazení o zadaný počet prvků počínaje zadní částí.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Poznámky

Ponechá podkladová data a ukazatel na ně beze změny. Nastaví `size` soukromý datový člen na velikost - n.

## <a name="basic_string_viewrend"></a><a name="rend"></a>basic_string_view::rend

Vrátí const iterator, který odkazuje na jeden za poslední prvek v obrácené masívní string_view.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Const reverzní random-access iterátor, který odkazuje na jeden za poslední prvek v obrácené string_view.

### <a name="remarks"></a>Poznámky

`rend`se používá s obráceným string_view [stejně](#end) jako konec se používá s string_view. `rend`lze použít k testování, zda reverzní iterátor dosáhl konce svého string_view. Hodnota vrácená `rend` by neměla být odkazována.

## <a name="basic_string_viewrfind"></a><a name="rfind"></a>basic_string_view::rfind

Hledá string_view v opačném pořadí pro podřetězec, který odpovídá zadané posloupnosti znaků.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parametry

*chVal*\
Hodnota znaku, kterou má členská funkce vyhledat.

*Posun*\
Index, ve kterém má hledání začít.

*Ptr*\
Řetězec C, pro který je členská funkce hledat.

*Počet*\
Počet znaků, počítání dopředu od prvního znaku, v řetězci C, pro které je členská funkce hledat.

*Str*\
String_view, pro které je členská funkce hledat.

### <a name="return-value"></a>Návratová hodnota

Index prvního znaku podřetězce při úspěšném; v `npos`opačném případě .

## <a name="basic_string_viewsize"></a><a name="size"></a>basic_string_view::velikost

Vrátí počet prvků v string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Délka string_view.

### <a name="remarks"></a>Poznámky

A string_view může změnit svou `remove_prefix` délku, například pomocí a `remove_suffix`. Vzhledem k tomu, že to nemění podkladová data řetězce, velikost string_view nemusí být nutně velikost podkladových dat.

## <a name="basic_string_viewsubstr"></a><a name="substr"></a>basic_string_view::substr

Vrátí string_view, která představuje (maximálně) zadaný počet znaků ze zadané pozice.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parametry

*Posun*\
Index vyhledávající prvek na pozici, ze které je kopie provedena, s výchozí hodnotou 0.

*Počet*\
Počet znaků, které mají být zahrnuty do podřetězce, pokud jsou k dispozici.

### <a name="return-value"></a>Návratová hodnota

A string_view objekt, který představuje zadanou dílčí sekvenci prvků.

## <a name="basic_string_viewswap"></a><a name="swap"></a>basic_string_view::swap

Vymění dvě string_views, jinými slovy ukazatele na podkladová řetězcová data a hodnoty velikosti.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parametry

*sv*\
Zdroj string_view, jehož ukazatele a hodnoty velikosti mají být vyměněny s cílovým string_view.

## <a name="see-also"></a>Viz také

[\<string_view>](../standard-library/string-view.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
