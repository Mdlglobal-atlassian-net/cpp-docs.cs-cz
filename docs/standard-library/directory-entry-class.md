---
title: directory_entry – třída
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- filesystem/std::experimental::filesystem::directory_entry::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator=
- filesystem/std::experimental::filesystem::directory_entry::assign
- filesystem/std::experimental::filesystem::directory_entry::replace_filename
- filesystem/std::experimental::filesystem::directory_entry::path
- filesystem/std::experimental::filesystem::directory_entry::status
- filesystem/std::experimental::filesystem::directory_entry::symlink_status
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;
- filesystem/std::experimental::filesystem::directory_entry::operator==
- filesystem/std::experimental::filesystem::directory_entry::operator!=
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;=
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;=
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
helpviewer_keywords:
- std::experimental::filesystem::directory_entry
- std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- std::experimental::filesystem::directory_entry::directory_entry
- std::experimental::filesystem::directory_entry::operator=
- std::experimental::filesystem::directory_entry::assign
- std::experimental::filesystem::directory_entry::replace_filename
- std::experimental::filesystem::directory_entry::path
- std::experimental::filesystem::directory_entry::status
- std::experimental::filesystem::directory_entry::symlink_status
- std::experimental::filesystem::directory_entry::operator&lt;
- std::experimental::filesystem::directory_entry::operator==
- std::experimental::filesystem::directory_entry::operator!=
- std::experimental::filesystem::directory_entry::operator&lt;=
- std::experimental::filesystem::directory_entry::operator&gt;
- std::experimental::filesystem::directory_entry::operator&gt;=
ms.openlocfilehash: 35b0dc55bf5db2f799d9ade28cd5968ceab3332b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458962"
---
# <a name="directoryentry-class"></a>directory_entry – třída

Popisuje objekt, který je vrácen pomocí `*X`, kde *X* je [Directory_iterator](../standard-library/directory-iterator-class.md) nebo [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class directory_entry;
```

## <a name="remarks"></a>Poznámky

Třída ukládá objekt typu [cesta](../standard-library/path-class.md). Uložená `path` může být instance [třídy path](../standard-library/path-class.md) nebo typu, který je odvozen z `path`. Také ukládá dvě [file_type](../standard-library/filesystem-enumerations.md#file_type) hodnoty; ten, který představuje informace o stavu uloženého souboru a druhý, který představuje informace o stavu symbolického propojení názvu souboru.

Další informace a příklady kódu naleznete v tématu [Navigace v systému souborůC++()](../standard-library/file-system-navigation.md).

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[directory_entry](#directory_entry)|Výchozí konstruktory se chovají podle očekávání. Čtvrtý konstruktor inicializuje `mypath` *Pval*, `mystat` *stat_arg*a `mysymstat` *symstat_arg*.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[assign](#assign)|Členská funkce přiřadí *Pval* k `mypath`, *statu* `mystat`a *symstat* . `mysymstat`|
|[Cesta](#path)|Vrátí `mypath`členské funkce.|
|[replace_filename](#replace_filename)|Členská funkce nahrazuje `mypath` `mypath.parent_path()` *Pval, s stat_arg*a *symstat_arg*  `mysymstat`  /  `mystat`|
|[status](#status)|Obě členské funkce vracejí `mystat` pravděpodobně, že jsou nejprve změněny.|
|[symlink_status](#symlink_status)|Obě členské funkce vracejí `mysymstat` pravděpodobně, že jsou nejprve změněny.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Nahradí prvky seznamu kopií jiného seznamu.|
|[operátor =](#op_as)|Výchozí operátory přiřazení členů se chovají podle očekávání.|
|[operator==](#op_eq)|Vrátí `mypath == right.mypath`.|
|[operátor <](#op_lt)|Vrátí `mypath < right.mypath`.|
|[operátor < =](#op_lteq)|Vrátí `!(right < *this)`.|
|[operátor >](#op_gt)|Vrátí `right < *this`.|
|[operator>=](#op_gteq)|Vrátí `!(*this < right)`.|
|[operátor const path_type &](#path_type)|Vrátí `mypath`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<experimentální/FileSystem&gt;

**Obor názvů:** std:: experimentální:: FileSystem

## <a name="assign"></a>řadit

Členská funkce přiřadí Pval `mypath`k, *stat_arg* k `mystat`a *symstat_arg* `mysymstat`.

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*\
Cesta k názvu uloženého souboru.

*stat_arg*\
Stav názvu uloženého souboru.

*symstat_arg*\
Stav symbolického odkazu pro uložený název souboru

## <a name="directory_entry"></a>directory_entry

Výchozí konstruktory se chovají podle očekávání. Čtvrtý konstruktor inicializuje `mypath` *Pval*, `mystat` *stat_arg*a `mysymstat` *symstat_arg*.

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*\
Cesta k názvu uloženého souboru.

*stat_arg*\
Stav názvu uloženého souboru.

*symstat_arg*\
Stav symbolického odkazu pro uložený název souboru

## <a name="op_neq"></a>! = – operátor

Vrátí `!(*this == right)`členské funkce.

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Directory_entry](../standard-library/directory-entry-class.md) je porovnán `directory_entry`s.

## <a name="op_as"></a>operátor =

Výchozí operátory přiřazení členů se chovají podle očekávání.

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Directory_entry](../standard-library/directory-entry-class.md) , který se kopíruje `directory_entry`do.

## <a name="op_eq"></a>operator = = – operátor

Vrátí `mypath == right.mypath`členské funkce.

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Directory_entry](../standard-library/directory-entry-class.md) je porovnán `directory_entry`s.

## <a name="op_lt"></a>podnikatel&lt;

Vrátí `mypath < right.mypath`členské funkce.

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Directory_entry](../standard-library/directory-entry-class.md) je porovnán `directory_entry`s.

## <a name="op_lteq"></a>podnikatel&lt;=

Vrátí `!(right < *this)`členské funkce.

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Directory_entry](../standard-library/directory-entry-class.md) je porovnán `directory_entry`s.

## <a name="op_gt"></a>podnikatel&gt;

Vrátí `right < *this`členské funkce.

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Directory_entry](../standard-library/directory-entry-class.md) je porovnán `directory_entry`s.

## <a name="op_gteq"></a>podnikatel&gt;=

Vrátí `!(*this < right)`členské funkce.

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Directory_entry](../standard-library/directory-entry-class.md) je porovnán `directory_entry`s.

## <a name="path_type"></a>operátor const path_type &

Vrátí `mypath`operátor member.

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a>dílčí

Vrátí `mypath`členské funkce.

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a>replace_filename

Členská funkce nahrazuje `mypath` `mypath.parent_path()` *Pval, s stat_arg*a *symstat_arg*  `mysymstat`  /  `mystat`

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*\
Cesta k názvu uloženého souboru.

*stat_arg*\
Stav názvu uloženého souboru.

*symstat_arg*\
Stav symbolického odkazu pro uložený název souboru

## <a name="status"></a>stav

Obě členské funkce vracejí `mystat` pravděpodobně, že jsou nejprve změněny následujícím způsobem:

1. Pokud `status_known(mystat)` pak neprovede žádnou akci.

1. V opačném `!status_known(mysymstat) && !is_symlink(mysymstat)` případě `mystat = mysymstat`, pokud je to.

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parametry

*EHS*\
Kód chyby stavu.

## <a name="symlink_status"></a>symlink_status

Obě členské funkce vracejí `mysymstat` pravděpodobně, že jsou nejprve změněny následujícím způsobem: Pokud `status_known(mysymstat)` pak neprovede žádnou akci. V opačném případě. `mysymstat = symlink_status(mypval)`

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parametry

*EHS*\
Kód chyby stavu.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<systému souborů&gt;](../standard-library/filesystem.md)
