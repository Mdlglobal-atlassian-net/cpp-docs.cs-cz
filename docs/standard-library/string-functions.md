---
title: '&lt;řetězec&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
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
ms.workload:
- cplusplus
ms.openlocfilehash: 26fe9fab46beb2333df3fae351f99bb661f6d3e1
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltstringgt-functions"></a>&lt;řetězec&gt; funkce

||||
|-|-|-|
|[getline](#getline)|[stod –](#stod)|[stof –](#stof)|
|[stoi –](#stoi)|[stol –](#stol)|[stold –](#stold)|
|[stoll –](#stoll)|[stoul –](#stoul)|[stoull –](#stoull)|
|[Swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a>  getline

Extrahuje řetězce z vstupního datového proudu řádek po řádku.

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delim);


template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& is,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delim);


// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str);


template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& is,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parametry

`is` Vstupní datový proud, ze které je extrahována řetězec.

`str` Řetězec, do kterého se čtou znaky ze vstupního datového proudu.

`delim` Oddělovač řádků.

### <a name="return-value"></a>Návratová hodnota

Vstupní datový proud `is`.

### <a name="remarks"></a>Poznámky

Dvojice funkce podpisy označena `(1)` extrahuje znaky z `is` dokud `delim` nenajde, uložit je do v `str`.

Dvojice funkce podpisy označena `(2)` pomocí nového řádku jako oddělovač řádků výchozí a chovat jako **getline**( `is`, `str`, `is`. `widen`(' `\n`')).

Druhý každý pár je analogie na první z nich pro podporu [odkazy rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

Extrakce zastaví, když dojde k jedné z následujících akcí:

- Na koncové souboru v takovém případě příznak vnitřní stav `is` je nastaven na `ios_base::eofbit`.

- Po funkce extrahuje element, který porovnává rovna **delim**, v takovém případě elementu je vrátit zpět ani připojenou k řízené sekvenci.

- Po funkce extrahuje `str.` [max_size](../standard-library/basic-string-class.md#max_size) prvky, ve kterém případ příznak vnitřní stav `is` je nastaven na `ios_base::failbit`.

- Některé jiné chybě, která dříve uvedené, v takovém případě příznak vnitřní stav `is` nastavený na `ios_base::badbit`

Informace o vnitřní stav příznaky najdete v tématu [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Pokud funkci extrahuje žádné elementy, vnitřní stav příznak `is` je nastaven na `ios_base::failbit`. V každém případě `getline` vrátí `is`.

Pokud je vyvolána výjimka, `is` a `str` jsou ponechána v platném stavu.

### <a name="example"></a>Příklad

Následující kód ukazuje `getline()` ve dvou režimech: nejdřív se výchozí oddělovač (každý na jednom řádku) a druhý s prázdný znak jako oddělovač. Znak end souboru (CTRL-Z na klávesnici) se používá k řízení ukončení chvíli smyčky. Toto nastaví příznak vnitřní stav `cin` k `eofbit`, které je potřeba smazat s [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) před druhý při smyčka bude fungovat správně.

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

## <a name="stod"></a>  stod –

Převede posloupnost znaků do `double`.

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

|Parametr|Popis|
|---------------|-----------------|
|`str`|Posloupnost znaků, který má být převeden.|
|`idx`|Hodnota index prvního znaku nepřevedeném.|

### <a name="return-value"></a>Návratová hodnota

`double` Hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí elementů v `str` na hodnotu `val` typu `double` jakoby pomocí volání metody `strtod( str.c_str(), _Eptr)`, kde `_Eptr` je objekt interní funkce. Pokud ` str.c_str() == *_Eptr` vyhodí objekt typu `invalid_argument`. Pokud se nastavuje volání `errno`, vyvolá objekt typu `out_of_range`. Jinak Pokud `idx` není ukazatele null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stof"></a>  stof –

Převede na typ float posloupnost znaků.

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`str`|Posloupnost znaků, který má být převeden.|
|`idx`|Hodnota index prvního znaku nepřevedeném.|

### <a name="return-value"></a>Návratová hodnota

Hodnota typu float.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí elementů v `str` na hodnotu `val` typu `float` jakoby pomocí volání metody `strtof( str.c_str(), _Eptr)`, kde `_Eptr` je objekt interní funkce. Pokud ` str.c_str() == *_Eptr` vyhodí objekt typu `invalid_argument`. Pokud se nastavuje volání `errno`, vyvolá objekt typu `out_of_range`. Jinak Pokud `idx` není ukazatele null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stoi"></a>  stoi –

Převede posloupnost znaků na celé číslo.

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

|Parametr|Popis|
|---------------|-----------------|
|`str`|Posloupnost znaků, který má být převeden.|
|`idx`|Obsahuje index prvního znaku nepřevedeném na vrátit.|
|`base`|Počet základní použití.|

### <a name="remarks"></a>Poznámky

Funkce `stoi` převede posloupnost znaků v `str` na hodnotu typu `int` a vrátí hodnotu. Například když uplyne posloupnost znaků "10", hodnota vrácený `stoi` je celé číslo 10.

`stoi` funkce se chová podobně jako `strtol` jednobajtové znaky, když je volána způsobem `strtol( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt interní funkci; nebo `wcstol` pro široké znaky, když je volána v podobným způsobem, `wcstol(Str.c_str(), _Eptr, idx)`. Další informace najdete v tématu [strtol –, wcstol –, _strtol_l –, _wcstol_l –](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Pokud `str.c_str() == *_Eptr`, `stoi` objekt typu, vyvolá `invalid_argument`. Pokud se nastavuje volání `errno`, nebo pokud vrácená hodnota nemůže být reprezentován jako objekt typu `int`, vyvolá objekt typu `out_of_range`. Jinak Pokud `idx` není ukazatele null, funkce úložiště `*_Eptr - str.c_str()` v `*idx`.

## <a name="stol"></a>  stol –

Převede posloupnost znaků do `long`.

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

|Parametr|Popis|
|---------------|-----------------|
|`str`|Posloupnost znaků, který má být převeden.|
|`idx`|Hodnota index prvního znaku nepřevedeném.|
|`base`|Počet základní použití.|

### <a name="return-value"></a>Návratová hodnota

Long – celočíselná hodnota.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí elementů v `str` na hodnotu `val` typu `long` jakoby pomocí volání metody `strtol( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt interní funkce. Pokud ` str.c_str() == *_Eptr` vyhodí objekt typu `invalid_argument`. Pokud se nastavuje volání `errno`, vyvolá objekt typu `out_of_range`. Jinak Pokud `idx` není ukazatele null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stold"></a>  stold –

Převede posloupnost znaků do `long double`.

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`str`|Posloupnost znaků, který má být převeden.|
|`idx`|Hodnota index prvního znaku nepřevedeném.|

### <a name="return-value"></a>Návratová hodnota

`long double` Hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí elementů v `str` na hodnotu `val` typu `long double` jakoby pomocí volání metody `strtold( str.c_str(), _Eptr)`, kde `_Eptr` je objekt interní funkce. Pokud ` str.c_str() == *_Eptr` vyhodí objekt typu `invalid_argument`. Pokud se nastavuje volání `errno`, vyvolá objekt typu `out_of_range`. Jinak Pokud `idx` není ukazatele null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stoll"></a>  stoll –

Převede posloupnost znaků do `long long`.

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

|Parametr|Popis|
|---------------|-----------------|
|`str`|Posloupnost znaků, který má být převeden.|
|`idx`|Hodnota index prvního znaku nepřevedeném.|
|`base`|Počet základní použití.|

### <a name="return-value"></a>Návratová hodnota

`long long` Hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí elementů v `str` na hodnotu `val` typu `long long` jakoby pomocí volání metody `strtoll( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt interní funkce. Pokud ` str.c_str() == *_Eptr` vyhodí objekt typu `invalid_argument`. Pokud se nastavuje volání `errno`, vyvolá objekt typu `out_of_range`. Jinak Pokud `idx` není ukazatele null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stoul"></a>  stoul –

Převede nepodepsaný posloupnost znaků dlouhé.

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

|Parametr|Popis|
|---------------|-----------------|
|`str`|Posloupnost znaků, který má být převeden.|
|`idx`|Hodnota index prvního znaku nepřevedeném.|
|`base`|Počet základní použití.|

### <a name="return-value"></a>Návratová hodnota

Nepodepsané dlouho celočíselná hodnota.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí elementů v `str` na hodnotu `val` typu `unsigned long` jakoby pomocí volání metody `strtoul( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt interní funkce. Pokud ` str.c_str() == *_Eptr` vyhodí objekt typu `invalid_argument`. Pokud se nastavuje volání `errno`, vyvolá objekt typu `out_of_range`. Jinak Pokud `idx` není ukazatele null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stoull"></a>  stoull –

Převede posloupnost znaků do `unsigned long long`.

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

|Parametr|Popis|
|---------------|-----------------|
|`str`|Posloupnost znaků, který má být převeden.|
|`idx`|Hodnota index prvního znaku nepřevedeném.|
|`base`|Počet základní použití.|

### <a name="return-value"></a>Návratová hodnota

`unsigned long long` Hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí elementů v `str` na hodnotu `val` typu `unsigned long long` jakoby pomocí volání metody `strtoull( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt interní funkce. Pokud ` str.c_str() == *_Eptr` vyhodí objekt typu `invalid_argument`. Pokud se nastavuje volání `errno`, vyvolá objekt typu `out_of_range`. Jinak Pokud `idx` není ukazatele null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="swap"></a>  Swap

Výměny pole znaků dva řetězce.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

`left` Jeden řetězec, jehož elementy jsou záměnu s těmi jiným řetězcem.

`right` Jiný řetězec, jehož elementy jsou k si místo se první řetězec.

### <a name="remarks"></a>Poznámky

Funkce šablony spustí speciální členské funkce *levém*.[ swap](../standard-library/basic-string-class.md#swap)(*správné*) pro řetězce, což zaručuje konstantní složitost.

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

## <a name="to_string"></a>  to_string –

Převede hodnotu na `string`.

```cpp
string to_string(int Val);
string to_string(unsigned int Val);
string to_string(long Val);
string to_string(unsigned long Val);
string to_string(long long Val);
string to_string(unsigned long long Val);
string to_string(float Val);
string to_string(double Val);
string to_string(long double Val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Val`|Hodnota, která má být převedena.|

### <a name="return-value"></a>Návratová hodnota

`string` Představující hodnotu.

### <a name="remarks"></a>Poznámky

Převede funkce `Val` pořadí elementů uložené v objektu array `Buf` vnitřní funkce, jako kdyby pomocí volání metody `sprintf(Buf, Fmt, Val)`, kde `Fmt` je

- `"%d"` Pokud `Val` má typ `int`

- `"%u"` Pokud `Val` má typ `unsigned int`

- `"%ld"` Pokud `Val` má typ `long`

- `"%lu"` Pokud `Val` má typ `unsigned long`

- `"%lld"` Pokud `Val` má typ `long long`

- `"%llu"` Pokud `Val` má typ `unsigned long long`

- `"%f"` Pokud `Val` má typ `float` nebo `double`

- `"%Lf"` Pokud `Val` má typ `long double`

Funkce vrátí hodnotu `string(Buf)`.

## <a name="to_wstring"></a>  to_wstring –

Převede hodnotu na široký řetězec.

```cpp
wstring to_wstring(int Val);
wstring to_wstring(unsigned int Val);
wstring to_wstring(long Val);
wstring to_wstring(unsigned long Val);
wstring to_wstring(long long Val);
wstring to_wstring(unsigned long long Val);
wstring to_wstring(float Val);
wstring to_wstring(double Val);
wstring to_wstring(long double Val);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Val`|Hodnota, která má být převedena.|

### <a name="return-value"></a>Návratová hodnota

Široký řetězec, který představuje hodnotu.

### <a name="remarks"></a>Poznámky

Převede funkce `Val` pořadí elementů uložené v objektu array `Buf` vnitřní funkce, jako kdyby pomocí volání metody `swprintf(Buf, Len, Fmt, Val)`, kde `Fmt` je

- `L"%d"` Pokud `Val` má typ `int`

- `L"%u"` Pokud `Val` má typ `unsigned int`

- `L"%ld"` Pokud `Val` má typ `long`

- `L"%lu"` Pokud `Val` má typ `unsigned long`

- `L"%lld"` Pokud `Val` má typ `long long`

- `L"%llu"` Pokud `Val` má typ `unsigned long long`

- `L"%f"` Pokud `Val` má typ `float` nebo `double`

- `L"%Lf"` Pokud `Val` má typ `long double`

Funkce vrátí hodnotu `wstring(Buf)`.

## <a name="see-also"></a>Viz také

[\<řetězec >](../standard-library/string.md)<br/>
