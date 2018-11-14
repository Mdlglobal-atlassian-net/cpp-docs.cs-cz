---
title: '&lt;řetězec&gt; funkce'
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
ms.openlocfilehash: d10af9bc32acd730db1fe9da3775ac2aa84e5fff
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519208"
---
# <a name="ltstringgt-functions"></a>&lt;řetězec&gt; funkce

||||
|-|-|-|
|[getline](#getline)|[stod –](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[Prohození](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a>  getline

Extrahuje řetězce z vstupní datový proud řádek po řádku.

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

*is*<br/>
Vstupní datový proud, ze kterého má být extrahován řetězec.

*str*<br/>
Řetězec, do kterého se čtení znaků ze vstupního datového proudu.

*Delim*<br/>
Oddělovač řádků.

### <a name="return-value"></a>Návratová hodnota

Vstupní datový proud *je*.

### <a name="remarks"></a>Poznámky

Pár signatury funkce označené `(1)` extrahovat znaky z *je* dokud *delim* nenajde, jejich uložením v *str*.

Pár signatury funkce označené `(2)` znaku nového řádku použijte jako oddělovač výchozí řádek a chovat stejně jako **getline**(`is`, `str`, `is`. `widen`(' `\n`')).

Druhá funkce každé dvojice je analogie té předchozí pro podporu [odkazy rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

Extrakce chvíle, kdy dojde k jedné z následujících akcí:

- Na ukončení souboru v takovém případě příznak vnitřní stav *je* je nastavena na `ios_base::eofbit`.

- Po funkci extrahuje element, který při porovnání rovna `delim`, v takovém případě elementu je vrátit ani připojenou k řízené sekvence.

- Po funkci extrahuje `str.` [max_size](../standard-library/basic-string-class.md#max_size) prvků, ve kterém malá a velká příznak vnitřní stav *je* je nastavena na `ios_base::failbit`.

- Jiná chyba než ty, které dříve uvedené, v takovém případě příznak vnitřní stav *je* nastavený na `ios_base::badbit`

Informace o vnitřní stav příznaků najdete v tématu [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Pokud funkci extrahuje žádné elementy, vnitřní stav příznak *je* je nastavena na `ios_base::failbit`. V každém případě `getline` vrátí *je*.

Pokud je vyvolána výjimka, *je* a *str* jsou ponechána v platném stavu.

### <a name="example"></a>Příklad

Následující kód ukazuje `getline()` ve dvou režimech: nejdřív s výchozím oddělovačem (nový řádek) a druhý s mezery jako oddělovače. Znak koncové souboru (CTRL-Z na klávesnici) se používá k řízení ukončení while smyčky. Tím se nastaví vnitřní stav příznak `cin` k `eofbit`, které musí být zrušeno zaškrtnutí s [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) před sekundu, zatímco smyčka bude fungovat správně.

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

Převede znakovou sekvenci k **double**.

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
|*str*|Sekvence znaků, který má být převeden.|
|*IDX*|Hodnota indexu prvního nepřevedeném znaku.|

### <a name="return-value"></a>Návratová hodnota

**Double** hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí prvků v *str* na hodnotu `val` typu **double** jako kdyby volala `strtod( str.c_str(), _Eptr)`, kde `_Eptr` je interní pro funkci, objekt. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud taková volání by nastavit `errno`, vyvolá objekt typu `out_of_range`. Jinak, pokud *idx* není ukazatel s hodnotou null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stof"></a>  stof

Převede znakovou sekvenci na typ float.

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
|*str*|Sekvence znaků, který má být převeden.|
|*IDX*|Hodnota indexu prvního nepřevedeném znaku.|

### <a name="return-value"></a>Návratová hodnota

Hodnota float.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí prvků v *str* na hodnotu `val` typu **float** jako kdyby volala `strtof( str.c_str(), _Eptr)`, kde `_Eptr` je interní pro funkci, objekt. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud taková volání by nastavit `errno`, vyvolá objekt typu `out_of_range`. Jinak, pokud *idx* není ukazatel s hodnotou null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stoi"></a>  stoi

Převede znakovou sekvenci na celé číslo.

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
|*str*|Sekvence znaků, který má být převeden.|
|*IDX*|Obsahuje index prvního znaku nepřevedeném návratu.|
|*base*|Počet základních k použití.|

### <a name="remarks"></a>Poznámky

Funkce `stoi` převede sekvenci znaků v *str* na hodnotu typu **int** a vrátí hodnotu. Například při předání sekvence znaků "10", vrácena hodnota `stoi` je celočíselná hodnota 10.

`stoi` se chová podobně jako funkce `strtol` pro jednobajtové znaky, když je volána způsobem `strtol( str.c_str(), _Eptr, idx)`, kde `_Eptr` je interní pro funkci, objekt nebo `wcstol` pro široké znaky, když je volána v podobným způsobem, `wcstol(Str.c_str(), _Eptr, idx)`. Další informace najdete v tématu [strtol – wcstol –, _strtol_l – _wcstol_l –](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Pokud `str.c_str() == *_Eptr`, `stoi` vyvolá objekt typu `invalid_argument`. Pokud taková volání by nastavit `errno`, nebo pokud vrácená hodnota nemůže být reprezentovaný jako objekt typu **int**, vyvolá objekt typu `out_of_range`. Jinak, pokud *idx* není ukazatel s hodnotou null, funkce úložiště `*_Eptr - str.c_str()` v `*idx`.

## <a name="stol"></a>  stol

Převede znakovou sekvenci k **dlouhé**.

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
|*str*|Sekvence znaků, který má být převeden.|
|*IDX*|Hodnota indexu prvního nepřevedeném znaku.|
|*base*|Počet základních k použití.|

### <a name="return-value"></a>Návratová hodnota

Hodnotu typu long integer.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí prvků v *str* na hodnotu `val` typu **dlouhé** jako kdyby volala `strtol( str.c_str(), _Eptr, idx)`, kde `_Eptr` je interní pro funkci, objekt. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud taková volání by nastavit `errno`, vyvolá objekt typu `out_of_range`. Jinak, pokud *idx* není ukazatel s hodnotou null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stold"></a>  stold

Převede znakovou sekvenci k **long double**.

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
|*str*|Sekvence znaků, který má být převeden.|
|*IDX*|Hodnota indexu prvního nepřevedeném znaku.|

### <a name="return-value"></a>Návratová hodnota

**Long double** hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí prvků v *str* na hodnotu `val` typu **long double** jako kdyby volala `strtold( str.c_str(), _Eptr)`, kde `_Eptr` je interní pro funkci, objekt. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud taková volání by nastavit `errno`, vyvolá objekt typu `out_of_range`. Jinak, pokud *idx* není ukazatel s hodnotou null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stoll"></a>  stoll

Převede znakovou sekvenci k **long long**.

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
|*str*|Sekvence znaků, který má být převeden.|
|*IDX*|Hodnota indexu prvního nepřevedeném znaku.|
|*base*|Počet základních k použití.|

### <a name="return-value"></a>Návratová hodnota

**Long long** hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí prvků v *str* na hodnotu `val` typu **long long** jako kdyby volala `strtoll( str.c_str(), _Eptr, idx)`, kde `_Eptr` je interní pro funkci, objekt. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud taková volání by nastavit `errno`, vyvolá objekt typu `out_of_range`. Jinak, pokud *idx* není ukazatel s hodnotou null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stoul"></a>  stoul

Převede znakovou sekvenci na nepodepsaný dlouhý.

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
|*str*|Sekvence znaků, který má být převeden.|
|*IDX*|Hodnota indexu prvního nepřevedeném znaku.|
|*base*|Počet základních k použití.|

### <a name="return-value"></a>Návratová hodnota

Hodnota bez znaménka typu long integer.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí prvků v *str* na hodnotu `val` typu **unsigned long** jako kdyby volala `strtoul( str.c_str(), _Eptr, idx)`, kde `_Eptr` je interní pro funkci, objekt . Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud taková volání by nastavit `errno`, vyvolá objekt typu `out_of_range`. Jinak, pokud *idx* není ukazatel s hodnotou null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="stoull"></a>  stoull

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
|*str*|Sekvence znaků, který má být převeden.|
|*IDX*|Hodnota indexu prvního nepřevedeném znaku.|
|*base*|Počet základních k použití.|

### <a name="return-value"></a>Návratová hodnota

**Unsigned long long.** hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede pořadí prvků v *str* na hodnotu `val` typu **unsigned long long.** jako kdyby volala `strtoull( str.c_str(), _Eptr, idx)`, kde `_Eptr` je interní objekt funkce. Pokud ` str.c_str() == *_Eptr` vyvolá objekt typu `invalid_argument`. Pokud taková volání by nastavit `errno`, vyvolá objekt typu `out_of_range`. Jinak, pokud *idx* není ukazatel s hodnotou null, funkce úložiště `*_Eptr -  str.c_str()` v `*idx` a vrátí `val`.

## <a name="swap"></a>  Prohození

Vymění pole znaků dva řetězce.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Jeden řetězec, jehož prvky mají vyměnit s těmi, která z jiného řetězce.

*doprava*<br/>
Další řetězec, jehož prvky mají vyměnit s první řetězec.

### <a name="remarks"></a>Poznámky

Funkce šablony provede speciální členská funkce *levé*.[ Prohození](../standard-library/basic-string-class.md#swap)(*správné*) pro řetězce, který zaručuje konstantní složitost.

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

## <a name="to_string"></a>  to_string

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
|*Val*|Hodnota, která má být převedena.|

### <a name="return-value"></a>Návratová hodnota

`string` , Který představuje hodnotu.

### <a name="remarks"></a>Poznámky

Funkce převede *Val* na řadu prvků, které jsou uloženy v objektu pole `Buf` interní pro funkci, jako kdyby volala `sprintf(Buf, Fmt, Val)`, kde `Fmt` je

- `"%d"` Pokud `Val` má typ **int**

- `"%u"` Pokud `Val` má typ **int bez znaménka**

- `"%ld"` Pokud `Val` má typ **dlouhý**

- `"%lu"` Pokud `Val` má typ **unsigned long**

- `"%lld"` Pokud `Val` má typ **long long**

- `"%llu"` Pokud `Val` má typ **unsigned long long.**

- `"%f"` Pokud `Val` má typ **float** nebo **double**

- `"%Lf"` Pokud `Val` má typ **long double**

Funkce vrátí `string(Buf)`.

## <a name="to_wstring"></a>  to_wstring

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

Funkce převede `Val` na řadu prvků, které jsou uloženy v objektu pole `Buf` interní pro funkci, jako kdyby volala `swprintf(Buf, Len, Fmt, Val)`, kde `Fmt` je

- `L"%d"` Pokud `Val` má typ **int**

- `L"%u"` Pokud `Val` má typ **int bez znaménka**

- `L"%ld"` Pokud `Val` má typ **dlouhý**

- `L"%lu"` Pokud `Val` má typ **unsigned long**

- `L"%lld"` Pokud `Val` má typ **long long**

- `L"%llu"` Pokud `Val` má typ **unsigned long long.**

- `L"%f"` Pokud `Val` má typ **float** nebo **double**

- `L"%Lf"` Pokud `Val` má typ **long double**

Funkce vrátí `wstring(Buf)`.

## <a name="see-also"></a>Viz také:

[\<řetězec >](../standard-library/string.md)<br/>
