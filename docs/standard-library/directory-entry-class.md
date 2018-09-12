---
title: directory_entry – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: 3c61d69c1ee5ad40191771dabd829514e3381e88
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691403"
---
# <a name="directoryentry-class"></a>directory_entry – třída

Popisuje objekt, který je vrácen `*X`, kde *X* je [directory_iterator –](../standard-library/directory-iterator-class.md) nebo [recursive_directory_iterator –](../standard-library/recursive-directory-iterator-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class directory_entry;
```

## <a name="remarks"></a>Poznámky

Uloží objekt typu třídy [cesta](../standard-library/path-class.md). Uložený `path` může být instancí třídy [path – třída](../standard-library/path-class.md) nebo typu, který je odvozen z `path`. Také ukládá dvě [file_type](../standard-library/filesystem-enumerations.md#file_type) hodnoty; ten, který reprezentuje, co se jedná o stav názvu uloženého souboru a další vlastnost, která představuje, co se jedná o stav symbolického odkazu názvu souboru.

Další informace a příklady kódu naleznete v tématu [navigace systému souborů (C++)](../standard-library/file-system-navigation.md).

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[directory_entry –](#directory_entry)|Výchozí konstruktory chovat dle očekávání. Čtvrtý konstruktor inicializuje `mypath` k *pval*, `mystat` k *stat_arg*, a `mysymstat` k *symstat_arg*.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[přiřazení](#assign)|Členská funkce přiřadí *pval* k `mypath`, *stat* k `mystat`, a *symstat* k `mysymstat`.|
|[Cesta](#path)|Členská funkce vrátí `mypath`.|
|[replace_filename](#replace_filename)|Členská funkce se nahradí `mypath` s `mypath.parent_path()`  /  *pval*, `mystat` s *stat_arg*, a `mysymstat` s *symstat_arg*|
|[Stav](#status)|Obě členské funkce vrátí `mystat` může být nejprve změněn.|
|[symlink_status](#symlink_status)|Obě členské funkce vrátí `mysymstat` může být nejprve změněn.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Nahradí prvky seznamu kopii jiného seznamu.|
|[operátor =](#op_as)|Operátory přiřazení nastavený na výchozí hodnotu člena chovat dle očekávání.|
|[operator==](#op_eq)|Vrátí `mypath == right.mypath`.|
|[Operator <](#op_lt)|Vrátí `mypath < right.mypath`.|
|[Operator < =](#op_lteq)|Vrátí `!(right < *this)`.|
|[Operator >](#op_gt)|Vrátí `right < *this`.|
|[operator>=](#op_gteq)|Vrátí `!(*this < right)`.|
|[operátor – konstanta path_type &](#path_type)|Vrátí `mypath`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<experimentální/systému souborů&gt;

**Namespace:** std::experimental::filesystem

## <a name="assign"></a> přiřazení

Členská funkce přiřadí *pval* k `mypath`, *stat_arg* k `mystat`, a *symstat_arg* k `mysymstat`.

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Cesta k názvu uloženého souboru.  

*stat_arg*<br/>
Stav názvu uloženého souboru.  

*symstat_arg*<br/>
Symbolický odkaz stav názvu uloženého souboru.  

## <a name="directory_entry"></a> directory_entry –

Výchozí konstruktory chovat dle očekávání. Čtvrtý konstruktor inicializuje `mypath` k *pval*, `mystat` k *stat_arg*, a `mysymstat` k *symstat_arg*.

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Cesta k názvu uloženého souboru.  

*stat_arg*<br/>
Stav názvu uloženého souboru.  

*symstat_arg*<br/>
Symbolický odkaz stav názvu uloženého souboru.  

## <a name="op_neq"></a> Operator! =

Členská funkce vrátí `!(*this == right)`.

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Directory_entry –](../standard-library/directory-entry-class.md) porovnávané hodnotě `directory_entry`.  

## <a name="op_as"></a> operátor =

Operátory přiřazení nastavený na výchozí hodnotu člena chovat dle očekávání.

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Directory_entry –](../standard-library/directory-entry-class.md) kopírovaná do `directory_entry`.  

## <a name="op_eq"></a> Operator ==

Členská funkce vrátí `mypath == right.mypath`.

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Directory_entry –](../standard-library/directory-entry-class.md) porovnávané hodnotě `directory_entry`.  

## <a name="op_lt"></a> – Operátor&lt;

Členská funkce vrátí `mypath < right.mypath`.

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Directory_entry –](../standard-library/directory-entry-class.md) porovnávané hodnotě `directory_entry`.  

## <a name="op_lteq"></a> – Operátor&lt;=

Členská funkce vrátí `!(right < *this)`.

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Directory_entry –](../standard-library/directory-entry-class.md) porovnávané hodnotě `directory_entry`.  

## <a name="op_gt"></a> – Operátor&gt;

Členská funkce vrátí `right < *this`.

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Directory_entry –](../standard-library/directory-entry-class.md) porovnávané hodnotě `directory_entry`.  

## <a name="op_gteq"></a> – Operátor&gt;=

Členská funkce vrátí `!(*this < right)`.

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
[Directory_entry –](../standard-library/directory-entry-class.md) porovnávané hodnotě `directory_entry`.  

## <a name="path_type"></a> operátor – konstanta path_type &

Členský operátor vrátí `mypath`.

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a> Cesta

Členská funkce vrátí `mypath`.

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a> replace_filename

Členská funkce se nahradí `mypath` s `mypath.parent_path()`  /  *pval*, `mystat` s *stat_arg*, a `mysymstat` s *symstat_arg*

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametry

*pval*<br/>
Cesta k názvu uloženého souboru.  

*stat_arg*<br/>
Stav názvu uloženého souboru.  

*symstat_arg*<br/>
Symbolický odkaz stav názvu uloženého souboru.  

## <a name="status"></a> Stav

Obě členské funkce vrátí `mystat` může být nejprve změněn následujícím způsobem:

1. Pokud `status_known(mystat)` pak Neprovádět žádnou akci.

1. Jinak, pokud `!status_known(mysymstat) && !is_symlink(mysymstat)` pak `mystat = mysymstat`.

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parametry

*ES*<br/>
Stavový kód chyby.  

## <a name="symlink_status"></a> symlink_status –

Obě členské funkce vrátí `mysymstat` může být nejprve změněn následujícím způsobem: Pokud `status_known(mysymstat)` pak Neprovádět žádnou akci. V opačném případě `mysymstat = symlink_status(mypval)`.

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parametry

*ES*<br/>
Stavový kód chyby.  

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<systém souborů&gt;](../standard-library/filesystem.md)<br/>
