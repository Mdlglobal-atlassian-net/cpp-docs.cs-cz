---
title: Path – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::path
dev_langs:
- C++
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4559bec84d7e6051155ad73f68a1ef8ae13ca6cc
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104157"
---
# <a name="path-class"></a>path – třída

**Cesta** třída uchovává objekt typu String\_typ názvem Jmeno zde pro účely budeme vhodný pro použití jako cestu. řetězec\_typ je synonymum pro základní\_řetězec\<value_type >, kde hodnota\_typ je synonymum pro znaky v části Windows nebo wchar_t v rámci specifikace Posix.

Další informace a příklady kódu naleznete v tématu [navigace systému souborů (C++)](../standard-library/file-system-navigation.md).

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
|[iterátor](#iterator)|Obousměrný konstantní iterátor, který určuje `path` součástí `myname`.|
|[STRING_TYPE](#string_type)|Typ je synonymum pro `basic_string<value_type>`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Připojení](#append)|Připojí k zadané pořadí `mypath`, převést a vkládání preferred_separator podle potřeby.|
|[přiřazení](#assign)|Nahradí `mypath` s zadané pořadí převede podle potřeby.|
|[začít](#begin)|Vrátí `path::iterator` označující první element path v názvu cesty, pokud jsou k dispozici.|
|[c_str](#c_str)|Vrací ukazatel na první znak v `mypath`.|
|[Vymazat](#clear)|Spustí `mypath.clear()`.|
|[compare](#compare)|Vrátí hodnoty porovnání.|
|[concat](#compare)|Připojí k zadané pořadí `mypath`, převést (ale ne vkládání oddělovač) podle potřeby.|
|[prázdný](#empty)|Vrátí `mypath.empty()`.|
|[ukončení](#end)|Vrátí iterátor koncová sekvence typu `iterator`.|
|[Rozšíření](#extension)|Vrátí přípona `filename()`.|
|[Název souboru](#filename)|Vrátí komponentu kořenové adresáře Jmeno, konkrétně `empty() path() : *--end()`. Komponenta může být prázdný.|
|[generic_string –](#generic_string)|Vrátí `this->string<Elem, Traits, Alloc>(al)` s (v části Windows) převést všechny zpětné lomítko na dopředné lomítko.|
|[generic_u16string](#generic_u16string)|Vrátí `u16string()` s (v části Windows) převést všechny zpětné lomítko na dopředné lomítko.|
|[generic_u32string](#generic_u32string)|Vrátí `u32string()` s (v části Windows) převést všechny zpětné lomítko na dopředné lomítko.|
|[generic_u8string](#generic_u8string)|Vrátí `u8string()` s (v části Windows) převést všechny zpětné lomítko na dopředné lomítko.|
|[generic_wstring](#generic_wstring)|Vrátí `wstring()` s (v části Windows) převést všechny zpětné lomítko na dopředné lomítko.|
|[has_extension](#has_extension)|Vrátí `!extension().empty()`.|
|[has_filename](#has_filename)|Vrátí `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Vrátí `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Vrátí `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Vrátí `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Vrátí `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Vrátí `!root_path().empty()`.|
|[has_stem](#has_stem)|Vrátí `!stem().empty()`.|
|[is_absolute](#is_absolute)|Pro Windows, funkce vrátí `has_root_name() && has_root_directory()`. Pro specifikace Posix, funkce vrátí `has_root_directory()`.|
|[is_relative](#is_relative)|Vrátí `!is_absolute()`.|
|[make_preferred](#make_preferred)|Převede každý oddělovače preferred_separator podle potřeby.|
|[Nativní](#native)|Vrátí `myname`.|
|[parent_path](#parent_path)|Vrátí nadřazenou součást cesty `myname`.|
|[preferred_separator](#preferred_separator)|Objekt konstanty poskytuje upřednostňované znak pro oddělení součásti cesty, v závislosti na operačním systému hostitele. |
|[RELATIVE_PATH](#relative_path)|Vrátí komponentu relativní cesta `myname`. |
|[remove_filename –](#remove_filename)|Odebere název souboru.|
|[replace_extension –](#replace_extension)|Nahrazuje rozšíření `myname`. |
|[replace_filename](#replace_filename)|RReplaces název souboru.|
|[root_directory](#root_directory)|Vrátí komponentu kořenové adresáře `myname`. |
|[root_name](#root_name)|Vrátí komponentu názvu kořenového `myname`. |
|[root_path](#root_path)|Vrátí komponentu kořenové cesty `myname`.|
|[stem](#stem)|Vrátí `stem` komponentu `myname`.|
|[string](#string)|Převede sekvenci uložené v `mypath`.|
|[Prohození](#swap)|Spustí `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Převede sekvenci uložené v `mypath` UTF-16 a vrátí je uložená v objektu typu `u16string`.|
|[u32string](#u32string)|Převede sekvenci uložené v `mypath` UTF-32 a vrátí je uložená v objektu typu `u32string`.|
|[u8string](#u8string)|Převede sekvenci uložené v `mypath` UTF-8 a vrátí je uložená v objektu typu `u8string`.|
|[value_type](#value_type)|Typ, který popisuje prvků cesty podporuje operačním systémem hostitele.|
|[wstring](#wstring)|Převede sekvenci uložené v `mypath` kódování podporuje pro systém hostitele `wchar_t` pořadí a vrátí je uložená v objektu typu `wstring`.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_as)|Nahradí prvky cesta kopie jinou cestu.|
|[operator+=](#op_add)|Různé `concat` výrazy.|
|[/ = – operátor](#op_divide)|Různé `append` výrazy.|
|[string_type – operátor](#op_string)|Vrátí `myname`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="append"></a> path::append –

Připojí k zadané pořadí `mypath`převedený a vkládání `preferred_separator` podle potřeby.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Zdroj*<br/>
Zadané pořadí.

*první*<br/>
Začátek zadaného pořadí.

*poslední*<br/>
Konec zadaného pořadí.

## <a name="assign"></a> path::Assign –

Nahradí `mypath` s zadané pořadí převede podle potřeby.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Zdroj*<br/>
Zadané pořadí.

*první*<br/>
Začátek zadaného pořadí.

*poslední*<br/>
Konec zadaného pořadí.

## <a name="begin"></a> path::begin –

Vrátí `path::iterator` označující první element path v názvu cesty, pokud jsou k dispozici.

```cpp
iterator begin() const;
```

## <a name="c_str"></a> path::c_str

Vrací ukazatel na první znak v `mypath`.

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a> path::clear –

Spustí `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="compare"></a> path::Compare –

První funkce vrací `mypath.compare(pval.native())`. Druhá funkce vrátí `mypath.compare(str)`. Třetí funkce vrátí `mypath.compare(ptr)`.

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Cesta k porovnání.

*str*<br/>
Řetězec určený k porovnání.

*ptr*<br/>
Ukazatel k porovnání.

## <a name="concat"></a> path::concat –

Připojí k zadané pořadí `mypath`, převést (ale ne vkládání oddělovač) podle potřeby.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parametry

*Zdroj*<br/>
Zadané pořadí.

*první*<br/>
Začátek zadaného pořadí.

*poslední*<br/>
Konec zadaného pořadí.

## <a name="const_iterator"></a> path::const_iterator

Synonymum pro `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a> path::Empty –

Vrátí `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="end"></a> path::end –

Vrátí iterátor koncová sekvence typu `iterator`.

```cpp
iterator end() const;
```

## <a name="extension"></a> path::Extension –

Vrátí přípona `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Poznámky

Vrátí přípona `filename() X` tak, aby:

Pokud `X == path(".") || X == path("..")` nebo, pokud `X` obsahuje bez tečky přípona je prázdný.

V opačném případě Přípona začíná (a zahrnuje) úplně vpravo tečkou.

## <a name="filename"></a> path::filename –

Vrátí komponentu kořenové adresáře Jmeno, konkrétně `empty() path() : *--end()`. Komponenta může být prázdný.

```cpp
path filename() const;
```

## <a name="generic_string"></a> path::generic_string

Vrátí `this->string<Elem, Traits, Alloc>(al)` s (v části Windows) převést všechny zpětné lomítko na dopředné lomítko.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a> path::generic_u16string

Vrátí `u16string()` s (v části Windows) převést všechny zpětné lomítko na dopředné lomítko.

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a> path::generic_u32string

Vrátí `u32string()` s (v části Windows) převést všechny zpětné lomítko na dopředné lomítko.

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a> path::generic_u8string

Vrátí `u8string()` s (v části Windows) převést všechny zpětné lomítko na dopředné lomítko.

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a> path::generic_wstring

Vrátí `wstring()` s (v části Windows) převést všechny zpětné lomítko na dopředné lomítko.

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a> path::has_extension

Vrátí `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a> path::has_filename –

Vrátí `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a> path::has_parent_path –

Vrátí `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a> path::has_relative_path –

Vrátí `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a> path::has_root_directory –

Vrátí `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a> path::has_root_name –

Vrátí `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a> path::has_root_path –

Vrátí `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a> path::has_stem

Vrátí `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a> path::is_absolute –

Pro Windows, funkce vrátí `has_root_name() && has_root_directory()`. Pro specifikace Posix, funkce vrátí `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a> path::is_relative –

Vrátí `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a> path::iterator

Obousměrné konstantní iterátor, který určuje cestu součástí `myname`.

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

Tato třída popisuje obousměrný konstantní iterátor, který určuje `path` součástí `myname` v pořadí:

1. název kořenového adresáře, pokud jsou k dispozici

1. kořenový adresář, pokud jsou k dispozici

1. zbývající prvky adresáři nadřazeného `path`, pokud jsou k dispozici, a končí název souboru, pokud jsou k dispozici

Pro `pval` objekt typu `path`:

1. `path::iterator X = pval.begin()` Určuje první `path` element v názvu cesty, pokud jsou k dispozici.

1. `X == pval.end()` platí v případě `X` body pouze za koncem sekvence komponent.

3. `*X` Vrátí řetězec, který odpovídá aktuální komponenty

1. `++X` Určuje další komponenta v pořadí, pokud jsou k dispozici.

1. `--X` Určuje předchozí komponenty v pořadí, pokud jsou k dispozici.

1. Změna `myname` zruší platnost všech iterátorů označující prvky v `myname`.

## <a name="make_preferred"></a> path::make_preferred –

Převede každý oddělovače preferred_separator podle potřeby.

```cpp
path& make_preferred();
```

## <a name="native"></a> path::Native

Vrátí `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a> path::Operator =

Nahradí prvky cesta kopie jinou cestu.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Cesta](../standard-library/path-class.md) kopírovaná do `path`.

*Zdroj*<br/>
Cesta ke zdroji.

### <a name="remarks"></a>Poznámky

První operátor kopie člen `right.myname` k `myname`. Druhý operátor člen přesune `right.myname` k `myname`. Třetí členský operátor se chová stejně jako `*this = path(source)`.

## <a name="op_add"></a> path::Operator +=

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

*doprava*<br/>
Přidání cesty.

*str*<br/>
Přidaný řetězec.

*ptr*<br/>
Přidání ukazatele.

*Elem*<br/>
Přidaný `value_type` nebo `Elem`.

*Zdroj*<br/>
Přidání zdroje.

### <a name="remarks"></a>Poznámky

Členské funkce se chovají stejně jako následující odpovídající výrazy:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string\<Elem>(1, elem)));`

## <a name="op_divide"></a> path::Operator / =

Různé `append` výrazy.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Přidání cesty.

*Zdroj*<br/>
Přidání zdroje.

### <a name="remarks"></a>Poznámky

Členské funkce se chovají stejně jako následující odpovídající výrazy:

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a> path::Operator string_type

Vrátí `myname`.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a> path::parent_path

Vrátí nadřazenou součást cesty `myname`.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí nadřazenou součást cesty `myname`, konkrétně předponu `myname` po odebrání `filename().native()` a bezprostředně předcházející oddělovačů adresáře. (Stejně, pokud `begin() != end()`, je kombinování všechny prvky v rozsahu [begin(),--end()) použitím postupně / = – operátor.) Komponenta může být prázdný.

## <a name="path"></a> path::path –

Vytvoří `path` různými způsoby.

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

*doprava*<br/>
Cesta, z nichž má být kopie vytvořené cesty.

*Zdroj*<br/>
Zdroj, z nichž má být kopie vytvořené cesty.

*Umístění*<br/>
Zadanému národnímu prostředí.

*první*<br/>
Pozice prvního prvku, který chcete zkopírovat.

*poslední*<br/>
Pozice posledního prvku, které se mají zkopírovat.

### <a name="remarks"></a>Poznámky

Konstruktory všechny vytvořit `myname` různými způsoby:

Pro `path()` je `myname()`.

Pro `path(const path& right`) je `myname(right.myname)`.

Pro `path(path&& right)` je `myname(right.myname)`.

Pro `template<class Source> path(const Source& source)` je `myname(source)`.

Pro `template<class Source> path(const Source& source, const locale& loc)` je `myname(source)`, získání všechny potřebné codecvt omezující vlastnosti z `loc`.

Pro `template<class InIt> path(InIt first, InIt last)` je `myname(first, last)`.

Pro `template<class InIt> path(InIt first, InIt last, const locale& loc)` je `myname(first, last)`, získání všechny potřebné codecvt omezující vlastnosti z `loc`.

## <a name="preferred_separator"></a> path::preferred_separator

Objekt konstanty poskytuje upřednostňované znak pro oddělení součásti cesty, v závislosti na operačním systému hostitele. 

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Poznámky

Všimněte si, že se jedná o stejnou měrou přípustné ve většině případů v rámci Windows použijte L "/" na příslušné místo.

## <a name="relative_path"></a> path::RELATIVE_PATH –

Vrátí komponentu relativní cesta `myname`. 

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí komponentu relativní cesta `myname`, konkrétně příponu `myname` po odebrání `root_path().native()` a všechny následné okamžitě redundantní oddělovač. Komponenta může být prázdný.

## <a name="remove_filename"></a> path::remove_filename –

Odebere název souboru.

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a> path::replace_extension –

Nahrazuje rozšíření `myname`. 

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parametry

*newext*<br/>
Nové rozšíření.

### <a name="remarks"></a>Poznámky

Nejprve Odebere příponu `extension().native()` z `myname`. Pak v případě `!newext.empty() && newext[0] != dot` (kde `dot` je `*path(".").c_str()`), pak `dot` se připojí k `myname`. Potom `newext` se připojí k `myname`.

## <a name="replace_filename"></a> path::replace_filename –

Nahradí název souboru.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Cesta k souboru.

### <a name="remarks"></a>Poznámky

Členské funkce provede:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a> path::root_directory –

Vrátí komponentu kořenové adresáře `myname`. 

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Poznámky

Komponenta může být prázdný.

## <a name="root_name"></a> path::root_name –

Vrátí komponentu názvu kořenového `myname`. 

```cpp
path root_name() const;
```

### <a name="remarks"></a>Poznámky

Komponenta může být prázdný.

## <a name="root_path"></a> path::root_path –

Vrátí komponentu kořenové cesty `myname`.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Poznámky

Vrátí komponentu kořenové cesty `myname`, konkrétně root_name() / root_directory. Komponenta může být prázdný.

## <a name="stem"></a> path::stem –

Vrátí `stem` komponentu `myname`.

```cpp
path stem() const;
```

### <a name="remarks"></a>Poznámky

Vrátí `stem` komponentu `myname`, konkrétně `filename().native()` ukončené jakékoli `extension().native()` odebrat. Komponenta může být prázdný.

## <a name="string"></a> path::String

Převede sekvenci uložené v `mypath`.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Poznámky

První členská funkce (šablona) převede sekvenci uložené v cesta stejným způsobem jako:

1. `string()` pro `string<char, Traits, Alloc>()`

1. `wstring()` pro `string<wchar_t, Traits, Alloc>()`

1. `u16string()` pro `string<char16_t, Traits, Alloc>()`

1. `u32string()` pro `string<char32_t, Traits, Alloc>()`

Druhá členská funkce převede sekvenci uložené v `mypath` kódování podporuje systém hostitele char pořadí a vrátí je uložená v objektu typu String.

## <a name="string_type"></a> path::STRING_TYPE

Typ je synonymum pro `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a> path::swap –

Spustí `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a> path::u16string

Převede sekvenci uložené v `mypath` UTF-16 a vrátí je uložená v objektu typu `u16string`.

```cpp
u16string u16string() const;
```

## <a name="u32string"></a> path::u32string

Převede sekvenci uložené v `mypath` UTF-32 a vrátí je uložená v objektu typu `u32string`.

```cpp
u32string u32string() const;
```

## <a name="u8string"></a> path::u8string

Převede sekvenci uložené v `mypath` UTF-8 a vrátí je uložená v objektu typu `u8string`.

```cpp
string u8string() const;
```

## <a name="value_type"></a> path::value_type

Typ, který popisuje prvků cesty podporuje operačním systémem hostitele.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a> path::wstring

Převede sekvenci uložené v `mypath` kódování podporuje pro systém hostitele `wchar_t` pořadí a vrátí je uložená v objektu typu `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
