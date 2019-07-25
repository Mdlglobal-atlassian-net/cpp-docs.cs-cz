---
title: path – třída
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 10c865aa2bc2431850c69e9dfedbef37414b2cb9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455102"
---
# <a name="path-class"></a>path – třída

Třída **path** ukládá objekt typu `string_type`, který je zde volán `myname` pro účely Exposition, vhodný pro použití jako cesta. `string_type`je synonymum pro `basic_string<value_type>`, kde `value_type` je synonymum pro **wchar_t** ve Windows nebo **char** v POSIX.

Další informace a příklady kódu naleznete v tématu [Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class path;
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Cesta](#path)|`path`Vytvoří.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[const_iterator](#const_iterator)|Synonymum pro `iterator`.|
|[iterator](#iterator)|Obousměrný konstantní iterátor, který určuje `path` `myname`komponenty.|
|[string_type](#string_type)|Typ je synonymum pro `basic_string<value_type>`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[příloh](#append)|Připojí určenou sekvenci k `mypath`, převede a vloží preferred_separator podle potřeby.|
|[assign](#assign)|Nahradí `mypath` zadanou sekvencí podle potřeby.|
|[ifunctiondiscovery](#begin)|`path::iterator` Vrátí označení prvního prvku cesty v cestě, pokud je k dispozici.|
|[c_str](#c_str)|Vrátí ukazatel na první znak v `mypath`.|
|[jejich](#clear)|Provede `mypath.clear()`.|
|[compare](#compare)|Vrátí hodnoty porovnání.|
|[concat](#compare)|Připojí určenou sekvenci k `mypath`převedené (ale nevloží oddělovač) podle potřeby.|
|[empty](#empty)|Vrátí `mypath.empty()`.|
|[účelu](#end)|Vrátí iterátor typu `iterator`konec sekvence.|
|[klapk](#extension)|Vrátí příponu `filename()`.|
|[Bitmap](#filename)|Vrátí součást kořenového adresáře pro pole jmen, `empty() path() : *--end()`konkrétně. Komponenta může být prázdná.|
|[generic_string](#generic_string)|Vrátí `this->string<Elem, Traits, Alloc>(al)` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.|
|[generic_u16string](#generic_u16string)|Vrátí `u16string()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.|
|[generic_u32string](#generic_u32string)|Vrátí `u32string()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.|
|[generic_u8string](#generic_u8string)|Vrátí `u8string()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.|
|[generic_wstring](#generic_wstring)|Vrátí `wstring()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.|
|[has_extension](#has_extension)|Vrátí `!extension().empty()`.|
|[has_filename](#has_filename)|Vrátí `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Vrátí `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Vrátí `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Vrátí `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Vrátí `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Vrátí `!root_path().empty()`.|
|[has_stem](#has_stem)|Vrátí `!stem().empty()`.|
|[is_absolute](#is_absolute)|Pro Windows vrátí `has_root_name() && has_root_directory()`funkce. U POSIX funkce vrátí `has_root_directory()`.|
|[is_relative](#is_relative)|Vrátí `!is_absolute()`.|
|[make_preferred](#make_preferred)|Převede jednotlivé oddělovače na preferred_separator podle potřeby.|
|[nativní](#native)|Vrátí `myname`.|
|[parent_path](#parent_path)|Vrátí komponentu nadřazené cesty pro `myname`.|
|[preferred_separator](#preferred_separator)|Objekt konstanty dává preferovanému znaku pro oddělení součástí cesty v závislosti na hostitelském operačním systému. |
|[relative_path](#relative_path)|Vrátí součást relativní cesty pro `myname`. |
|[remove_filename](#remove_filename)|Odstraní název souboru.|
|[replace_extension](#replace_extension)|Nahradí rozšíření `myname`. |
|[replace_filename](#replace_filename)|RReplaces název souboru.|
|[root_directory](#root_directory)|Vrátí součást `myname`kořenového adresáře. |
|[root_name](#root_name)|Vrátí komponentu `myname`názvu kořenového adresáře. |
|[root_path](#root_path)|Vrátí součást kořenové cesty pro `myname`.|
|[stonek](#stem)|Vrátí komponentu prvku `myname`. `stem`|
|[string](#string)|Převede sekvenci uloženou `mypath`v.|
|[swap](#swap)|Provede `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Převede sekvenci uloženou `mypath` v do UTF-16 a vrátí ji uloženou v objektu typu `u16string`.|
|[u32string](#u32string)|Převede sekvenci uloženou `mypath` v do UTF-32 a vrátí ji uloženou v objektu typu `u32string`.|
|[u8string](#u8string)|Převede sekvenci uloženou `mypath` v do UTF-8 a vrátí ji uloženou v objektu typu `u8string`.|
|[value_type](#value_type)|Typ popisuje prvky cesty, které jsou na něj přizpůsobeny hostitelským operačním systémem.|
|[wstring](#wstring)|Převede sekvenci, která `mypath` je uložena v, do kódování, které upřednostňuje hostitelský systém `wchar_t` pro sekvenci a vrátí ji uloženou v objektu `wstring`typu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_as)|Nahradí prvky cesty kopií jiné cesty.|
|[operator+=](#op_add)|Různé `concat` výrazy.|
|[operator/= – operátor](#op_divide)|Různé `append` výrazy.|
|[operátor string_type](#op_string)|Vrátí `myname`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> systému souborů

**Obor názvů:** std:: experimentální:: FileSystem

## <a name="append"></a>cesta:: Append

Připojí určenou sekvenci k `mypath`, převede a `preferred_separator` vloží podle potřeby.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Zdrojová*\
Zadaná sekvence

*první*\
Začátek zadaného pořadí.

*posledního*\
Konec zadaného pořadí.

## <a name="assign"></a>cesta:: přiřadit

Nahradí `mypath` zadanou sekvencí podle potřeby.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Zdrojová*\
Zadaná sekvence

*první*\
Začátek zadaného pořadí.

*posledního*\
Konec zadaného pořadí.

## <a name="begin"></a>cesta:: begin

`path::iterator` Vrátí označení prvního prvku cesty v cestě, pokud je k dispozici.

```cpp
iterator begin() const;
```

## <a name="c_str"></a>cesta:: c_str

Vrátí ukazatel na první znak v `mypath`.

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a>cesta:: Clear

Provede `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="compare"></a>cesta:: Compare

První funkce vrátí `mypath.compare(pval.native())`. Druhá funkce vrátí `mypath.compare(str)`. Třetí funkce vrátí `mypath.compare(ptr)`.

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*pval*\
Cesta, která se má porovnat

*str*\
Řetězec, který se má porovnat

*střed*\
Ukazatel na porovnání

## <a name="concat"></a>cesta:: Concat

Připojí určenou sekvenci k `mypath`převedené (ale nevloží oddělovač) podle potřeby.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Zdrojová*\
Zadaná sekvence

*první*\
Začátek zadaného pořadí.

*posledního*\
Konec zadaného pořadí.

## <a name="const_iterator"></a>cesta:: const_iterator

Synonymum pro `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>cesta:: Empty

Vrátí `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="end"></a>cesta:: end

Vrátí iterátor typu `iterator`konec sekvence.

```cpp
iterator end() const;
```

## <a name="extension"></a>cesta:: rozšíření

Vrátí příponu `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Poznámky

Vrátí příponu `filename() X` tohoto typu:

Pokud `X == path(".") || X == path("..")` nebo IF `X` neobsahuje tečku, přípona je prázdná.

V opačném případě přípona začíná (a obsahuje) tečku vpravo.

## <a name="filename"></a>cesta:: filename

Vrátí součást kořenového adresáře pro pole jmen, `empty() path() : *--end()`konkrétně. Komponenta může být prázdná.

```cpp
path filename() const;
```

## <a name="generic_string"></a>cesta:: generic_string

Vrátí `this->string<Elem, Traits, Alloc>(al)` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a>cesta:: generic_u16string

Vrátí `u16string()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a>cesta:: generic_u32string

Vrátí `u32string()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a>cesta:: generic_u8string

Vrátí `u8string()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a>cesta:: generic_wstring

Vrátí `wstring()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a>cesta:: has_extension

Vrátí `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a>cesta:: has_filename

Vrátí `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a>cesta:: has_parent_path

Vrátí `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a>cesta:: has_relative_path

Vrátí `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a>cesta:: has_root_directory

Vrátí `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>cesta:: has_root_name

Vrátí `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a>cesta:: has_root_path

Vrátí `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>cesta:: has_stem

Vrátí `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>cesta:: is_absolute

Pro Windows vrátí `has_root_name() && has_root_directory()`funkce. U POSIX funkce vrátí `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>cesta:: is_relative

Vrátí `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>cesta:: iterátor

Obousměrný konstantní iterátor, který určuje součásti cesty pro `myname`.

```cpp
class iterator
   {
   // bidirectional iterator for path
   typedef bidirectional_iterator_tag iterator_category;
   typedef path_type value_type;
   typedef ptrdiff_t difference_type;
   typedef const value_type *pointer;
   typedef const value_type& reference;
   // ...
   };
```

### <a name="remarks"></a>Poznámky

Třída popisuje obousměrný konstantní iterátor, který určuje `path` `myname` komponenty v sekvenci:

1. název kořenového adresáře, pokud je k dispozici

1. kořenový adresář, pokud je k dispozici

1. zbývající prvky adresáře nadřazeného objektu `path`, pokud jsou k dispozici, končící názvem souboru, pokud je k dispozici

Pro `pval` objekt typu `path`:

1. `path::iterator X = pval.begin()`Určuje první `path` prvek v cestě, pokud je k dispozici.

1. `X == pval.end()`má hodnotu true `X` , pokud body hned za koncem sekvence komponent.

3. `*X`Vrátí řetězec, který odpovídá aktuální součásti.

1. `++X`Určuje další komponentu v sekvenci, pokud je k dispozici.

1. `--X`určí předchozí komponentu v sekvenci, pokud je k dispozici.

1. Změna neověřuje všechny iterátory, které mají za následek určení `myname`prvků v. `myname`

## <a name="make_preferred"></a>cesta:: make_preferred

Převede každý oddělovač `preferred_separator` podle potřeby.

```cpp
path& make_preferred();
```

## <a name="native"></a>cesta:: nativní

Vrátí `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a>Path:: operator =

Nahradí prvky cesty kopií jiné cesty.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Cesta](../standard-library/path-class.md) , která se kopíruje `path`do.

*Zdrojová*\
Zdrojová cesta

### <a name="remarks"></a>Poznámky

První operátor členu `right.myname` kopíruje `myname`do. Druhý operátor členu přesune `right.myname` na `myname`. Třetí členský operátor se chová stejně jako `*this = path(source)`.

## <a name="op_add"></a>Path:: operator + =

Různé `concat` výrazy.

```cpp
path& operator+=(const path& right);
path& operator+=(const string_type& str);
path& operator+=(const value_type *ptr);
path& operator+=(value_type elem);

template <class Source>
path& operator+=(const Source& source);

template <class Elem>
path& operator+=(Elem elem);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Přidaná cesta

*str*\
Přidaný řetězec.

*střed*\
Přidaný ukazatel.

*elem*\
Přidané `value_type` nebo .`Elem`

*Zdrojová*\
Přidaný zdroj.

### <a name="remarks"></a>Poznámky

Členské funkce se chovají stejně jako následující odpovídající výrazy:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="op_divide"></a>Path:: operator/=

Různé `append` výrazy.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Přidaná cesta

*Zdrojová*\
Přidaný zdroj.

### <a name="remarks"></a>Poznámky

Členské funkce se chovají stejně jako následující odpovídající výrazy:

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a>cesta:: operator string_type

Vrátí `myname`.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a>cesta::p arent_path

Vrátí komponentu nadřazené cesty pro `myname`.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí komponentu nadřazené cesty pro `myname`, specifickou `myname` předponu po odebrání `filename().native()` a všechny bezprostředně předchozí oddělovače adresářů. (Pokud je, `begin() != end()`je-li kombinace všech prvků v rozsahu `[begin(), --end())` kombinována po sobě `operator/=`, použije se.) Komponenta může být prázdná.

## <a name="path"></a>cesta::p ATH

`path` Sestaví různými způsoby.

```cpp
path();

path(const path& right);
path(path&& right) noexcept;

template <class Source>
path(const Source& source);

template <class Source>
path(const Source& source, const locale& loc);

template <class InIt>
path(InIt first, InIt last);

template <class InIt>
path(InIt first, InIt last, const locale& loc);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Cesta, na kterou má být vytvořená cesta kopie.

*Zdrojová*\
Zdroj, jehož vytvořená cesta má být kopie.

*Loc*\
Zadané národní prostředí.

*první*\
Pozice prvního prvku, který chcete zkopírovat.

*posledního*\
Pozice posledního prvku, který má být zkopírován.

### <a name="remarks"></a>Poznámky

Všechny konstruktory jsou `myname` v různých způsobech:

Pro `path()` něj je `myname()`.

Pro `path(const path& right`) je `myname(right.myname)`.

Pro `path(path&& right)` něj je `myname(right.myname)`.

Pro `template<class Source> path(const Source& source)` něj je `myname(source)`.

K `template<class Source> path(const Source& source, const locale& loc)` tomu je `myname(source)`potřeba získat všechny potřebné omezující vlastnosti codecvt z `loc`.

Pro `template<class InIt> path(InIt first, InIt last)` něj je `myname(first, last)`.

K `template<class InIt> path(InIt first, InIt last, const locale& loc)` tomu je `myname(first, last)`potřeba získat všechny potřebné omezující vlastnosti codecvt z `loc`.

## <a name="preferred_separator"></a>cesta::p referred_separator

Objekt konstanty dává preferovanému znaku pro oddělení součástí cesty v závislosti na hostitelském operačním systému.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Poznámky

Všimněte si, že je ve Windows stejně přípustný i pro použití L '/' na svém místě.

## <a name="relative_path"></a>cesta:: RELATIVE_PATH

Vrátí součást relativní cesty pro `myname`.

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí komponentu relativní cesty pro `myname`, specifickou `myname` příponu po odebrání `root_path().native()` a všechny bezprostředně následné nadbytečné oddělovače adresářů. Komponenta může být prázdná.

## <a name="remove_filename"></a>cesta:: remove_filename

Odstraní název souboru.

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a>cesta:: replace_extension

Nahradí rozšíření `myname`.

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parametry

*newext*\
Nové rozšíření.

### <a name="remarks"></a>Poznámky

Nejprve odebere příponu `extension().native()` z `myname`. Pak pokud `!newext.empty() && newext[0] != dot` (kde `dot` je `*path(".").c_str()`), pak `dot` je připojen k `myname`. Pak *NewExt* je připojen k `myname`.

## <a name="replace_filename"></a>cesta:: replace_filename

Nahradí název souboru.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parametry

*pval*\
Cesta k názvu souboru.

### <a name="remarks"></a>Poznámky

Členská funkce se spustí:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a>cesta:: root_directory

Vrátí součást `myname`kořenového adresáře.

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Poznámky

Komponenta může být prázdná.

## <a name="root_name"></a>cesta:: root_name

Vrátí komponentu `myname`názvu kořenového adresáře.

```cpp
path root_name() const;
```

### <a name="remarks"></a>Poznámky

Komponenta může být prázdná.

## <a name="root_path"></a>cesta:: root_path

Vrátí součást kořenové cesty pro `myname`.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí komponentu `myname`kořenové cesty, konkrétně `root_name()`  / . `root_directory` Komponenta může být prázdná.

## <a name="stem"></a>cesta:: kmen

Vrátí komponentu prvku `myname`. `stem`

```cpp
path stem() const;
```

### <a name="remarks"></a>Poznámky

`stem` Vrátí komponentu`myname`, konkrétně`filename().native()`s jakýmkoliv koncovým odebráním.`extension().native()` Komponenta může být prázdná.

## <a name="string"></a>cesta:: řetězec

Převede sekvenci uloženou `mypath`v.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Poznámky

První členská funkce (Template) převede sekvenci uloženou `mypath` stejným způsobem jako:

1. `string()` pro `string<char, Traits, Alloc>()`

1. `wstring()` pro `string<wchar_t, Traits, Alloc>()`

1. `u16string()` pro `string<char16_t, Traits, Alloc>()`

1. `u32string()` pro `string<char32_t, Traits, Alloc>()`

Druhá členská funkce převede sekvenci uloženou `mypath` v na kódování, které upřednostňuje hostitelský systém pro sekvenci **znaků** a vrátí ji uloženou v objektu typu `string`.

## <a name="string_type"></a>cesta:: string_type

Typ je synonymum pro `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a>cesta:: swap

Provede `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a>cesta:: u16string

Převede sekvenci uloženou `mypath` v do UTF-16 a vrátí ji uloženou v objektu typu `u16string`.

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>cesta:: u32string

Převede sekvenci uloženou `mypath` v do UTF-32 a vrátí ji uloženou v objektu typu `u32string`.

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>cesta:: u8string

Převede sekvenci uloženou `mypath` v do UTF-8 a vrátí ji uloženou v objektu typu `u8string`.

```cpp
string u8string() const;
```

## <a name="value_type"></a>cesta:: value_type

Typ popisuje prvky, `path` které jsou na něj přizpůsobeny hostitelským operačním systémem.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a>cesta:: wstring

Převede sekvenci uloženou `mypath` v na kódování, které upřednostňuje hostitelský systém pro sekvenci **wchar_t** a vrátí ji uloženou v objektu typu `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
