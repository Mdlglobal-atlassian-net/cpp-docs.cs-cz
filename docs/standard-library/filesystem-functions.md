---
title: '&lt;systém souborů&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: 0e47339813256d189e1ce6b71506d9ae29a93f51
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213462"
---
# <a name="ltfilesystemgt-functions"></a>&lt;systém souborů&gt; funkce

Tyto nové bezplatné funkce v [ \<filesystem >](../standard-library/filesystem.md) záhlaví provést úpravy a dotaz týkající se cesty, soubory, symbolických odkazů, adresářů a svazky. Další informace a příklady kódu naleznete v tématu [navigace systému souborů (C++)](../standard-library/file-system-navigation.md).
||||
|-|-|-|
|[Absolutní](#absolute)|[začít](#begin)|[Canonical](#canonical)|
|[kopírování](#copy)|[copy_file –](#copy_file)|[copy_symlink](#copy_symlink)|
|[create_directories](#create_directories)|[create_directory](#create_directory)|[create_directory_symlink](#create_directory_symlink)|
|[create_hard_link](#create_hard_link)|[create_symlink](#create_symlink)|[current_path](#current_path)|
|[ukončení](#end)|[ekvivalent](#equivalent)|[Existuje](#exists)|
|[file_size –](#file_size)|[hard_link_count](#hard_link_count)|[hash_value](#hash_value)|
|[is_block_file](#is_block_file)|[is_character_file](#is_character_file)|[is_directory](#is_directory)|
|[is_empty](#is_empty)|[is_fifo](#is_fifo)|[is_other](#is_other)|
|[is_regular_file](#is_regular_file)|[is_socket](#is_socket)|[is_symlink](#is_symlink)|
|[last_write_time](#last_write_time)|[Oprávnění](#permissions)|[read_symlink](#read_symlink)|
|[remove](#remove)|[remove_all](#remove_all)|[Přejmenovat](#rename)|
|[resize_file –](#resize_file)|[space](#space)|[Stav](#status)|
|[status_known –](#status_known)|[Prohození](#swap)|[symlink_status](#symlink_status)|
|[system_complete](#system_complete)|[temp_directory_path](#temp_directory_path)|[u8path](#u8path)|


## <a name="absolute"></a> Absolutní

```cpp
path absolute(const path& pval, const path& base = current_path());
```

Funkce vrátí absolutní cesta odpovídající `pval` vzhledem k názvu cesty `base`:

1. Pokud pval.has_root_name() & & pval.has_root_directory() funkce vrátí pval.

1. Pokud pval.has_root_name() & &! pval.has_root_directory() funkce vrátí pval.root_name() / absolute(base).root_directory() / absolute(base).relative_path() / pval.relative_path().

1. Pokud! pval.has_root_name() & & pval.has_root_directory() funkce vrátí absolute(base).root_name() / pval.

1. Pokud! pval.has_root_name() & &! pval.has_root_directory() funkce vrátí absolute(base) / pval.

## <a name="begin"></a>  začít

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Obě funkce vrátí `iter`.

## <a name="canonical"></a>  Canonical

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Všechny funkce formuláře absolutní cesta pabs = absolutní (pval, base) (nebo pabs = absolute(pval) pro přetížení s parametrem žádné základní), pak snížit na kanonický tvar v následujícím pořadí kroků:

1. Všechny komponenty cesty X které is_symlink(X) má hodnotu true je nahrazena read_symlink(X).

1. Všechny komponenty cesty. (tečka je aktuální adresář stanovené předchozí komponenty cesta) se odebere.

1. Každá dvojice X součástí cesty /.. (tečka – tečka je nadřazený adresář stanovené předchozí komponenty cesta) se odebere.

Funkce pak vrátí pabs.

## <a name="copy"></a>  kopírování

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkce všech případně zkopírujte nebo odkaz na jeden nebo více souborů `from` k `to` pod kontrolou `opts`, který je považován za copy_options::none pro přetížení bez `opts` parametru. `opts` musí obsahovat nanejvýš jeden z:

- skip_existing, overwrite_existing nebo update_existing

- copy_symlinks nebo skip_symlinks

- directories_only, create_symlinks nebo create_hard_links

Funkce nejprve určit file_status – f hodnoty pro `from` a t pro `to`:

- Pokud požádá o & (copy_options::create_symlinks &#124; copy_options::skip_symlinks), Autor symlink_status – volání

- v opačném případě voláním stav

- V opačném případě Oznamte chybu.

Pokud! exists(f) &#124; &#124; ekvivalent (f, t) &#124; &#124; is_other(f) &#124; &#124; is_other(t) &#124; &#124; is_directory(f) & & is_regular_file(t), potom nahlásit chybu (a dělat nic dalšího).

Jinak, pokud is_symlink(f) pak:

- Pokud možnosti & copy_options::skip_symlinks proveďte žádnou akci.

- Jinak, pokud! exists(t) & & Možnosti & copy_options::copy_symlinks pak copy_symlink – (od, požádá o).

- V opačném případě Oznamte chybu.

Jinak, pokud is_regular_file(f) pak:

- Pokud požádá o & copy_options::directories_only pak Neprovádět žádnou akci.

- Jinak, pokud požádá o & copy_options::create_symlinks pak create_symlink(to, from).

- Jinak, pokud požádá o & copy_options::create_hard_links pak create_hard_link(to, from).

- Jinak, pokud is_directory(f) pak copy_file – (z položky/from.filename(), požádá o).

- Copy_file – jinak (od, požádá o).

Jinak, pokud is_directory(f) & & (požádá o & copy_options::recursive &#124; &#124; ! požádá o) pak:

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

V opačném případě Neprovádět žádnou akci.

## <a name="copy_file"></a>  copy_file –

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Funkce všechny možné zkopírovat soubor na `from` k `to` pod kontrolou `opts`, který je považován za copy_options::none pro přetížení bez `opts` parametru. `opts` musí obsahovat nanejvýš jeden skip_existing, overwrite_existing nebo update_existing.

Pokud existuje\(k\) && \!\(požádá o & \(copy_options::skip_existing &#124; copy_options::overwrite_existing &#124; copy_options::update_existing\) \) pak sestavu jako chybu, že soubor již existuje.

Jinak, pokud \!existuje\(k\) &#124; &#124; požádá o & copy_options::overwrite_existing &#124; &#124; požádá o & copy_options::update_existing & & last_write_time –\(do \) \< last_write_time –\(z\) &#124; &#124; \! \(požádá o & \(copy_options::skip_existing &#124; copy_options::o verwrite_existing &#124; copy_options:update_existing\) \) pak se pokusíte zkopírovat obsah a atributy souboru ze souboru. Sestavu jako chybu, pokud se nezdaří pokus o kopírování.

Funkce vrátí hodnotu PRAVDA, pokud dojde k pokusu o kopírování a úspěšné, jinak hodnota false.

## <a name="copy_symlink "></a>  copy_symlink –

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Pokud is_directory\(z\) funkce volá create_directory_symlink –\(z možnosti\). V opačném případě volá create_symlink –\(z možnosti\).

## <a name="create_directories"></a>  create_directories –

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Pro název cesty, jako\/b\/c funkce vytvoří adresáře a\/b podle potřeby, takže je možné vytvořit adresář\/b\/c podle potřeby. To vrací hodnotu true, pouze pokud se ve skutečnosti vytváří adresáři `pval`.

## <a name="create_directory"></a>  create_directory –

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

Funkce vytvoří adresář `pval` podle potřeby. To vrací hodnotu true, pouze pokud se ve skutečnosti vytváří adresáři `pval`, v takovém případě kopíruje oprávnění z existujícího souboru `attr`, nebo využívá perms::all pro přetížení bez `attr` parametru.

## <a name="create_directory_symlink "></a>  create_directory_symlink –

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkce vytvoří odkaz jako symlink k adresáři `to`.

## <a name="create_hard_link"></a>  create_hard_link –

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

Funkce vytvoří odkaz jako pevný odkaz pro adresář nebo soubor `to`.

## <a name="create_symlink "></a>  create_symlink –

```cpp
void create_symlink(const path& to,  const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Funkce vytvoří `link` jako symlink do souboru `to`.

## <a name="current_path"></a>  current_path –

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Funkce se žádný parametr `pval` vrátí název cesty pro aktuální adresář. Zbývající funkce nastavit aktuální adresář `pval`.

## <a name="end"></a>  ukončení

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

První funkce vrací directory_iterator –\( \) a druhá funkce vrátí recursive_directory_iterator –\(\)

## <a name="equivalent"></a>  ekvivalent

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Funkce vrací hodnotu true pouze v případě `left` a `right` určit stejné entity systému souborů.

## <a name="exists"></a>  Existuje

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

První funkce vrací status_known – & & stat.type\( \) \! \= file_not_found. Druhý a třetí funkce vrací existuje\(stav\(pval\)\).

## <a name="file_size"></a>  file_size –

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí velikost v bajtech souboru určeném `pval`, pokud existuje\(pval\) & & is_regular_file –\(pval\) a můžete určit velikost souboru. V opačném případě se ohlásí chyby a vrátí uintmax_t\(\-1\).

## <a name="hard_link_count"></a>  hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí počet pevných odkazů pro `pval`, nebo \-1, pokud dojde k chybě.

## <a name="hash_value"></a>  hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

Funkce vrátí hodnotu hash pro pval.native\(\).

## <a name="is_block_file"></a>  is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

První funkce vrací stat.type\( \) \= \= file_type::block. Zbývající funkce vrátí is_block_file\(stav\(pval\)\).

## <a name="is_character_file"></a>  is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

První funkce vrací stat.type\( \) \= \= file_type::character. Zbývající funkce vrátí is_character_file\(stav\(pval\)\).

## <a name="is_directory "></a>  is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

První funkce vrací stat.type\( \) \= \= file_type::directory. Zbývající funkce vrátí is_directory_file\(stav\(pval\)\).

## <a name="is_empty"></a>  is_empty –

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Pokud is_directory\(pval\) directory_iterator – vrátí funkce\(pval\) \= \= directory_iterator –\(\); v opačném případě vrátí název_ velikost\(pval\) \= \= 0.

## <a name="is_fifo"></a>  is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

První funkce vrací stat.type\( \) \= \= file_type::fifo. Zbývající funkce vrátí is_fifo\(stav\(pval\)\).

## <a name="is_other"></a>  is_other –

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

První funkce vrací stat.type\( \) \= \= file_type::other. Is_other – vrátí zbývající funkce\(stav\(pval\)\).

## <a name="s_regular_file"></a>  is_regular_file –

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

První funkce vrací stat.type\( \) \= \= file_type::regular. Is_regular_file – vrátí zbývající funkce\(stav\(pval\)\).

## <a name="is_socket"></a>  is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

První funkce vrací stat.type\( \) \= \= file_type::socket. Zbývající funkce vrátí is_socket\(stav\(pval\)\).

## <a name="is_symlink"></a>  is_symlink –

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

První funkce vrací stat.type\( \) \= \= file_type::symlink. Is_symlink – vrátí zbývající funkce\(stav\(pval\)\).

## <a name="last_write_time"></a>  last_write_time –

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

První dvě funkce vrátí čas poslední změny dat pro `pval`, nebo file_time_type\(\-1\) Pokud dojde k chybě. Poslední dvě funkce nastaví čas poslední změny dat pro `pval` k new_time.

## <a name="permissions"></a>  Oprávnění

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Funkce nastaví oprávnění pro cesty určené `pval` maska & perms::mask pod kontrolou oprávnění & \(perms::add_perms &#124; perms::remove_perms\). Maska musí obsahovat nanejvýš jeden perms::add_perms a perms::remove_perms.

Pokud maska & perms::add_perms funkce nastaví oprávnění pro stav stav\(pval\).permissions\( \) &#124; maska & perms::mask. Jinak, pokud maska & perms::remove_perms funkce nastaví oprávnění pro stav stav\(pval\).permissions\( \) & ~\(maska & perms::mask\). Jinak funkce nastaví oprávnění maska & perms::mask.

## <a name="read_symlink"></a>  read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Funkce nahlásit chyby a vrátí cestu\( \) Pokud \!is_symlink –\(pval\). V opačném případě vrátí funkce objekt typu `path` obsahující symbolický odkaz.

## <a name="remove"></a>  odebrat

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Funkce vrací hodnotu true pouze tehdy, pokud existuje\(symlink_status –\(pval\) \) a soubor se úspěšně odebral. Symlink je sama o sobě odebrána, není soubor, který se jmenuje.

## <a name="remove_all"></a>  remove_all –

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Pokud `pval` je adresář, funkce rekurzivně odebrat všechny položky adresář a potom položku samotný. V opačném případě volání funkce odebrat. Vrátí počet všech elementů se úspěšně odebral.

## <a name="rename"></a>  Přejmenovat

```cpp
void rename(const path& from,  const path& to);
void rename(const path& from,  const path& to, error_code& ec) noexcept;
```

Přejmenování funkce `from` k `to`. Symlink je sama o sobě přejmenovali, není soubor, který se jmenuje.

## <a name="resize_file"></a>  resize_file –

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Změnit velikost souboru takové funkce tohoto file_size –\(pval\) \= \= velikost

## <a name="space"></a>  místo

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí informace o svazku určeném `pval`, v strukturu typu `space_info`. Struktura obsahuje uintmax_t\(\-1\) pro libovolnou hodnotu, která nelze určit.

## <a name="status"></a>  Stav

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Funkce vrátí název cesty stav, typ souboru a oprávnění přidružené k `pval`. Symlink je sama o sobě není testovány, ale tento soubor Určuje.

## <a name="status_known"></a>  status_known –

```cpp
bool status_known(file_status stat) noexcept;
```

Funkce vrátí stat.type\( \) \! \= file_type::none

## <a name="swap"></a>  Prohození

```cpp
void swap(path& left, path& right) noexcept;
```

Funkce vyměňuje obsahy `left` a `right`.

## <a name="symlink_status"></a>  symlink_status –

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Funkce vrátí stav symlink cesty, typ souboru a oprávnění přidružené k `pval`. Tyto funkce se chovají stejně jako stav\(pval\) s tím rozdílem, že symlink samotného testování, nikoli soubor jmenuje.

## <a name="system_complete"></a>  system_complete –

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Vrátí absolutní cestu souboru, který bere v úvahu, podle potřeby, aktuální adresář spojené s jeho název kořenové funkce. \(Pro specifikace Posix, funkce vrátí absolutní\(pval\).\)

## <a name="temp_directory_path"></a>  temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Funkce vrátí název cesty k adresáři vhodný pro dočasné soubory.

## <a name="u8path"></a>  u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

První funkce se chová stejně jako path(source) a druhá funkce se chová stejně jako cestu (jméno, příjmení) s tím rozdílem, že určený zdroj v každém případě je považován za sekvenci prvků char kódováním UTF-8, bez ohledu na to systém souborů.


