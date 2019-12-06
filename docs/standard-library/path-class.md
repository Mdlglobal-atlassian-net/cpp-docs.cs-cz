---
title: path – třída
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 0bc26bb04464c52ed08d46e6a12c12cae6909d6f
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898797"
---
# <a name="path-class"></a>path – třída

Třída **path** ukládá objekt typu `string_type`, který se označuje `myname` tady pro účely Exposition, vhodný pro použití jako cesta. `string_type` je synonymum pro `basic_string<value_type>`, kde `value_type` je synonymum pro **wchar_t** ve Windows nebo **char** v POSIX.

Další informace a příklady kódu naleznete v tématu [Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class path;
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Cesta](#path)|Vytvoří `path`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[const_iterator](#const_iterator)|Synonymum pro `iterator`.|
|[iterator](#iterator)|Obousměrný konstantní iterátor, který určuje `path` komponenty `myname`.|
|[string_type](#string_type)|Typ je synonymum pro `basic_string<value_type>`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[příloh](#append)|Připojí určenou sekvenci k `mypath`, převedená a vkládání preferred_separator podle potřeby.|
|[assign](#assign)|Nahradí `mypath` zadaným pořadím, které se převedou podle potřeby.|
|[ifunctiondiscovery](#begin)|Vrátí `path::iterator` určující první prvek cesty v cestě, pokud je k dispozici.|
|[c_str](#c_str)|Vrátí ukazatel na první znak v `mypath`.|
|[jejich](#clear)|Provede `mypath.clear()`.|
|[compare](#compare)|Vrátí hodnoty porovnání.|
|[concat](#compare)|Připojí určenou sekvenci k `mypath`, převeden (ale nevloží oddělovač) podle potřeby.|
|[empty](#empty)|Vrací objekt `mypath.empty()`.|
|[účelu](#end)|Vrátí iterátor koncové sekvence typu `iterator`.|
|[klapk](#extension)|Vrátí příponu `filename()`.|
|[filename](#filename)|Vrátí komponentu kořenového adresáře jmenující, konkrétně `empty() path() : *--end()`. Komponenta může být prázdná.|
|[generic_string](#generic_string)|Vrátí `this->string<Elem, Traits, Alloc>(al)` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.|
|[generic_u16string](#generic_u16string)|Vrátí `u16string()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.|
|[generic_u32string](#generic_u32string)|Vrátí `u32string()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.|
|[generic_u8string](#generic_u8string)|Vrátí `u8string()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.|
|[generic_wstring](#generic_wstring)|Vrátí `wstring()` s (pod Windows) jakékoli zpětné lomítko převedené na lomítko.|
|[has_extension](#has_extension)|Vrací objekt `!extension().empty()`.|
|[has_filename](#has_filename)|Vrací objekt `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Vrací objekt `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Vrací objekt `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Vrací objekt `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Vrací objekt `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Vrací objekt `!root_path().empty()`.|
|[has_stem](#has_stem)|Vrací objekt `!stem().empty()`.|
|[is_absolute](#is_absolute)|V případě systému Windows vrátí funkce `has_root_name() && has_root_directory()`. U POSIX funkce vrátí `has_root_directory()`.|
|[is_relative](#is_relative)|Vrací objekt `!is_absolute()`.|
|[make_preferred](#make_preferred)|V případě potřeby převede každý oddělovač na preferred_separator.|
|[nativní](#native)|Vrací objekt `myname`.|
|[parent_path](#parent_path)|Vrátí komponentu nadřazené cesty `myname`.|
|[preferred_separator](#preferred_separator)|Objekt konstanty dává preferovanému znaku pro oddělení součástí cesty v závislosti na hostitelském operačním systému. |
|[relative_path](#relative_path)|Vrátí součást relativní cesty `myname`. |
|[remove_filename](#remove_filename)|Odstraní název souboru.|
|[replace_extension](#replace_extension)|Nahradí rozšíření `myname`. |
|[replace_filename](#replace_filename)|RReplaces název souboru.|
|[root_directory](#root_directory)|Vrátí součást kořenového adresáře `myname`. |
|[root_name](#root_name)|Vrátí komponentu názvu kořenového adresáře `myname`. |
|[root_path](#root_path)|Vrátí součást kořenové cesty `myname`.|
|[stonek](#stem)|Vrátí součást `stem` `myname`.|
|[string](#string)|Převede sekvenci uloženou v `mypath`.|
|[swap](#swap)|Provede `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Převede sekvenci uloženou v `mypath` na UTF-16 a vrátí ji uloženou v objektu typu `u16string`.|
|[u32string](#u32string)|Převede sekvenci uloženou v `mypath` na UTF-32 a vrátí ji uloženou v objektu typu `u32string`.|
|[u8string](#u8string)|Převede sekvenci uloženou v `mypath` na UTF-8 a vrátí ji uloženou v objektu typu `u8string`.|
|[value_type](#value_type)|Typ popisuje prvky cesty, které jsou na něj přizpůsobeny hostitelským operačním systémem.|
|[wstring](#wstring)|Převede sekvenci uloženou v `mypath` na kódování, které upřednostňuje hostitelský systém pro `wchar_t` sekvenci a vrátí ji uloženou v objektu typu `wstring`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_as)|Nahradí prvky cesty kopií jiné cesty.|
|[operator+=](#op_add)|Různé výrazy `concat`.|
|[operator/= – operátor](#op_divide)|Různé výrazy `append`.|
|[operátor string_type](#op_string)|Vrací objekt `myname`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<systém souborů >

**Obor názvů:** std:: experimentální:: FileSystem

## <a name="append"></a>cesta:: Append

Připojí určenou sekvenci k `mypath`, převedená a vkládání `preferred_separator` podle potřeby.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

\ *zdroje*
Zadaná sekvence

*první*\
Začátek zadaného pořadí.

*poslední*\
Konec zadaného pořadí.

## <a name="assign"></a>cesta:: přiřadit

Nahradí `mypath` zadaným pořadím, které se převedou podle potřeby.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

\ *zdroje*
Zadaná sekvence

*první*\
Začátek zadaného pořadí.

*poslední*\
Konec zadaného pořadí.

## <a name="begin"></a>cesta:: begin

Vrátí `path::iterator` určující první prvek cesty v cestě, pokud je k dispozici.

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

\ *str*
Řetězec, který se má porovnat

\ *PTR*
Ukazatel na porovnání

## <a name="concat"></a>cesta:: Concat

Připojí určenou sekvenci k `mypath`, převeden (ale nevloží oddělovač) podle potřeby.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

\ *zdroje*
Zadaná sekvence

*první*\
Začátek zadaného pořadí.

*poslední*\
Konec zadaného pořadí.

## <a name="const_iterator"></a>cesta:: const_iterator

Synonymum pro `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>cesta:: Empty

Vrací objekt `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="end"></a>cesta:: end

Vrátí iterátor koncové sekvence typu `iterator`.

```cpp
iterator end() const;
```

## <a name="extension"></a>cesta:: rozšíření

Vrátí příponu `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Poznámky

Vrací příponu `filename() X` takto:

Pokud `X == path(".") || X == path("..")` nebo pokud `X` neobsahuje tečku, přípona je prázdná.

V opačném případě přípona začíná (a obsahuje) tečku vpravo.

## <a name="filename"></a>cesta:: filename

Vrátí komponentu kořenového adresáře jmenující, konkrétně `empty() path() : *--end()`. Komponenta může být prázdná.

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

Vrací objekt `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a>cesta:: has_filename

Vrací objekt `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a>cesta:: has_parent_path

Vrací objekt `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a>cesta:: has_relative_path

Vrací objekt `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a>cesta:: has_root_directory

Vrací objekt `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>cesta:: has_root_name

Vrací objekt `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a>cesta:: has_root_path

Vrací objekt `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>cesta:: has_stem

Vrací objekt `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>cesta:: is_absolute

V případě systému Windows vrátí funkce `has_root_name() && has_root_directory()`. U POSIX funkce vrátí `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>cesta:: is_relative

Vrací objekt `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>cesta:: iterátor

Obousměrný konstantní iterátor, který určuje součásti cesty `myname`.

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

Třída popisuje obousměrný konstantní iterátor, který určuje `path` komponenty `myname` v sekvenci:

1. název kořenového adresáře, pokud je k dispozici

1. kořenový adresář, pokud je k dispozici

1. zbývající prvky adresáře nadřazeného `path`, pokud jsou k dispozici, končící názvem souboru, pokud je k dispozici

Pro `pval` objekt typu `path`:

1. `path::iterator X = pval.begin()` určuje první prvek `path` v cestě, pokud je k dispozici.

1. `X == pval.end()` má hodnotu true, pokud `X` body hned za koncem sekvence komponent.

3. `*X` vrátí řetězec, který odpovídá aktuální komponentě.

1. `++X` určí další komponentu v sekvenci, pokud je k dispozici.

1. `--X` určí předchozí komponentu v sekvenci, pokud je k dispozici.

1. Změna `myname` zruší platnost všech iterátorů, jejichž výsledkem je určení prvků v `myname`.

## <a name="make_preferred"></a>cesta:: make_preferred

V případě potřeby převede každý oddělovač na `preferred_separator`.

```cpp
path& make_preferred();
```

## <a name="native"></a>cesta:: nativní

Vrací objekt `myname`.

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

*pravé*\
[Cesta](../standard-library/path-class.md) , která se kopíruje do `path`.

\ *zdroje*
Zdrojová cesta

### <a name="remarks"></a>Poznámky

První operátor členu kopíruje `right.myname` do `myname`. Druhý operátor členu přesune `right.myname` k `myname`. Třetí členský operátor se chová stejně jako `*this = path(source)`.

## <a name="op_add"></a>Path:: operator + =

Různé výrazy `concat`.

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

*pravé*\
Přidaná cesta

\ *str*
Přidaný řetězec.

\ *PTR*
Přidaný ukazatel.

*elem*\
Přidaná `value_type` nebo `Elem`.

\ *zdroje*
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

Různé výrazy `append`.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parametry

*pravé*\
Přidaná cesta

\ *zdroje*
Přidaný zdroj.

### <a name="remarks"></a>Poznámky

Členské funkce se chovají stejně jako následující odpovídající výrazy:

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a>Path:: operator string_type

Vrací objekt `myname`.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a>cesta::p arent_path

Vrátí komponentu nadřazené cesty `myname`.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí komponentu nadřazené cesty `myname`, konkrétně prefix `myname` po odebrání `filename().native()` a všech bezprostředně předchozích oddělovačů adresářů. (Stejně, pokud `begin() != end()`, jedná se o kombinaci všech prvků v rozsahu `[begin(), --end())` po úspěšném použití `operator/=`.) Komponenta může být prázdná.

## <a name="path"></a>cesta::p ATH

Sestaví `path` různými způsoby.

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

*pravé*\
Cesta, na kterou má být vytvořená cesta kopie.

\ *zdroje*
Zdroj, jehož vytvořená cesta má být kopie.

\ *Loc*
Zadané národní prostředí.

*první*\
Pozice prvního prvku, který chcete zkopírovat.

*poslední*\
Pozice posledního prvku, který má být zkopírován.

### <a name="remarks"></a>Poznámky

Konstruktory všechny konstrukce `myname` různými způsoby:

Pro `path()` je `myname()`.

Pro `path(const path& right`) je `myname(right.myname)`.

Pro `path(path&& right)` je `myname(right.myname)`.

Pro `template<class Source> path(const Source& source)` je `myname(source)`.

Pro `template<class Source> path(const Source& source, const locale& loc)` je `myname(source)`, získá všechny potřebné omezující vlastnosti codecvt z `loc`.

Pro `template<class InIt> path(InIt first, InIt last)` je `myname(first, last)`.

Pro `template<class InIt> path(InIt first, InIt last, const locale& loc)` je `myname(first, last)`, získá všechny potřebné omezující vlastnosti codecvt z `loc`.

## <a name="preferred_separator"></a>cesta::p referred_separator

Objekt konstanty dává preferovanému znaku pro oddělení součástí cesty v závislosti na hostitelském operačním systému.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Poznámky

Všimněte si, že je ve Windows stejně přípustný i pro použití L '/' na svém místě.

## <a name="relative_path"></a>cesta:: relative_path

Vrátí součást relativní cesty `myname`.

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí součást relativní cesty `myname`, konkrétně příponu `myname` po odebrání `root_path().native()` a všechny bezprostředně následné redundantní oddělovače adresářů. Komponenta může být prázdná.

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

Nejprve odebere příponu `extension().native()` z `myname`. Až se pak `!newext.empty() && newext[0] != dot` (kde `dot` je `*path(".").c_str()`), `dot` se připojí k `myname`. Pak se k `myname`připojí *NewExt* .

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

Vrátí součást kořenového adresáře `myname`.

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Poznámky

Komponenta může být prázdná.

## <a name="root_name"></a>cesta:: root_name

Vrátí komponentu názvu kořenového adresáře `myname`.

```cpp
path root_name() const;
```

### <a name="remarks"></a>Poznámky

Komponenta může být prázdná.

## <a name="root_path"></a>cesta:: root_path

Vrátí součást kořenové cesty `myname`.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí součást kořenové cesty `myname`, konkrétně `root_name()` / `root_directory`. Komponenta může být prázdná.

## <a name="stem"></a>cesta:: kmen

Vrátí součást `stem` `myname`.

```cpp
path stem() const;
```

### <a name="remarks"></a>Poznámky

Vrátí součást `stem` `myname`, konkrétně `filename().native()` všechny ukončovací `extension().native()` odebrány. Komponenta může být prázdná.

## <a name="string"></a>cesta:: řetězec

Převede sekvenci uloženou v `mypath`.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Poznámky

První členská funkce (Template) převede sekvenci uloženou v `mypath` stejným způsobem jako:

1. `string()` pro `string<char, Traits, Alloc>()`

1. `wstring()` pro `string<wchar_t, Traits, Alloc>()`

1. `u16string()` pro `string<char16_t, Traits, Alloc>()`

1. `u32string()` pro `string<char32_t, Traits, Alloc>()`

Druhá členská funkce převede sekvenci uloženou v `mypath` na kódování, které upřednostňuje hostitelský systém pro sekvenci **znaků** a vrátí ji uloženou v objektu typu `string`.

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

Převede sekvenci uloženou v `mypath` na UTF-16 a vrátí ji uloženou v objektu typu `u16string`.

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>cesta:: u32string

Převede sekvenci uloženou v `mypath` na UTF-32 a vrátí ji uloženou v objektu typu `u32string`.

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>cesta:: u8string

Převede sekvenci uloženou v `mypath` na UTF-8 a vrátí ji uloženou v objektu typu `u8string`.

```cpp
string u8string() const;
```

## <a name="value_type"></a>cesta:: value_type

Typ popisuje prvky `path`, na které přidává hostitelský operační systém.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a>cesta:: wstring

Převede sekvenci uloženou v `mypath` na kódování, které upřednostňuje hostitelský systém pro **wchar_t** sekvenci a vrátí ji uloženou v objektu typu `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
