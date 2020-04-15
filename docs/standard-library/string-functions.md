---
title: '&lt;funkce&gt; řetězce'
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
ms.openlocfilehash: 3f1dca71a6bb9d5461150378191b9373f907ecd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376665"
---
# <a name="ltstringgt-functions"></a>&lt;funkce&gt; řetězce

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[řekl](#stold)|
|[Stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[Swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a>getline

Extrahujte řetězce ze vstupního datového proudu po řádcích.

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
Vstupní datový proud, ze kterého má být řetězec extrahován.

*Str*\
Řetězec, do kterého jsou číst znaky ze vstupního datového proudu.

*Oddělovač*\
Oddělovač řádků.

### <a name="return-value"></a>Návratová hodnota

Vstupní datový proud *in_stream*.

### <a name="remarks"></a>Poznámky

Dvojice funkčních podpisů `(1)` označená extrahovat znaky z *in_stream,* dokud *oddělovač* je nalezen, jejich ukládání v *str*.

Dvojice označených `(2)` podpisů funkcí používá nový řádek jako výchozí oddělovač řádků a chová se jako `getline(in_stream, str, in_stream. widen('\n'))`.

Druhá funkce každé dvojice je analogová k první, která podporuje [rvalue reference](../cpp/lvalues-and-rvalues-visual-cpp.md).

Extrakce se zastaví, když dojde k jedné z následujících akcí:

- Na konci souboru, v takovém případě *in_stream* vnitřní příznak `ios_base::eofbit`stavu in_stream je nastavena na .

- Poté, co funkce extrahuje prvek, který porovnává rovná *oddělovač*. Prvek není získat zpět nebo připojen k řízené sekvence.

- Poté, co `str.`funkce extrahuje [max_size](../standard-library/basic-string-class.md#max_size) prvky. Příznak vnitřního stavu *in_stream* `ios_base::failbit`je nastaven na .

- Některé jiné chyby než ty, které byly dříve uvedeny; vnitřní státní příznak *in_stream* je `ios_base::badbit`nastaven na .

Informace o vnitřní příznaky stavu naleznete [v tématu ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Pokud funkce extrahuje žádné prvky, *in_stream* vnitřní stav `ios_base::failbit`příznak in_stream je nastavena na . V každém `getline` případě vrátí *in_stream*.

Pokud je vyvolána výjimka, *in_stream* a *str* jsou ponechány v platném stavu.

### <a name="example"></a>Příklad

Následující kód ukazuje `getline()` ve dvou režimech: nejprve s výchozím oddělovačem (nový řádek) a druhý s mezerami jako oddělovač. Znak konce souboru (CTRL-Z na klávesnici) se používá k řízení ukončení while smyčky. Tato hodnota nastaví vnitřní `cin` `eofbit`stav příznak u , který musí být vymazány s [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) před druhou, zatímco smyčky bude fungovat správně.

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

Převede posloupnost **`double`** znaků na .

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

*Str*\
Pořadí znaků, které mají být převedeny.

*Idx*\
Hodnota indexu prvního nepřevedeného znaku.

### <a name="return-value"></a>Návratová hodnota

Hodnota. **`double`**

### <a name="remarks"></a>Poznámky

Funkce převede posloupnost prvků v *str* **`double`** na hodnotu `strtod( str.c_str(), _Eptr)`typu `_Eptr` jako by voláním , kde je objekt vnitřní funkce. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové `errno`volání bylo nastaveno , `out_of_range`vyvolá objekt typu . Jinak pokud *idx* není ukazatel null, funkce `*_Eptr -  str.c_str()` `*idx` ukládá a vrátí hodnotu.

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

*Str*\
Pořadí znaků, které mají být převedeny.

*Idx*\
Hodnota indexu prvního nepřevedeného znaku.

### <a name="return-value"></a>Návratová hodnota

Hodnota. **`float`**

### <a name="remarks"></a>Poznámky

Funkce převede posloupnost prvků v *str* **`float`** na hodnotu `strtof( str.c_str(), _Eptr)`typu `_Eptr` jako by voláním , kde je objekt vnitřní funkce. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové `errno`volání bylo nastaveno , `out_of_range`vyvolá objekt typu . Jinak pokud *idx* není ukazatel null, funkce `*_Eptr -  str.c_str()` `*idx` ukládá a vrátí hodnotu.

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

Hodnota celéčíslo.

### <a name="parameters"></a>Parametry

*Str*\
Pořadí znaků, které mají být převedeny.

*Idx*\
Hodnota indexu prvního nepřevedeného znaku.

*Základní*\
Základ čísel, který chcete použít.

### <a name="remarks"></a>Poznámky

Funkce `stoi` převede posloupnost znaků v *str* **`int`** na hodnotu typu a vrátí hodnotu. Například při předání sekvence znaků "10", `stoi` hodnota vrácená je celé číslo 10.

`stoi`chová podobně jako funkce `strtol` pro jednobajtové znaky, když je `strtol( str.c_str(), _Eptr, idx)`volána `_Eptr` způsobem , kde je objekt vnitřní funkce; nebo `wcstol` pro široké znaky, když je to `wcstol(Str.c_str(), _Eptr, idx)`voláno podobným způsobem, . Další informace naleznete [v tématech strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Pokud `str.c_str() == *_Eptr` `stoi` , vyvolá objekt `invalid_argument`typu . Pokud by takové `errno`volání nastalo nebo pokud vrácená hodnota nemůže **`int`** být reprezentována jako `out_of_range`objekt typu , vyvolá objekt typu . V opačném případě pokud *idx* není ukazatel `*_Eptr - str.c_str()` null, funkce ukládá v `*idx`.

## <a name="stol"></a><a name="stol"></a>stol

Převede posloupnost **`long`** znaků na .

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

*Str*\
Pořadí znaků, které mají být převedeny.

*Idx*\
Hodnota indexu prvního nepřevedeného znaku.

*Základní*\
Základ čísel, který chcete použít.

### <a name="return-value"></a>Návratová hodnota

Hodnota dlouhého celého čísla.

### <a name="remarks"></a>Poznámky

Funkce převede posloupnost prvků v *str* **`long`** na hodnotu `strtol( str.c_str(), _Eptr, idx)`typu `_Eptr` jako by voláním , kde je objekt vnitřní funkce. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové `errno`volání bylo nastaveno , `out_of_range`vyvolá objekt typu . Jinak pokud *idx* není ukazatel null, funkce `*_Eptr -  str.c_str()` `*idx` ukládá a vrátí hodnotu.

## <a name="stold"></a><a name="stold"></a>řekl

Převede posloupnost **`long double`** znaků na .

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parametry

*Str*\
Pořadí znaků, které mají být převedeny.

*Idx*\
Hodnota indexu prvního nepřevedeného znaku.

### <a name="return-value"></a>Návratová hodnota

Hodnota. **`long double`**

### <a name="remarks"></a>Poznámky

Funkce převede posloupnost prvků v *str* **`long double`** na hodnotu `strtold( str.c_str(), _Eptr)`typu `_Eptr` jako by voláním , kde je objekt vnitřní funkce. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové `errno`volání bylo nastaveno , `out_of_range`vyvolá objekt typu . Jinak pokud *idx* není ukazatel null, funkce `*_Eptr -  str.c_str()` `*idx` ukládá a vrátí hodnotu.

## <a name="stoll"></a><a name="stoll"></a>Stoll

Převede posloupnost **`long long`** znaků na .

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

*Str*\
Pořadí znaků, které mají být převedeny.

*Idx*\
Hodnota indexu prvního nepřevedeného znaku.

*Základní*\
Základ čísel, který chcete použít.

### <a name="return-value"></a>Návratová hodnota

Hodnota. **`long long`**

### <a name="remarks"></a>Poznámky

Funkce převede posloupnost prvků v *str* **`long long`** na hodnotu `strtoll( str.c_str(), _Eptr, idx)`typu `_Eptr` jako by voláním , kde je objekt vnitřní funkce. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové `errno`volání bylo nastaveno , `out_of_range`vyvolá objekt typu . Jinak pokud *idx* není ukazatel null, funkce `*_Eptr -  str.c_str()` `*idx` ukládá a vrátí hodnotu.

## <a name="stoul"></a><a name="stoul"></a>stoul

Převede posloupnost znaků na dlouho neznatá.

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

*Str*\
Pořadí znaků, které mají být převedeny.

*Idx*\
Hodnota indexu prvního nepřevedeného znaku.

*Základní*\
Základ čísel, který chcete použít.

### <a name="return-value"></a>Návratová hodnota

Nepodepsaná hodnota dlouhého čísla.

### <a name="remarks"></a>Poznámky

Funkce převede posloupnost prvků v *str* **`unsigned long`** na hodnotu `strtoul( str.c_str(), _Eptr, idx)`typu `_Eptr` jako by voláním , kde je objekt vnitřní funkce. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové `errno`volání bylo nastaveno , `out_of_range`vyvolá objekt typu . Jinak pokud *idx* není ukazatel null, funkce `*_Eptr -  str.c_str()` `*idx` ukládá a vrátí hodnotu.

## <a name="stoull"></a><a name="stoull"></a>stoull

Převede posloupnost **`unsigned long long`** znaků na .

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

*Str*\
Pořadí znaků, které mají být převedeny.

*Idx*\
Hodnota indexu prvního nepřevedeného znaku.

*Základní*\
Základ čísel, který chcete použít.

### <a name="return-value"></a>Návratová hodnota

Hodnota. **`unsigned long long`**

### <a name="remarks"></a>Poznámky

Funkce převede posloupnost prvků v *str* **`unsigned long long`** na hodnotu `strtoull( str.c_str(), _Eptr, idx)`typu `_Eptr` jako by voláním , kde je objekt vnitřní funkce. Pokud `str.c_str() == *_Eptr`, vyvolá objekt typu `invalid_argument`. Pokud by takové `errno`volání bylo nastaveno , `out_of_range`vyvolá objekt typu . Jinak pokud *idx* není ukazatel null, funkce `*_Eptr -  str.c_str()` `*idx` ukládá a vrátí hodnotu.

## <a name="swap"></a><a name="swap"></a>Swap

Vyměňuje pole znaků dvou řetězců.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Jeden řetězec, jehož prvky mají být zaměněny s prvky jiného řetězce.

*Právo*\
Druhý řetězec, jehož prvky mají být vyměněny za první řetězec.

### <a name="remarks"></a>Poznámky

Funkce šablony provede specializovanou člennou funkci *vlevo*. [swap](../standard-library/basic-string-class.md#swap)*(vpravo)* pro řetězce, což zaručuje neustálou složitost.

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

Převede hodnotu `string`na .

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

*Hodnotu*\
Hodnota, která má být převedena.

### <a name="return-value"></a>Návratová hodnota

Který `string` představuje hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede *hodnotu* na posloupnost prvků `Buf` uložených v objektu `sprintf(Buf, Fmt, value)`pole `Fmt` uvnitř funkce jako volání , kde je

- `"%d"`pokud je *hodnota* typu**`int`**

- `"%u"`pokud je *hodnota* typu**`unsigned int`**

- `"%ld"`pokud je *hodnota* typu**`long`**

- `"%lu"`pokud je *hodnota* typu**`unsigned long`**

- `"%lld"`pokud je *hodnota* typu**`long long`**

- `"%llu"`pokud je *hodnota* typu**`unsigned long long`**

- `"%f"`pokud *value* je hodnota **`float`** typu nebo**`double`**

- `"%Lf"`pokud je *hodnota* typu**`long double`**

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

*Hodnotu*\
Hodnota, která má být převedena.

### <a name="return-value"></a>Návratová hodnota

Široký řetězec, který představuje hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede *hodnotu* na posloupnost prvků `Buf` uložených v objektu `swprintf(Buf, Len, Fmt, value)`pole `Fmt` uvnitř funkce jako volání , kde je

- `L"%d"`pokud je *hodnota* typu**`int`**

- `L"%u"`pokud je *hodnota* typu**`unsigned int`**

- `L"%ld"`pokud je *hodnota* typu**`long`**

- `L"%lu"`pokud je *hodnota* typu**`unsigned long`**

- `L"%lld"`pokud je *hodnota* typu**`long long`**

- `L"%llu"`pokud je *hodnota* typu**`unsigned long long`**

- `L"%f"`pokud *value* je hodnota **`float`** typu nebo**`double`**

- `L"%Lf"`pokud je *hodnota* typu**`long double`**

Funkce vrátí `wstring(Buf)`.

## <a name="see-also"></a>Viz také

[\<řetězec>](../standard-library/string.md)
