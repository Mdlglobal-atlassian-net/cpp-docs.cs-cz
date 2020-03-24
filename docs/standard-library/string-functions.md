---
title: '&lt;řetězcové&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- string/std::getline
- string/std::stod
- string/std::stof
- string/std::stoi
- string/std::stol
- string/std::stold
- string/std::stoll
- string/std::stoul
- string/std::stoull
- string/std::swap
- string/std::to_string
- string/std::to_wstring
ms.assetid: 1a4ffd11-dce5-4cc6-a043-b95de034c7c4
helpviewer_keywords:
- std::getline [C++]
- std::stod [C++]
- std::stof [C++]
- std::stoi [C++]
- std::stol [C++]
- std::stold [C++]
- std::stoll [C++]
- std::stoul [C++]
- std::stoull [C++]
- std::swap [C++]
- std::to_string [C++]
- std::to_wstring [C++]
ms.openlocfilehash: dbcc4a86731bba092d8358a046fd3f9eb949f91f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214965"
---
# <a name="ltstringgt-functions"></a>&lt;řetězcové&gt; funkce

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[adresu](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a>getline

Extrahuje řetězce ze vstupního datového proudu řádek po řádku.

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delimiter);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delimiter);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& in_stream,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

*in_stream*\
Vstupní datový proud, ze kterého má být extrahován řetězec.

\ *str*
Řetězec, do kterého jsou čteny znaky ze vstupního datového proudu.

\ *oddělovače*
Oddělovač řádků.

### <a name="return-value"></a>Návratová hodnota

Vstupní datový proud *in_stream*.

### <a name="remarks"></a>Poznámky

Dvojice podpisů funkcí označených `(1)` extrakci znaků od *in_stream* , dokud není *oddělovač* nalezen, a ukládá je do *str*.

Dvojice signatur funkcí označená `(2)` jako výchozí oddělovač řádků použít nový řádek a chová se jako `getline(in_stream, str, in_stream. widen('\n'))`.

Druhá funkce každého páru je analogická k prvnímu typu pro podporu [odkazů rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

Extrakce se zastaví, když dojde k jedné z následujících akcí:

- Na konci souboru se v takovém případě příznak interního stavu *in_stream* nastaví na `ios_base::eofbit`.

- Poté, co funkce extrahuje prvek, který se porovná s *oddělovačem*. Element se nevrátí ani nepřipojí k řízené sekvenci.

- Poté, co funkce získá `str.`[max_size](../standard-library/basic-string-class.md#max_size) prvky. Příznak interního stavu *in_stream* je nastaven na hodnotu `ios_base::failbit`.

- Jiná jiná chyba než ta, která byla dříve uvedena v seznamu; příznak interního stavu *in_stream* je nastaven na hodnotu `ios_base::badbit`.

Informace o příznacích interního stavu naleznete v tématu [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

Pokud funkce extrahuje žádné prvky, příznak interního stavu *in_stream* je nastaven na hodnotu `ios_base::failbit`. V každém případě `getline` vrátí *in_stream*.

Pokud je vyvolána výjimka, *in_stream* a *str* zůstanou v platném stavu.

### <a name="example"></a>Příklad

Následující kód ukazuje `getline()` ve dvou režimech: nejprve s výchozím oddělovačem (nový řádek) a druhým s prázdným znakem jako oddělovač. Znak konce souboru (CTRL-Z na klávesnici) slouží k řízení ukončení smyčky while. Tato hodnota nastaví příznak interního stavu `cin` na `eofbit`, který musí být smazán pomocí [basic_ios:: Clear ()](../standard-library/basic-ios-class.md#clear) před tím, než druhý bude smyčka fungovat správně.

```cpp
// compile with: /EHsc /W4
#include <string>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    string str;
    vector<string> v1;
    cout << "Enter a sentence, press ENTER between sentences. (Ctrl-Z to stop): " << endl;
    // Loop until end-of-file (Ctrl-Z) is input, store each sentence in a vector.
    // Default delimiter is the newline character.
    while (getline(cin, str)) {
        v1.push_back(str);
    }

    cout << "The following input was stored with newline delimiter:" << endl;
    for (const auto& p : v1) {
        cout << p << endl;
    }

    cin.clear();

    vector<string> v2;
    // Now try it with a whitespace delimiter
    while (getline(cin, str, ' ')) {
        v2.push_back(str);
    }

    cout << "The following input was stored with whitespace as delimiter:" << endl;
    for (const auto& p : v2) {
        cout << p << endl;
    }
}
```

## <a name="stod"></a><a name="stod"></a>stod

Převede posloupnost znaků na **`double`** .

```cpp
double stod(
    const string& str,
    size_t* idx = 0);

double stod(
    const wstring& str,
    size_t* idx = 0
;
```

### <a name="parameters"></a>Parametry

\ *str*
Sekvence znaků, která má být převedena.

\ *IDX*
Hodnota indexu prvního nepřevedeného znaku.

### <a name="return-value"></a>Návratová hodnota

Hodnota **`double`** .

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na hodnotu typu **`double`** jako if voláním `strtod( str.c_str(), _Eptr)`, kde `_Eptr` je objekt interní pro funkci. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu `out_of_range`. V opačném případě, pokud není *IDX* ukazatel s hodnotou null, funkce ukládá `*_Eptr -  str.c_str()` v `*idx` a vrátí hodnotu.

## <a name="stof"></a><a name="stof"></a>stof

Převede sekvenci znaků na float.

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parametry

\ *str*
Sekvence znaků, která má být převedena.

\ *IDX*
Hodnota indexu prvního nepřevedeného znaku.

### <a name="return-value"></a>Návratová hodnota

Hodnota **`float`** .

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na hodnotu typu **`float`** jako if voláním `strtof( str.c_str(), _Eptr)`, kde `_Eptr` je objekt interní pro funkci. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu `out_of_range`. V opačném případě, pokud není *IDX* ukazatel s hodnotou null, funkce ukládá `*_Eptr -  str.c_str()` v `*idx` a vrátí hodnotu.

## <a name="stoi"></a><a name="stoi"></a>stoi

Převede sekvenci znaků na celé číslo.

```cpp
int stoi(
    const string& str,
    size_t* idx = 0,
    int base = 10);

int stoi(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="return-value"></a>Návratová hodnota

Celočíselná hodnota.

### <a name="parameters"></a>Parametry

\ *str*
Sekvence znaků, která má být převedena.

\ *IDX*
Hodnota indexu prvního nepřevedeného znaku.

*základní*\
Základní číslo, které se má použít.

### <a name="remarks"></a>Poznámky

Funkce `stoi` Převede sekvenci znaků v *str* na hodnotu typu **`int`** a vrátí hodnotu. Například při předání sekvence znaků "10" hodnota vrácená `stoi` je celé číslo 10.

`stoi` se chová podobně jako funkce `strtol` pro jednobajtové znaky, pokud je volána způsobem `strtol( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt pro funkci interní. nebo `wcstol` pro velké znaky, pokud je volána podobným způsobem, `wcstol(Str.c_str(), _Eptr, idx)`. Další informace najdete v tématu [strtol, wcstol, _strtol_l _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Pokud `str.c_str() == *_Eptr`, `stoi` vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, nebo Pokud vrácená hodnota nemůže být reprezentována jako objekt typu **`int`** , vyvolá objekt typu `out_of_range`. V opačném případě, pokud není *IDX* ukazatel s hodnotou null, funkce ukládá `*_Eptr - str.c_str()` v `*idx`.

## <a name="stol"></a><a name="stol"></a>stol

Převede posloupnost znaků na **`long`** .

```cpp
long stol(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long stol(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parametry

\ *str*
Sekvence znaků, která má být převedena.

\ *IDX*
Hodnota indexu prvního nepřevedeného znaku.

*základní*\
Základní číslo, které se má použít.

### <a name="return-value"></a>Návratová hodnota

Hodnota Long-Integer.

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na hodnotu typu **`long`** jako if voláním `strtol( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt interní pro funkci. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu `out_of_range`. V opačném případě, pokud není *IDX* ukazatel s hodnotou null, funkce ukládá `*_Eptr -  str.c_str()` v `*idx` a vrátí hodnotu.

## <a name="stold"></a><a name="stold"></a>stold

Převede posloupnost znaků na **`long double`** .

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parametry

\ *str*
Sekvence znaků, která má být převedena.

\ *IDX*
Hodnota indexu prvního nepřevedeného znaku.

### <a name="return-value"></a>Návratová hodnota

Hodnota **`long double`** .

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na hodnotu typu **`long double`** jako if voláním `strtold( str.c_str(), _Eptr)`, kde `_Eptr` je objekt interní pro funkci. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu `out_of_range`. V opačném případě, pokud není *IDX* ukazatel s hodnotou null, funkce ukládá `*_Eptr -  str.c_str()` v `*idx` a vrátí hodnotu.

## <a name="stoll"></a><a name="stoll"></a>stoll

Převede posloupnost znaků na **`long long`** .

```cpp
long long stoll(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long long stoll(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parametry

\ *str*
Sekvence znaků, která má být převedena.

\ *IDX*
Hodnota indexu prvního nepřevedeného znaku.

*základní*\
Základní číslo, které se má použít.

### <a name="return-value"></a>Návratová hodnota

Hodnota **`long long`** .

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na hodnotu typu **`long long`** jako if voláním `strtoll( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt interní pro funkci. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu `out_of_range`. V opačném případě, pokud není *IDX* ukazatel s hodnotou null, funkce ukládá `*_Eptr -  str.c_str()` v `*idx` a vrátí hodnotu.

## <a name="stoul"></a><a name="stoul"></a>stoul

Převede sekvenci znaků na Long bez znaménka.

```cpp
unsigned long stoul(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long stoul(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parametry

\ *str*
Sekvence znaků, která má být převedena.

\ *IDX*
Hodnota indexu prvního nepřevedeného znaku.

*základní*\
Základní číslo, které se má použít.

### <a name="return-value"></a>Návratová hodnota

Hodnota bez znaménka Long-Integer.

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na hodnotu typu **`unsigned long`** jako if voláním `strtoul( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt interní pro funkci. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu `out_of_range`. V opačném případě, pokud není *IDX* ukazatel s hodnotou null, funkce ukládá `*_Eptr -  str.c_str()` v `*idx` a vrátí hodnotu.

## <a name="stoull"></a><a name="stoull"></a>stoull

Převede posloupnost znaků na **`unsigned long long`** .

```cpp
unsigned long long stoull(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long long stoull(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Parametry

\ *str*
Sekvence znaků, která má být převedena.

\ *IDX*
Hodnota indexu prvního nepřevedeného znaku.

*základní*\
Základní číslo, které se má použít.

### <a name="return-value"></a>Návratová hodnota

Hodnota **`unsigned long long`** .

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na hodnotu typu **`unsigned long long`** jako if voláním `strtoull( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt interní pro funkci. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu `out_of_range`. V opačném případě, pokud není *IDX* ukazatel s hodnotou null, funkce ukládá `*_Eptr -  str.c_str()` v `*idx` a vrátí hodnotu.

## <a name="swap"></a><a name="swap"></a>adresu

Vyměňuje pole znaků dvou řetězců.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*levý*\
Jeden řetězec, jehož prvky mají být prohozeny pomocí prvků jiného řetězce.

*pravé*\
Druhý řetězec, jehož prvky mají být prohozeny prvním řetězcem.

### <a name="remarks"></a>Poznámky

Funkce šablony spustí funkci specializovaného členu *Left*. [swap](../standard-library/basic-string-class.md#swap)(*Right*) pro řetězce, které zaručují konstantní složitost.

### <a name="example"></a>Příklad

```cpp
// string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   swap ( s1 , s2 );
   cout << "\nAfter swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;
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

## <a name="to_string"></a><a name="to_string"></a>to_string

Převede hodnotu na `string`.

```cpp
string to_string(int value);
string to_string(unsigned int value);
string to_string(long value);
string to_string(unsigned long value);
string to_string(long long value);
string to_string(unsigned long long value);
string to_string(float value);
string to_string(double value);
string to_string(long double value);
```

### <a name="parameters"></a>Parametry

*hodnota*\
Hodnota, která má být převedena.

### <a name="return-value"></a>Návratová hodnota

`string`, která představuje hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede *hodnotu* na sekvenci prvků uložených v objektu Array `Buf` interní funkce jako if voláním `sprintf(Buf, Fmt, value)`, kde `Fmt` je

- `"%d"`, je-li *hodnota* typu **`int`**

- `"%u"`, je-li *hodnota* typu **`unsigned int`**

- `"%ld"`, je-li *hodnota* typu **`long`**

- `"%lu"`, je-li *hodnota* typu **`unsigned long`**

- `"%lld"`, je-li *hodnota* typu **`long long`**

- `"%llu"`, je-li *hodnota* typu **`unsigned long long`**

- `"%f"`, je-li *hodnota* typu **`float`** nebo **`double`**

- `"%Lf"`, je-li *hodnota* typu **`long double`**

Funkce vrátí `string(Buf)`.

## <a name="to_wstring"></a><a name="to_wstring"></a>to_wstring

Převede hodnotu na široký řetězec.

```cpp
wstring to_wstring(int value);
wstring to_wstring(unsigned int value);
wstring to_wstring(long value);
wstring to_wstring(unsigned long value);
wstring to_wstring(long long value);
wstring to_wstring(unsigned long long value);
wstring to_wstring(float value);
wstring to_wstring(double value);
wstring to_wstring(long double value);
```

### <a name="parameters"></a>Parametry

*hodnota*\
Hodnota, která má být převedena.

### <a name="return-value"></a>Návratová hodnota

Široký řetězec, který představuje hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede *hodnotu* na sekvenci prvků uložených v objektu Array `Buf` interní funkce jako if voláním `swprintf(Buf, Len, Fmt, value)`, kde `Fmt` je

- `L"%d"`, je-li *hodnota* typu **`int`**

- `L"%u"`, je-li *hodnota* typu **`unsigned int`**

- `L"%ld"`, je-li *hodnota* typu **`long`**

- `L"%lu"`, je-li *hodnota* typu **`unsigned long`**

- `L"%lld"`, je-li *hodnota* typu **`long long`**

- `L"%llu"`, je-li *hodnota* typu **`unsigned long long`**

- `L"%f"`, je-li *hodnota* typu **`float`** nebo **`double`**

- `L"%Lf"`, je-li *hodnota* typu **`long double`**

Funkce vrátí `wstring(Buf)`.

## <a name="see-also"></a>Viz také

[\<řetězec >](../standard-library/string.md)
