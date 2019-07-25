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
ms.openlocfilehash: 828aeb975178850f5c0a7ea3b7e982bbadd6e7c4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455602"
---
# <a name="ltstringgt-functions"></a>&lt;řetězcové&gt; funkce

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a>getline

Extrahuje řetězce ze vstupního datového proudu řádek po řádku.

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

*dojde*\
Vstupní datový proud, ze kterého má být extrahován řetězec.

*str*\
Řetězec, do kterého jsou čteny znaky ze vstupního datového proudu.

*delim*\
Oddělovač řádků.

### <a name="return-value"></a>Návratová hodnota

Vstupní datový proud *je*.

### <a name="remarks"></a>Poznámky

Pár signatur funkcí označených jako `(1)` extrahované znaky z *je* , dokud není nalezen *delim* a ukládá je do *str*.

Dvojice podpisů funkcí označená `(2)` jako výchozí oddělovač řádků používá nový řádek a chová se jako getline (`is`, `str`, `is`. `widen`(' `\n`')).

Druhá funkce každého páru je analogická k prvnímu typu pro podporu [odkazů rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

Extrakce se zastaví, když dojde k jedné z následujících akcí:

- Na konci souboru, v takovém případě je příznak interního stavu nastaven na  `ios_base::eofbit`.

- Poté, co funkce extrahuje prvek, který porovnává rovnost `delim`, v takovém případě se element nevrátí zpět ani nepřipojí k řízené sekvenci.

- Poté, co funkce `str.`extrahuje prvky [max_size](../standard-library/basic-string-class.md#max_size) , v takovém případě je příznak  interního stavu nastaven `ios_base::failbit`na hodnotu.

- Některá jiná jiná chyba než uvedená dřív, v takovém případě je příznak interního stavu  nastaven na hodnotu`ios_base::badbit`

Informace o příznacích interního stavu naleznete v tématu [ios_base:: iostate](../standard-library/ios-base-class.md#iostate).

Pokud funkce extrahuje žádné prvky, příznak interního stavu *je* nastaven na `ios_base::failbit`. V každém `getline` *případě vrátí hodnotu*.

Pokud je vyvolána výjimka, *je* a *str* ponechána v platném stavu.

### <a name="example"></a>Příklad

Následující kód ukazuje `getline()` ve dvou režimech: nejprve s výchozím oddělovačem (nový řádek) a druhým s prázdným znakem jako oddělovač. Znak konce souboru (CTRL-Z na klávesnici) slouží k řízení ukončení smyčky while. Tím se nastaví příznak `cin` interního stavu na `eofbit`, který musí být smazán pomocí [basic_ios:: Clear ()](../standard-library/basic-ios-class.md#clear) před tím, než druhý bude smyčka fungovat správně.

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

## <a name="stod"></a>stod

Převede posloupnost znaků na dvojitou hodnotu.

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
|*str*|Sekvence znaků, která má být převedena.|
|*idx*|Hodnota indexu prvního nepřevedeného znaku.|

### <a name="return-value"></a>Návratová hodnota

Hodnota typu **Double**

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na `val` hodnotu typu **Double** jako if voláním `strtod( str.c_str(), _Eptr)`, kde `_Eptr` je objekt pro funkci interní. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu. `out_of_range` V opačném případě, pokud není *IDX* ukazatel s hodnotou null, `*_Eptr -  str.c_str()` funkce `*idx` ukládá a `val`vrací.

## <a name="stof"></a>stof

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

|Parametr|Popis|
|---------------|-----------------|
|*str*|Sekvence znaků, která má být převedena.|
|*idx*|Hodnota indexu prvního nepřevedeného znaku.|

### <a name="return-value"></a>Návratová hodnota

Hodnota float.

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na `val` hodnotu typu **float** jako if voláním `strtof( str.c_str(), _Eptr)`, kde `_Eptr` je objekt pro funkci interní. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu. `out_of_range` V opačném případě, pokud není *IDX* ukazatel s hodnotou null, `*_Eptr -  str.c_str()` funkce `*idx` ukládá a `val`vrací.

## <a name="stoi"></a>stoi

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

|Parametr|Popis|
|---------------|-----------------|
|*str*|Sekvence znaků, která má být převedena.|
|*idx*|Obsahuje index prvního nepřevedeného znaku při návratu.|
|*base*|Základní číslo, které se má použít.|

### <a name="remarks"></a>Poznámky

Funkce `stoi` Převede sekvenci znaků v *str* na hodnotu typu **int** a vrátí hodnotu. Například při předání sekvence znaků "10" hodnota vrácená `stoi` hodnotou je celé číslo 10.

`stoi`se chová `strtol` podobně jako funkce pro jednobajtové znaky, pokud je volána způsobem `strtol( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt interní pro funkci; nebo `wcstol` pro velké znaky, pokud je volán podobným způsobem, `wcstol(Str.c_str(), _Eptr, idx)`. Další informace najdete v tématu [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Pokud `str.c_str() == *_Eptr` `invalid_argument`, `stoi` vyvolá objekt typu. Pokud by takové volání bylo nastaveno `errno`, nebo Pokud vrácená hodnota nemůže být reprezentována jako objekt typu **int**, vyvolá objekt typu `out_of_range`. V opačném případě, pokud není *IDX* ukazatel s hodnotou null, `*_Eptr - str.c_str()` funkce `*idx`ukládá do.

## <a name="stol"></a>stol

Převede sekvenci znaků na **Long**.

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
|*str*|Sekvence znaků, která má být převedena.|
|*idx*|Hodnota indexu prvního nepřevedeného znaku.|
|*base*|Základní číslo, které se má použít.|

### <a name="return-value"></a>Návratová hodnota

Hodnota Long-Integer.

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na `val` hodnotu typu **Long** , jako by bylo voláno voláním `strtol( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt pro funkci interní. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu. `out_of_range` V opačném případě, pokud není *IDX* ukazatel s hodnotou null, `*_Eptr -  str.c_str()` funkce `*idx` ukládá a `val`vrací.

## <a name="stold"></a>stold

Převede sekvenci znaků na **Long Double**.

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
|*str*|Sekvence znaků, která má být převedena.|
|*idx*|Hodnota indexu prvního nepřevedeného znaku.|

### <a name="return-value"></a>Návratová hodnota

Hodnota **Long Double** .

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na `val` hodnotu typu **Long Double** , jako by bylo voláno voláním `strtold( str.c_str(), _Eptr)`, kde `_Eptr` je objekt pro funkci interní. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu. `out_of_range` V opačném případě, pokud není *IDX* ukazatel s hodnotou null, `*_Eptr -  str.c_str()` funkce `*idx` ukládá a `val`vrací.

## <a name="stoll"></a>stoll

Převede sekvenci znaků na **dlouhou dobu**.

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
|*str*|Sekvence znaků, která má být převedena.|
|*idx*|Hodnota indexu prvního nepřevedeného znaku.|
|*base*|Základní číslo, které se má použít.|

### <a name="return-value"></a>Návratová hodnota

**Dlouhá dlouhá** hodnota.

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na `val` hodnotu typu **Long Long** , jako by bylo voláno voláním `strtoll( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt pro funkci interní. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu. `out_of_range` V opačném případě, pokud není *IDX* ukazatel s hodnotou null, `*_Eptr -  str.c_str()` funkce `*idx` ukládá a `val`vrací.

## <a name="stoul"></a>stoul

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

|Parametr|Popis|
|---------------|-----------------|
|*str*|Sekvence znaků, která má být převedena.|
|*idx*|Hodnota indexu prvního nepřevedeného znaku.|
|*base*|Základní číslo, které se má použít.|

### <a name="return-value"></a>Návratová hodnota

Hodnota bez znaménka Long-Integer.

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na `val` hodnotu typu **bez znaménka** jako if voláním `strtoul( str.c_str(), _Eptr, idx)`, kde `_Eptr` je objekt pro funkci interní. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu. `out_of_range` V opačném případě, pokud není *IDX* ukazatel s hodnotou null, `*_Eptr -  str.c_str()` funkce `*idx` ukládá a `val`vrací.

## <a name="stoull"></a>stoull

Převede znakovou sekvenci do **unsigned long long**.

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
|*str*|Sekvence znaků, která má být převedena.|
|*idx*|Hodnota indexu prvního nepřevedeného znaku.|
|*base*|Základní číslo, které se má použít.|

### <a name="return-value"></a>Návratová hodnota

Hodnota **bez znaménka Long Long** .

### <a name="remarks"></a>Poznámky

Funkce převede sekvenci prvků v *str* na `val` hodnotu typu **bez znaménka** , která se zavolá `strtoull( str.c_str(), _Eptr, idx)`, `_Eptr` Pokud je objekt pro funkci interní. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud by takové volání bylo nastaveno `errno`, vyvolá objekt typu. `out_of_range` V opačném případě, pokud není *IDX* ukazatel s hodnotou null, `*_Eptr -  str.c_str()` funkce `*idx` ukládá a `val`vrací.

## <a name="swap"></a>adresu

Vyměňuje pole znaků dvou řetězců.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*zbývá*\
Jeden řetězec, jehož prvky mají být prohozeny s jinými řetězci.

*Kliknutím*\
Druhý řetězec, jehož prvky mají být prohozeny prvním řetězcem.

### <a name="remarks"></a>Poznámky

Funkce šablony spustí funkci specializovaného členu *Left*. [prohodit](../standard-library/basic-string-class.md#swap) (*Right*) pro řetězce, které zaručují konstantní složitost.

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

## <a name="to_string"></a>to_string

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
|*Počítává*|Hodnota, která má být převedena.|

### <a name="return-value"></a>Návratová hodnota

Hodnota `string` , která představuje hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede hodnotu *Val* na sekvenci prvků uložených v objektu `Buf` Array pro funkci jako if voláním `sprintf(Buf, Fmt, Val)`, kde `Fmt` je

- `"%d"`Pokud `Val` má typ **int**

- `"%u"`IF `Val` má typ **unsigned int**

- `"%ld"`Pokud `Val` má typ **Long**

- `"%lu"`IF `Val` má typ **unsigned long**

- `"%lld"`Pokud `Val` má typ **Long Long**

- `"%llu"`IF `Val` má typ **unsigned long long**

- `"%f"`Pokud `Val` má typ **float** nebo **Double**

- `"%Lf"`IF `Val` typu **Long Double**

Funkce vrátí `string(Buf)`.

## <a name="to_wstring"></a>to_wstring

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

Funkce se převede `Val` na sekvenci prvků uložených v objektu `Buf` pole, který je interní pro funkci, jako if voláním `swprintf(Buf, Len, Fmt, Val)`, `Fmt` kde je

- `L"%d"`Pokud `Val` má typ **int**

- `L"%u"`IF `Val` má typ **unsigned int**

- `L"%ld"`Pokud `Val` má typ **Long**

- `L"%lu"`IF `Val` má typ **unsigned long**

- `L"%lld"`Pokud `Val` má typ **Long Long**

- `L"%llu"`IF `Val` má typ **unsigned long long**

- `L"%f"`Pokud `Val` má typ **float** nebo **Double**

- `L"%Lf"`IF `Val` typu **Long Double**

Funkce vrátí `wstring(Buf)`.

## <a name="see-also"></a>Viz také:

[\<> řetězců](../standard-library/string.md)
