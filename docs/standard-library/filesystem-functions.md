---
title: '&lt;funkce&gt; souborového systému'
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
ms.openlocfilehash: f1b48ed6f533d4ccb5f9ef5e6dbcbd6e5cc4f7a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332054"
---
# <a name="ltfilesystemgt-functions"></a>&lt;funkce&gt; souborového systému

Tyto volné funkce v [ \<záhlaví souborového systém>u](../standard-library/filesystem.md) upravují a dotazují operace na cestách, souborech, symlinkech, adresářích a svazcích. Další informace a příklady kódu naleznete [v tématu File System Navigation (C++)](../standard-library/file-system-navigation.md).

## <a name="absolute"></a><a name="absolute"></a>Absolutní

```cpp
path absolute(const path& pval, const path& base = current_path());
```

Funkce vrátí absolutní cestu odpovídající *pval* vzhledem `base`k cestě :

1. Pokud `pval.has_root_name() && pval.has_root_directory()` funkce vrátí *pval*.

1. Pokud `pval.has_root_name() && !pval.has_root_directory()` funkce `pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`vrátí  /  `pval.relative_path()`.

1. Pokud `!pval.has_root_name() && pval.has_root_directory()` funkce `absolute(base).root_name()`  / vrátí *pval*.

1. Pokud `!pval.has_root_name() && !pval.has_root_directory()` funkce `absolute(base)`  / vrátí *pval*.

## <a name="begin"></a><a name="begin"></a>Začít

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Obě funkce vrátí *iter*.

## <a name="canonical"></a><a name="canonical"></a>Kanonický

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Všechny funkce tvoří absolutní `pabs = absolute(pval, base)` cestu `pabs = absolute(pval)` (nebo pro přetížení bez základního parametru), pak ji zmenšete na kanonický tvar v následujícím pořadí kroků:

1. Každá součást `X` cesty, pro kterou `is_symlink(X)` je **true,** je nahrazena . `read_symlink(X)`

1. Každá součást `.` cesty (tečka je aktuální adresář vytvořený předchozími součástmi cesty) je odebrána.

1. Každá dvojice součástí `X` / `..` cesty (tečka je nadřazený adresář vytvořený předchozími součástmi cesty) je odebrána.

Funkce pak `pabs`vrátí .

## <a name="copy"></a><a name="copy"></a>Kopírovat

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkce všechny případně kopírovat nebo propojit jeden nebo více souborů *na od* *do* pod kontrolou *opts*, který je přijat jako `copy_options::none` pro přetížení bez *opts* parametr. *musí* obsahovat nejvýše jednu z těchto

- `skip_existing`, `overwrite_existing`, nebo`update_existing`

- `copy_symlinks` nebo `skip_symlinks`

- `directories_only`, `create_symlinks`, nebo`create_hard_links`

Funkce nejprve určují `f` file_status hodnoty `t` pro *od* a *do*:

- pokud `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`, telefonicky`symlink_status`

- v opačném případě,`status`

- V opačném případě nahlásíte chybu.

Pokud `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`, oni pak hlásit chybu (a nedělat nic jiného).

V opačném `is_symlink(f)` případě, pokud:

- Pokud `options & copy_options::skip_symlinks`, pak nedělat nic.

- V opačném `!exists(t)&& options & copy_options::copy_symlinks`případě, pokud , then `copy_symlink(from, to, opts)`.

- V opačném případě nahlaste chybu.

V opačném `is_regular_file(f)`případě, pokud , pak:

- Pokud `opts & copy_options::directories_only`, pak nedělat nic.

- V opačném `opts & copy_options::create_symlinks`případě, pokud , then `create_symlink(to, from)`.

- V opačném `opts & copy_options::create_hard_links`případě, pokud , then `create_hard_link(to, from)`.

- V opačném `is_directory(f)`případě, pokud , then `copy_file(from, to`  /  `from.filename(), opts)`.

- V opačném případě hodnota `copy_file(from, to, opts)`.

V opačném `is_directory(f) && (opts & copy_options::recursive || !opts)`případě, pokud , pak:

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

Jinak nedělej nic.

## <a name="copy_file"></a><a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkce všechny případně zkopírovat soubor *na od* *do* pod kontrolou `copy_options::none` *opts*, který je přijat jako pro přetížení bez *opts* parametr. *musí* obsahovat nejvýše jednu `overwrite_existing`z `update_existing` `skip_existing`, nebo .

Pokud `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`, pak oznamte jako chybu, že soubor již existuje.

V opačném `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`případě se pokuste zkopírovat obsah a atributy souboru *do* souboru *do*. Pokud se pokus o kopii nezdaří, oznamte jako chybu.

Funkce vrátí **hodnotu true,** pokud dojde k pokusu o kopii a bude úspěšná, jinak **false**.

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Pokud `is_directory(from)`funkce volá `create_directory_symlink(from, to)`. V opačném `create_symlink(from, to)`případě volá .

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Pro název cesty,\/jako\/je například b c,\/funkce vytvoří adresáře a a\/\/b podle potřeby tak, aby bylo možné vytvořit adresář b c podle potřeby. Vrátí **true** pouze v případě, že skutečně vytvoří *adresář pval*.

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

Funkce vytvoří *pval* adresáře podle potřeby. Vrátí hodnotu true pouze v případě, že ve skutečnosti vytvoří *pval*adresáře `perms::all` , v takovém případě zkopíruje oprávnění z existujícího *attr*souboru nebo použije pro přetížení s *parametrem attr.*

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkce vytvoří propojení jako symlink do adresáře *do*aplikace .

## <a name="create_hard_link"></a><a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

Funkce vytvoří vazbu jako pevný odkaz na adresář nebo soubor *.*

## <a name="create_symlink"></a><a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkce vytvoří *vazbu* jako symlink k souboru *na*.

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Funkce bez parametru *pval* vrátí cestu pro aktuální adresář. Zbývající funkce nastaví aktuální adresář na *pval*.

## <a name="end"></a><a name="end"></a>Konec

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

Vrátí se `directory_iterator()` první funkce a druhá funkce.`recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a>Ekvivalentní

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Funkce vrátí **hodnotu true** pouze v případě, *že levý* a *pravý* zvolit stejnou entitu souborového systému.

## <a name="exists"></a><a name="exists"></a>Existuje

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

První funkce `status_known && stat.type() != file_not_found`vrátí . Druhá a třetí `exists(status(pval))`funkce vrátí .

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí velikost v bajtů souboru zvoleného `exists(pval) && is_regular_file(pval)` *pval*, pokud a velikost souboru lze určit. V opačném případě nahlásí chybu a vrátí se `uintmax_t(-1)`.

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí počet pevných odkazů pro \- *pval*nebo 1, pokud dojde k chybě.

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

Funkce vrátí hodnotu hash pro . `pval.native()`

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

První funkce `stat.type() == file_type::block`vrátí . Zbývající funkce vrátí `is_block_file(status(pval))`.

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

První funkce `stat.type() == file_type::character`vrátí . Zbývající funkce vrátí `is_character_file(status(pval))`.

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

První funkce `stat.type() == file_type::directory`vrátí . Zbývající funkce vrátí `is_directory_file(status(pval))`.

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Pokud `is_directory(pval)`, pak `directory_iterator(pval) == directory_iterator()`funkce vrátí ; v opačném `file_size(pval) == 0`případě vrátí .

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

První funkce `stat.type() == file_type::fifo`vrátí . Zbývající funkce vrátí `is_fifo(status(pval))`.

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

První funkce `stat.type() == file_type::other`vrátí . Zbývající funkce vrátí `is_other(status(pval))`.

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

První funkce `stat.type() == file_type::regular`vrátí . Zbývající funkce vrátí `is_regular_file(status(pval))`.

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

První funkce `stat.type() == file_type::socket`vrátí . Zbývající funkce vrátí `is_socket(status(pval))`.

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

První funkce `stat.type() == file_type::symlink`vrátí . Zbývající funkce vrátí `is_symlink(status(pval))`.

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

První dvě funkce vrátí čas poslední změny dat `file_time_type(-1)` pro *pval*nebo pokud dojde k chybě. Poslední dvě funkce nastavit čas poslední změny dat pro *pval* *na new_time*.

## <a name="permissions"></a><a name="permissions"></a>Oprávnění

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Funkce nastavit oprávnění pro cestu *zvolenpval* `mask & perms::mask` pod kontrolou `perms & (perms::add_perms | perms::remove_perms)`. *maska* musí obsahovat `perms::add_perms` `perms::remove_perms`nejvýše jeden z písmen a) a d).

Pokud `mask & perms::add_perms`funkce nastaví oprávnění `status(pval).permissions() | mask & perms::mask`na . V opačném `mask & perms::remove_perms`případě, pokud , `status(pval).permissions() & ~(mask & perms::mask)`funkce nastavit oprávnění . V opačném případě funkce `mask & perms::mask`nastavit oprávnění k .

## <a name="proximate"></a><a name="proximate"></a>proxim

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

Funkce hlásí chybu a `path()` `!is_symlink(pval)`vrátí se v případě , že . Jinak funkce vrátí objekt typu `path` obsahující symbolický odkaz.

## <a name="relative"></a><a name="relative"></a>Relativní

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>Odebrat

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí **true** `exists(symlink_status(pval))` pouze v případě, že a soubor je úspěšně odebrán. Samotný symlink je odebrán, nikoli soubor, který zvolí.

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Pokud *pval* je adresář, funkce rekurzivně odebrat všechny položky adresáře, pak položka sama. V opačném případě `remove`funkce volání . Vrátí počet všech prvků úspěšně odebrány.

## <a name="rename"></a><a name="rename"></a>Přejmenovat

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

Funkce přejmenují *z* *na na*. Samotný symlink je sám přejmenován, nikoli soubor, který zvolí.

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Funkce mění velikost souboru tak, aby`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>Prostor

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí informace o svazku zvoleném *pval* `space_info`, ve struktuře typu . Struktura obsahuje `uintmax_t(-1)` pro všechny hodnoty, které nelze určit.

## <a name="status"></a><a name="status"></a>Stav

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí stav cesty, typ souboru a oprávnění přidružená k *pval*. Samotný symlink není testován, ale soubor, který zvolí.

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

Funkce vrátí`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>Swap

```cpp
void swap(path& left, path& right) noexcept;
```

Funkce vyměňuje obsah *levé* a *pravé*.

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Funkce vrátí stav symlink s názvem cesty, typ souboru a oprávnění přidružená k *pval*. Funkce se chovají stejně jako `status(pval)` s tím rozdílem, že samotný symlink je testován, nikoli soubor, který zvolí.

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Funkce vrátí absolutní cestu, která bere v úvahu, podle potřeby aktuální adresář přidružený k jeho kořenový název. \(Pro POSIX funkce `absolute(pval)`vrátit .\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Funkce vrátí cestu pro adresář vhodný pro obsahující dočasné soubory.

## <a name="u8path"></a><a name="u8path"></a>u8cesta

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

První funkce se chová stejně jako `path(source)` druhá funkce se `path(first, last)` chová stejně jako s tím rozdílem, že vybraný zdroj v každém případě je považován za posloupnost char prvků kódovaných jako UTF-8, bez ohledu na souborový systém.

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
