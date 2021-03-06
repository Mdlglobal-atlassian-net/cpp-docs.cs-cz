---
title: '&lt;funkce systému&gt; souborů'
ms.date: 03/27/2019
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::absolute
- FILESYSTEM/std::experimental::filesystem::canonical
- FILESYSTEM/std::experimental::filesystem::copy
- FILESYSTEM/std::experimental::filesystem::copy_file
- FILESYSTEM/std::experimental::filesystem::copy_symlink
- FILESYSTEM/std::experimental::filesystem::create_directories
- FILESYSTEM/std::experimental::filesystem::create_directory
- FILESYSTEM/std::experimental::filesystem::create_directory_symlink
- FILESYSTEM/std::experimental::filesystem::create_hard_link
- FILESYSTEM/std::experimental::filesystem::create_symlink
- FILESYSTEM/std::experimental::filesystem::current_path
- FILESYSTEM/std::experimental::filesystem::equivalent
- FILESYSTEM/std::experimental::filesystem::exists
- FILESYSTEM/std::experimental::filesystem::file_size
- FILESYSTEM/std::experimental::filesystem::hard_link_count
- FILESYSTEM/std::experimental::filesystem::hash_value
- FILESYSTEM/std::experimental::filesystem::is_block_file
- FILESYSTEM/std::experimental::filesystem::is_character_file
- FILESYSTEM/std::experimental::filesystem::is_directory
- FILESYSTEM/std::experimental::filesystem::is_empty
- FILESYSTEM/std::experimental::filesystem::is_fifo
- FILESYSTEM/std::experimental::filesystem::is_other
- FILESYSTEM/std::experimental::filesystem::is_regular_file
- FILESYSTEM/std::experimental::filesystem::is_socket
- FILESYSTEM/std::experimental::filesystem::is_symlink
- FILESYSTEM/std::experimental::filesystem::last_write_time
- FILESYSTEM/std::experimental::filesystem::permissions
- FILESYSTEM/std::experimental::filesystem::read_symlink
- FILESYSTEM/std::experimental::filesystem::remove
- FILESYSTEM/std::experimental::filesystem::remove_all
- FILESYSTEM/std::experimental::filesystem::rename
- FILESYSTEM/std::experimental::filesystem::resize_file
- FILESYSTEM/std::experimental::filesystem::space
- FILESYSTEM/std::experimental::filesystem::status
- FILESYSTEM/std::experimental::filesystem::status_known
- FILESYSTEM/std::experimental::filesystem::swap
- FILESYSTEM/std::experimental::filesystem::symlink_status
- FILESYSTEM/std::experimental::filesystem::system_complete
- FILESYSTEM/std::experimental::filesystem::temp_directory_path
- FILESYSTEM/std::experimental::filesystem::u8path
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
helpviewer_keywords:
- std::experimental::filesystem::absolute
- std::experimental::filesystem::canonical
- std::experimental::filesystem::copy
- std::experimental::filesystem::copy_file
- std::experimental::filesystem::copy_symlink
- std::experimental::filesystem::create_directories
- std::experimental::filesystem::create_directory
- std::experimental::filesystem::create_directory_symlink
- std::experimental::filesystem::create_hard_link
- std::experimental::filesystem::create_symlink
- std::experimental::filesystem::current_path
- std::experimental::filesystem::equivalent
- std::experimental::filesystem::exists
- std::experimental::filesystem::file_size
- std::experimental::filesystem::hard_link_count
- std::experimental::filesystem::hash_value
- std::experimental::filesystem::is_block_file
- std::experimental::filesystem::is_character_file
- std::experimental::filesystem::is_directory
- std::experimental::filesystem::is_empty
- std::experimental::filesystem::is_fifo
- std::experimental::filesystem::is_other
- std::experimental::filesystem::is_regular_file
- std::experimental::filesystem::is_socket
- std::experimental::filesystem::is_symlink
- std::experimental::filesystem::last_write_time
- std::experimental::filesystem::permissions
- std::experimental::filesystem::read_symlink
- std::experimental::filesystem::remove
- std::experimental::filesystem::remove_all
- std::experimental::filesystem::rename
- std::experimental::filesystem::resize_file
- std::experimental::filesystem::space
- std::experimental::filesystem::status
- std::experimental::filesystem::status_known
- std::experimental::filesystem::swap
- std::experimental::filesystem::symlink_status
- std::experimental::filesystem::system_complete
- std::experimental::filesystem::temp_directory_path
- std::experimental::filesystem::u8path
ms.openlocfilehash: 1e5994faab69c1809f820b41186d9b618aa7c193
ms.sourcegitcommit: d2ccbba1bf4e66d6b6b0582dc01ba39f4a54f0aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82984081"
---
# <a name="ltfilesystemgt-functions"></a>&lt;funkce systému&gt; souborů

Tyto bezplatné funkce v [ \<hlavičce>systému souborů](../standard-library/filesystem.md) mění a dotazují operace na cestách, souborech, symbolických odkazů, adresářích a svazcích. Další informace a příklady kódu naleznete v tématu [Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md).

## <a name="absolute"></a><a name="absolute"></a>absolutně

```cpp
path absolute(const path& pval, const path& base = current_path());
```

Funkce vrátí absolutní cestu odpovídající *Pval* vzhledem k cestě `base`:

1. Vrátí `pval.has_root_name() && pval.has_root_directory()` -li funkce hodnotu *Pval*.

1. Pokud `pval.has_root_name() && !pval.has_root_directory()` `pval.root_name()`  /  `absolute(base).root_directory()`funkce  / vrátí  / . `absolute(base).relative_path()` `pval.relative_path()`

1. Vrátí `!pval.has_root_name() && pval.has_root_directory()` -li funkce `absolute(base).root_name()`  / hodnotu *Pval*.

1. Vrátí `!pval.has_root_name() && !pval.has_root_directory()` -li funkce `absolute(base)`  / hodnotu *Pval*.

## <a name="begin"></a><a name="begin"></a>ifunctiondiscovery

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Obě funkce vrací *ITER*.

## <a name="canonical"></a><a name="canonical"></a>Interpret

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Všechny funkce tvoří absolutní cestu `pabs = absolute(pval, base)` (nebo `pabs = absolute(pval)` pro přetížení bez základního parametru) a pak ji zmenší na kanonický tvar v následujícím pořadí kroků:

1. Každá součást `X` cesty, pro `is_symlink(X)` kterou je **hodnota true** , `read_symlink(X)`je nahrazena.

1. Každá součást `.` cesty (tečka je aktuální adresář vytvořený pomocí předchozí součásti cesty) je odebrána.

1. Každý pár součástí `X` / `..` cesty (tečka-tečka je nadřazený adresář vytvořený předchozími součástmi cesty) je odebraný.

Funkce pak vrátí `pabs`.

## <a name="copy"></a><a name="copy"></a>kopií

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkce všechny mohou kopírovat nebo propojit jeden nebo více souborů *z* *na k pod kontrolou* *výslovný*, která je pořízena jako `copy_options::none` pro přetížení bez parametru *výslovný* . *výslovný* musí obsahovat nejvýše jednu z těchto:

- `skip_existing`, `overwrite_existing`nebo`update_existing`

- `copy_symlinks` nebo `skip_symlinks`

- `directories_only`, `create_symlinks`nebo`create_hard_links`

Funkce nejprve určí file_status hodnoty `f` *z od* `t` *do*a pro:

- Pokud `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`, při volání`symlink_status`

- v opačném případě voláním`status`

- V opačném případě nahlásí chybu.

V `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`takovém případě nahlásí chybu (a neudělá nic jiného).

`is_symlink(f)` V opačném případě:

- Pokud `options & copy_options::skip_symlinks`a pak neprovádějte žádnou akci.

- V opačném `!exists(t)&& options & copy_options::copy_symlinks`případě, `copy_symlink(from, to, opts)`Pokud.

- V opačném případě nahlaste chybu.

`is_regular_file(f)`V opačném případě:

- Pokud `opts & copy_options::directories_only`a pak neprovádějte žádnou akci.

- V opačném `opts & copy_options::create_symlinks`případě, `create_symlink(to, from)`Pokud.

- V opačném `opts & copy_options::create_hard_links`případě, `create_hard_link(to, from)`Pokud.

- V opačném `is_directory(f)`případě, `copy_file(from, to`  /  `from.filename(), opts)`Pokud.

- V opačném případě hodnota `copy_file(from, to, opts)`.

`is_directory(f) && (opts & copy_options::recursive || !opts)`V opačném případě:

```cpp
if (!exists(t))
{  // copy directory contents recursively
    create_directory(to, from, ec);

    for (directory_iterator next(from), end; ec == error_code() && next != end; ++next)
    {
        copy(next->path(), to / next->path().filename(), opts, ec);
    }
}
```

V opačném případě neprovádějte žádnou akci.

## <a name="copy_file"></a><a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkce všechny mohou kopírovat soubor *z* *do do pod kontrolou* ovládacího prvku *výslovný*, který je pořízen jako `copy_options::none` pro přetížení bez parametru *výslovný* . *výslovný* musí obsahovat maximálně jeden z `skip_existing`, `overwrite_existing`nebo. `update_existing`

Pokud `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`a pak ohlásit jako chybu, že soubor již existuje.

`!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`V opačném případě se pokusí zkopírovat obsah a atributy souboru *z* do souboru *do*. Ohlásit jako chybu, pokud se pokus o kopírování nezdaří

Funkce vrátí **hodnotu true** , pokud dojde k pokusu o zkopírování a úspěchu, jinak **false**.

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Pokud `is_directory(from)`je funkce volána `create_directory_symlink(from, to)`. V opačném případě `create_symlink(from, to)`volá.

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Pro cestu,\/jako je b\/c, funkce vytvoří adresáře a a\/b podle potřeby, aby mohl vytvořit adresář a\/b\/c podle potřeby. Vrátí **hodnotu true** pouze v případě, že ve skutečnosti vytvoří adresář *Pval*.

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

Funkce vytvoří adresář *Pval* podle potřeby. Vrátí hodnotu true pouze v případě, že ve skutečnosti vytvoří adresář *Pval*. v takovém případě kopíruje oprávnění z existujícího souboru *ATTR*nebo `perms::all` používá pro přetížení bez parametru *ATTR* .

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkce vytvoří *v adresáři propojení jako symlink do adresáře*.

## <a name="create_hard_link"></a><a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

Funkce vytvoří odkaz jako pevný odkaz na adresář nebo soubor *na*.

## <a name="create_symlink"></a><a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkce vytvoří *odkaz* jako symlink souboru *na*.

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Funkce bez parametru *Pval* vrátí cestu pro aktuální adresář. Zbývající funkce nastaví aktuální adresář na *Pval*.

## <a name="end"></a><a name="end"></a>účelu

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

První funkce vrátí `directory_iterator()` a druhá funkce vrátí`recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a>stejného

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Funkce vrátí **hodnotu true** pouze v případě, že *levé* a *pravé* zvolí stejnou entitu systému souborů.

## <a name="exists"></a><a name="exists"></a>neexistuje

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

První funkce vrátí `status_known && stat.type() != file_not_found`. Druhá a třetí funkce vrátí `exists(status(pval))`.

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí velikost souboru (v bajtech) zvoleného funkcí *Pval*, pokud `exists(pval) && is_regular_file(pval)` je možné určit velikost souboru. V opačném případě nahlásí chybu `uintmax_t(-1)`a vrátí.

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí počet pevných odkazů pro *Pval*, nebo \-1, pokud dojde k chybě.

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

Funkce vrátí hodnotu hash pro `pval.native()`.

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

První funkce vrátí `stat.type() == file_type::block`. Zbývající funkce vrátí `is_block_file(status(pval))`.

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

První funkce vrátí `stat.type() == file_type::character`. Zbývající funkce vrátí `is_character_file(status(pval))`.

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

První funkce vrátí `stat.type() == file_type::directory`. Zbývající funkce vrátí `is_directory_file(status(pval))`.

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Pokud `is_directory(pval)`je, funkce vrátí hodnotu `directory_iterator(pval) == directory_iterator()`; v opačném `file_size(pval) == 0`případě vrátí.

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

První funkce vrátí `stat.type() == file_type::fifo`. Zbývající funkce vrátí `is_fifo(status(pval))`.

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

První funkce vrátí `stat.type() == file_type::other`. Zbývající funkce vrátí `is_other(status(pval))`.

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

První funkce vrátí `stat.type() == file_type::regular`. Zbývající funkce vrátí `is_regular_file(status(pval))`.

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

První funkce vrátí `stat.type() == file_type::socket`. Zbývající funkce vrátí `is_socket(status(pval))`.

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

První funkce vrátí `stat.type() == file_type::symlink`. Zbývající funkce vrátí `is_symlink(status(pval))`.

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

První dvě funkce vrátí čas poslední změny dat pro *Pval*, nebo `file_time_type(-1)` Pokud dojde k chybě. Poslední dvě funkce nastavily čas poslední změny dat pro *Pval* na *new_time*.

## <a name="permissions"></a><a name="permissions"></a>nastaven

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Funkce nastaví oprávnění pro cestu zvolenou v *Pval* na `mask & perms::mask` pod kontrolou `perms & (perms::add_perms | perms::remove_perms)`. *Maska* musí obsahovat maximálně jeden z `perms::add_perms` a. `perms::remove_perms`

Pokud `mask & perms::add_perms`, funkce nastaví oprávnění na `status(pval).permissions() | mask & perms::mask`. `mask & perms::remove_perms`V opačném případě funkce nastaví oprávnění na `status(pval).permissions() & ~(mask & perms::mask)`. V opačném případě funkce nastaví oprávnění na `mask & perms::mask`.

## <a name="proximate"></a><a name="proximate"></a>Blízkém

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a><a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Funkce nahlásí chybu a vrátí `path()` , pokud `!is_symlink(pval)`. V opačném případě funkce vrátí objekt typu `path` , který obsahuje symbolický odkaz.

## <a name="relative"></a><a name="relative"></a>relativní

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>odebrány

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí **hodnotu true** pouze v `exists(symlink_status(pval))` případě, že soubor byl úspěšně odebrán. Symlink je sám odebraný, nikoli soubor, který si vybírá.

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Pokud je *Pval* adresářem, funkce rekurzivně odeberou všechny položky adresáře a potom vlastní položku. V opačném případě volání `remove`funkce. Vrátí počet všech prvků úspěšně odebraných.

## <a name="rename"></a><a name="rename"></a>Změňte

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

Funkce se přejmenují *z* na *na*. Symlink je sám přejmenován, nikoli soubor, který si zvolí.

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Funkce změní velikost souboru tak, aby`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>Space

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí informace o svazku zvoleném funkcí *Pval*ve struktuře typu `space_info`. Struktura obsahuje `uintmax_t(-1)` pro libovolnou hodnotu, která nemůže být určena.

## <a name="status"></a><a name="status"></a>stav

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí stav cesty, typ souboru a oprávnění přidružené k *Pval*. Symlink sám o sobě není testován, ale soubor, který si zvolí.

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

Funkce vrátí`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>adresu

```cpp
void swap(path& left, path& right) noexcept;
```

Funkce odměňuje obsah *vlevo* a *vpravo*.

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí stav symlink cesty, typ souboru a oprávnění, které jsou přidruženy k *Pval*. Funkce se chovají stejně jako `status(pval)` s tím rozdílem, že symlink je sám testován, nikoli soubor, který si zvolí.

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Funkce vrátí absolutní cestu, která v případě potřeby vezme v úvahu aktuální adresář přidružený ke svému kořenovému názvu. \(U POSIX se vrátí `absolute(pval)`funkce.\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Funkce vrátí cestu k adresáři vhodnému pro adresář, který je vhodný pro obsahující dočasné soubory.

## <a name="u8path"></a><a name="u8path"></a>u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

První funkce se chová stejně jako `path(source)` a druhá funkce se chová stejně jako `path(first, last)` s tím rozdílem, že zvolený zdroj v každém případě je pořízen jako sekvence znakových elementů kódovaných jako UTF-8 bez ohledu na systém souborů.

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
