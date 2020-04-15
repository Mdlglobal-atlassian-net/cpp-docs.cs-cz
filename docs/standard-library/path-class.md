---
title: path – třída
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 669dfd2c8cd8576ebfb6684bab7cf63cdd51babc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372111"
---
# <a name="path-class"></a>path – třída

Třída **cesta** ukládá objekt `string_type`typu `myname` , který je zde volán pro účely expozice, vhodný pro použití jako cesta. `string_type`je synonymem `basic_string<value_type>`pro `value_type` , kde je synonymem pro **wchar_t** v systému Windows nebo **char** na POSIX.

Další informace a příklady kódu naleznete v [tématu File System Navigation (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Syntaxe

```cpp
class path;
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Cestu](#path)|Vytvoří `path`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[const_iterator](#const_iterator)|Synonymum `iterator`pro .|
|[Iterace](#iterator)|Obousměrný konstantní iterátor, který označuje `path` součásti `myname`.|
|[string_type](#string_type)|Typ je synonymem `basic_string<value_type>`pro .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Připojit](#append)|Připojí zadanou sekvenci k `mypath`aplikaci , převedenou a vloženou preferred_separator podle potřeby.|
|[Přiřadit](#assign)|Nahradí `mypath` zadanou sekvenci, převedenou podle potřeby.|
|[Začít](#begin)|Vrátí `path::iterator` označení prvního prvku cesty v názvu cesty, pokud je k dispozici.|
|[c_str](#c_str)|Vrátí ukazatel na první `mypath`znak v souboru .|
|[Jasné](#clear)|Provede `mypath.clear()`.|
|[Porovnat](#compare)|Vrátí hodnoty porovnání.|
|[Concat](#compare)|Připojí zadanou sekvenci k `mypath`, převedené (ale ne vložení oddělovače) podle potřeby.|
|[empty](#empty)|Vrací objekt `mypath.empty()`.|
|[Konec](#end)|Vrátí iterátor typu na konci sekvence `iterator`.|
|[Rozšíření](#extension)|Vrátí příponu `filename()`.|
|[Název_souboru](#filename)|Vrátí součást kořenového adresáře `empty() path() : *--end()`myname, konkrétně . Součást může být prázdná.|
|[generic_string](#generic_string)|Vrátí `this->string<Elem, Traits, Alloc>(al)` s (v rámci systému Windows) všechna zpětná lomítka převedena na lomítko.|
|[generic_u16string](#generic_u16string)|Vrátí `u16string()` s (v rámci systému Windows) všechna zpětná lomítka převedena na lomítko.|
|[generic_u32string](#generic_u32string)|Vrátí `u32string()` s (v rámci systému Windows) všechna zpětná lomítka převedena na lomítko.|
|[generic_u8string](#generic_u8string)|Vrátí `u8string()` s (v rámci systému Windows) všechna zpětná lomítka převedena na lomítko.|
|[generic_wstring](#generic_wstring)|Vrátí `wstring()` s (v rámci systému Windows) všechna zpětná lomítka převedena na lomítko.|
|[has_extension](#has_extension)|Vrací objekt `!extension().empty()`.|
|[has_filename](#has_filename)|Vrací objekt `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Vrací objekt `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Vrací objekt `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Vrací objekt `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Vrací objekt `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Vrací objekt `!root_path().empty()`.|
|[has_stem](#has_stem)|Vrací objekt `!stem().empty()`.|
|[is_absolute](#is_absolute)|V systému Windows `has_root_name() && has_root_directory()`vrátí funkce . Pro POSIX funkce `has_root_directory()`vrátí .|
|[is_relative](#is_relative)|Vrací objekt `!is_absolute()`.|
|[make_preferred](#make_preferred)|Podle potřeby převede každý oddělovač na preferred_separator.|
|[Nativní](#native)|Vrací objekt `myname`.|
|[parent_path](#parent_path)|Vrátí nadřazenou součást cesty aplikace `myname`.|
|[preferred_separator](#preferred_separator)|Konstantní objekt poskytuje upřednostňovaný znak pro oddělení součástí cesty v závislosti na hostitelském operačním systému. |
|[relative_path](#relative_path)|Vrátí relativní součást `myname`cesty aplikace . |
|[remove_filename](#remove_filename)|Odebere název souboru.|
|[replace_extension](#replace_extension)|Nahradí rozšíření . `myname` |
|[replace_filename](#replace_filename)|RNahradí název souboru.|
|[root_directory](#root_directory)|Vrátí součást kořenového `myname`adresáře aplikace . |
|[root_name](#root_name)|Vrátí součást kořenového `myname`názvu souboru . |
|[root_path](#root_path)|Vrátí součást kořenové `myname`cesty aplikace .|
|[Kmenových](#stem)|Vrátí `stem` součást `myname`souboru .|
|[Řetězec](#string)|Převede sekvenci uloženou v aplikaci `mypath`.|
|[Swap](#swap)|Provede `swap(mypath, right.mypath)`.|
|[u16řetězec](#u16string)|Převede sekvenci uloženou na `mypath` UTF-16 a `u16string`vrátí ji uloženou v objektu typu .|
|[u32řetězec](#u32string)|Převede sekvenci uloženou na `mypath` UTF-32 a `u32string`vrátí ji uloženou v objektu typu .|
|[u8řetězec](#u8string)|Převede sekvenci uloženou na `mypath` UTF-8 a `u8string`vrátí ji uloženou v objektu typu .|
|[value_type](#value_type)|Typ popisuje prvky cesty upřednostňované hostitelským operačním systémem.|
|[wstring](#wstring)|Převede sekvenci uloženou v `mypath` kódování upřednostňovaném `wchar_t` hostitelským systémem pro sekvenci a vrátí ji uloženou v objektu typu `wstring`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_as)|Nahradí prvky cesty kopií jiné cesty.|
|[operátor+=](#op_add)|Různé `concat` výrazy.|
|[operátor/=](#op_divide)|Různé `append` výrazy.|
|[operátor string_type](#op_string)|Vrací objekt `myname`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> souborového systému

**Obor názvů:** std::experimental::filesystem

## <a name="pathappend"></a><a name="append"></a>cesta::připojit

Připojí zadanou sekvenci k `mypath`, `preferred_separator` převedena a vložení podle potřeby.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Zdroj*\
Zadaná sekvence.

*První*\
Začátek zadané sekvence.

*Poslední*\
Konec zadané sekvence.

## <a name="pathassign"></a><a name="assign"></a>cesta::přiřadit

Nahradí `mypath` zadanou sekvenci, převedenou podle potřeby.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Zdroj*\
Zadaná sekvence.

*První*\
Začátek zadané sekvence.

*Poslední*\
Konec zadané sekvence.

## <a name="pathbegin"></a><a name="begin"></a>cesta::begin

Vrátí `path::iterator` označení prvního prvku cesty v názvu cesty, pokud je k dispozici.

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a>cesta::c_str

Vrátí ukazatel na první `mypath`znak v souboru .

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a>cesta::vymazat

Provede `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a>cesta::porovnat

První funkce `mypath.compare(pval.native())`vrátí . Druhá funkce `mypath.compare(str)`vrátí . Třetí funkce `mypath.compare(ptr)`vrátí .

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*pval*\
Cesta k porovnání.

*Str*\
Řetězec porovnat.

*Ptr*\
Ukazatel k porovnání.

## <a name="pathconcat"></a><a name="concat"></a>cesta::concat

Připojí zadanou sekvenci k `mypath`, převedené (ale ne vložení oddělovače) podle potřeby.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Zdroj*\
Zadaná sekvence.

*První*\
Začátek zadané sekvence.

*Poslední*\
Konec zadané sekvence.

## <a name="pathconst_iterator"></a><a name="const_iterator"></a>cesta::const_iterator

Synonymum `iterator`pro .

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a>cesta::prázdné

Vrací objekt `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a>cesta::konec

Vrátí iterátor typu na konci sekvence `iterator`.

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a>cesta::rozšíření

Vrátí příponu `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Poznámky

Vrátí příponu `filename() X` takové, že:

Pokud `X == path(".") || X == path("..")` nebo `X` pokud neobsahuje žádnou tečku, přípona je prázdná.

V opačném případě přípona začíná (a zahrnuje) tečku nejvíce vpravo.

## <a name="pathfilename"></a><a name="filename"></a>cesta::název souboru

Vrátí součást kořenového adresáře `empty() path() : *--end()`myname, konkrétně . Součást může být prázdná.

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a>cesta::generic_string

Vrátí `this->string<Elem, Traits, Alloc>(al)` s (v rámci systému Windows) všechna zpětná lomítka převedena na lomítko.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a>cesta::generic_u16string

Vrátí `u16string()` s (v rámci systému Windows) všechna zpětná lomítka převedena na lomítko.

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a>cesta::generic_u32string

Vrátí `u32string()` s (v rámci systému Windows) všechna zpětná lomítka převedena na lomítko.

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a>cesta::generic_u8string

Vrátí `u8string()` s (v rámci systému Windows) všechna zpětná lomítka převedena na lomítko.

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a>cesta::generic_wstring

Vrátí `wstring()` s (v rámci systému Windows) všechna zpětná lomítka převedena na lomítko.

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a>cesta::has_extension

Vrací objekt `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a>cesta::has_filename

Vrací objekt `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a>cesta::has_parent_path

Vrací objekt `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a>cesta::has_relative_path

Vrací objekt `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a>cesta::has_root_directory

Vrací objekt `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a>cesta::has_root_name

Vrací objekt `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a>cesta::has_root_path

Vrací objekt `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a>cesta::has_stem

Vrací objekt `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a>cesta::is_absolute

V systému Windows `has_root_name() && has_root_directory()`vrátí funkce . Pro POSIX funkce `has_root_directory()`vrátí .

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a>cesta::is_relative

Vrací objekt `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a>cesta::iterator

Obousměrný konstantní iterátor, který označuje součásti `myname`cesty .

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

Třída popisuje obousměrný konstantní iterátor, který označuje `path` součásti `myname` v pořadí:

1. kořenový název, je-li k dispozici

1. kořenový adresář, pokud je k dispozici

1. zbývající prvky adresáře `path`nadřazeného objektu , pokud jsou přítomny, končící názvem souboru, pokud jsou k dispozici

Pro `pval` objekt typu `path`:

1. `path::iterator X = pval.begin()`označuje první `path` prvek v pathname, pokud je k dispozici.

1. `X == pval.end()`true, `X` když body těsně za koncem sekvence komponent.

1. `*X`vrátí řetězec, který odpovídá aktuální součásti.

1. `++X`označuje další součást v pořadí, pokud je k dispozici.

1. `--X`označuje předchozí součást v pořadí, pokud je k dispozici.

1. Změna `myname` zneplatní všechny iterátory označující `myname`prvky v .

## <a name="pathmake_preferred"></a><a name="make_preferred"></a>cesta::make_preferred

Převede každý oddělovač podle `preferred_separator` potřeby.

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a>cesta::nativní

Vrací objekt `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a>cesta::operátor=

Nahradí prvky cesty kopií jiné cesty.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parametry

*Právo*\
[Cesta](../standard-library/path-class.md) kopírovaná do `path`.

*Zdroj*\
Zdrojová cesta.

### <a name="remarks"></a>Poznámky

První operátor člena `right.myname` `myname`zkopíruje do . Druhý operátor člena `right.myname` `myname`přesune do . Třetí operátor člena se chová `*this = path(source)`stejně jako .

## <a name="pathoperator"></a><a name="op_add"></a>cesta::operátor+=

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

*Právo*\
Přidaná cesta.

*Str*\
Přidaný řetězec.

*Ptr*\
Přidané ukazatel.

*Elem*\
Přidané `value_type` nebo `Elem`.

*Zdroj*\
Přidaný zdroj.

### <a name="remarks"></a>Poznámky

Členské funkce se chovají stejně jako následující odpovídající výrazy:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="pathoperator"></a><a name="op_divide"></a>cesta::operátor/=

Různé `append` výrazy.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parametry

*Právo*\
Přidaná cesta.

*Zdroj*\
Přidaný zdroj.

### <a name="remarks"></a>Poznámky

Členské funkce se chovají stejně jako následující odpovídající výrazy:

1. `append(right);`

1. `append(source);`

## <a name="pathoperator-string_type"></a><a name="op_string"></a>cesta::operátor string_type

Vrací objekt `myname`.

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a>cesta::parent_path

Vrátí nadřazenou součást cesty aplikace `myname`.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí nadřazenou součást cesty `myname` `myname` aplikace `filename().native()` , konkrétně předponu po odebrání a všechny bezprostředně předcházející oddělovače adresářů. (Stejně `begin() != end()`tak, pokud , je to kombinace `[begin(), --end())` všech prvků `operator/=`v rozsahu postupným použitím .) Součást může být prázdná.

## <a name="pathpath"></a><a name="path"></a>cesta::path

Konstrukce `path` různými způsoby.

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

*Právo*\
Cesta, která je postavená cesta má být kopie.

*Zdroj*\
Zdroj, jehož je vytvořená cesta kopie.

*Loc*\
Zadané národní prostředí.

*První*\
Pozice prvního prvku, který chcete zkopírovat.

*Poslední*\
Pozice posledního prvku, který má být zkopírován.

### <a name="remarks"></a>Poznámky

Konstruktory všechny `myname` konstrukce různými způsoby:

Pro `path()` to `myname()`je .

Pro `path(const path& right`) `myname(right.myname)`to je .

Pro `path(path&& right)` to `myname(right.myname)`je .

Pro `template<class Source> path(const Source& source)` to `myname(source)`je .

Pro `template<class Source> path(const Source& source, const locale& loc)` to `myname(source)`je , získání všech potřebných `loc`kodekt fazety z .

Pro `template<class InIt> path(InIt first, InIt last)` to `myname(first, last)`je .

Pro `template<class InIt> path(InIt first, InIt last, const locale& loc)` to `myname(first, last)`je , získání všech potřebných `loc`kodekt fazety z .

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a>cesta::preferred_separator

Konstantní objekt poskytuje upřednostňovaný znak pro oddělení součástí cesty v závislosti na hostitelském operačním systému.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Poznámky

Všimněte si, že je stejně přípustné ve většině kontextů v rámci systému Windows používat L'/' na jeho místo.

## <a name="pathrelative_path"></a><a name="relative_path"></a>cesta::relative_path

Vrátí relativní součást `myname`cesty aplikace .

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí relativní součást `myname`cesty aplikace , konkrétně `myname` příponu po odebrání `root_path().native()` a všechny bezprostředně následné redundantní oddělovače adresářů. Součást může být prázdná.

## <a name="pathremove_filename"></a><a name="remove_filename"></a>cesta::remove_filename

Odebere název souboru.

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a>cesta::replace_extension

Nahradí rozšíření . `myname`

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parametry

*newext*\
Nové rozšíření.

### <a name="remarks"></a>Poznámky

Nejprve odebere příponu `extension().native()` z `myname`. Pak `!newext.empty() && newext[0] != dot` pokud `dot` (kde `*path(".").c_str()` `dot` je), pak `myname`je připojen k . Potom *newext* je `myname`připojen k .

## <a name="pathreplace_filename"></a><a name="replace_filename"></a>cesta::replace_filename

Nahradí název souboru.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parametry

*pval*\
Cesta názvu souboru.

### <a name="remarks"></a>Poznámky

Členská funkce se provádí:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathroot_directory"></a><a name="root_directory"></a>cesta::root_directory

Vrátí součást kořenového `myname`adresáře aplikace .

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Poznámky

Součást může být prázdná.

## <a name="pathroot_name"></a><a name="root_name"></a>cesta::root_name

Vrátí součást kořenového `myname`názvu souboru .

```cpp
path root_name() const;
```

### <a name="remarks"></a>Poznámky

Součást může být prázdná.

## <a name="pathroot_path"></a><a name="root_path"></a>cesta::root_path

Vrátí součást kořenové `myname`cesty aplikace .

```cpp
path root_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí součást kořenové `myname`cesty `root_name()`  /  `root_directory`aplikace , specifically . Součást může být prázdná.

## <a name="pathstem"></a><a name="stem"></a>cesta::stopka

Vrátí `stem` součást `myname`souboru .

```cpp
path stem() const;
```

### <a name="remarks"></a>Poznámky

Vrátí `stem` součást `myname`aplikace `filename().native()` , konkrétně `extension().native()` s odebráním všech koncovek. Součást může být prázdná.

## <a name="pathstring"></a><a name="string"></a>cesta::řetězec

Převede sekvenci uloženou v aplikaci `mypath`.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Poznámky

První členská funkce (šablona) převede uloženou `mypath` sekvenci stejným způsobem jako:

1. `string()`Pro`string<char, Traits, Alloc>()`

1. `wstring()`Pro`string<wchar_t, Traits, Alloc>()`

1. `u16string()`Pro`string<char16_t, Traits, Alloc>()`

1. `u32string()`Pro`string<char32_t, Traits, Alloc>()`

Druhá členská funkce převede `mypath` sekvenci uloženou v kódování upřednostňovaném hostitelským systémem pro sekvenci **znaků** a vrátí ji uloženou v objektu typu `string`.

## <a name="pathstring_type"></a><a name="string_type"></a>cesta::string_type

Typ je synonymem `basic_string<value_type>`pro .

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a>cesta::swap

Provede `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a>cesta::u16string

Převede sekvenci uloženou na `mypath` UTF-16 a `u16string`vrátí ji uloženou v objektu typu .

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a>cesta::u32string

Převede sekvenci uloženou na `mypath` UTF-32 a `u32string`vrátí ji uloženou v objektu typu .

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a>cesta::u8string

Převede sekvenci uloženou na `mypath` UTF-8 a `u8string`vrátí ji uloženou v objektu typu .

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a>cesta::value_type

Typ popisuje prvky `path` upřednostňované hostitelským operačním systémem.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a>cesta::wstring

Převede sekvenci uloženou v `mypath` kódování upřednostňovaném hostitelským systémem pro **wchar_t** sekvenci a vrátí ji uloženou v objektu typu `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)
