---
title: '&lt;výčty souborového systému&gt;'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
ms.openlocfilehash: 0d5b31b31f9f435c52db89521b4b753c16d86501
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368412"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;výčty souborového systému&gt;

Toto téma dokumentuje výčty v záhlaví souborového systému.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<experimentální/souborový systém>

**Obor názvů:** std::experimental::filesystem

## <a name="copy_options"></a><a name="copy_options"></a>copy_options

Výčet hodnot bitové masky, který se používá s [funkcemi copy](filesystem-functions.md#copy) a [copy_file](filesystem-functions.md#copy_file) k určení chování.

### <a name="syntax"></a>Syntaxe

```cpp
enum class copy_options {
   none = 0,
   skip_existing = 1,
   overwrite_existing = 2,
   update_existing = 4,
   recursive = 8,
   copy_symlinks = 16,
   skip_symlinks = 32,
   directories_only = 64,
   create_symlinks = 128,
   create_hard_links = 256
};
```

### <a name="values"></a>Hodnoty

|`Name`|Popis|
|------------|-----------------|
|`none`|Proveďte výchozí chování pro operaci.|
|`skip_existing`|Nekopírovat, pokud soubor již existuje, neoznamujte chybu.|
|`overwrite_existing`|Přepište soubor, pokud již existuje.|
|`update_existing`|Přepište soubor, pokud již existuje a je starší než nahrazení.|
|`recursive`|Rekurzivně kopírujte podadresáře a jejich obsah.|
|`copy_symlinks`|Zkopírujte symbolické odkazy jako symbolické odkazy namísto kopírování souborů, na které odkazují.|
|`skip_symlinks`|Ignorovat symbolické odkazy.|
|`directories_only`|Pouze iterate přes adresáře, ignorovat soubory.|
|`create_symlinks`|Místo kopírování souborů vytvořte symbolické odkazy. Absolutní cesta musí být použita jako zdrojová cesta, pokud cíl není aktuální masce.|
|`create_hard_links`|Vytvořte pevné odkazy namísto kopírování souborů.|

## <a name="directory_options"></a><a name="directory_options"></a>directory_options

Určuje, zda se mají používat symbolické odkazy na adresáře nebo je ignorovat.

### <a name="syntax"></a>Syntaxe

```cpp
enum class directory_options {
   none = 0,
   follow_directory_symlink
};
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`none`|Výchozí chování: ignorovat symbolické odkazy na adresáře. Odepření oprávnění je chyba.|
|`follow_directory_symlink`|Považovat symbolické odkazy na adresáře jako skutečné adresáře.|

## <a name="file_type"></a><a name="file_type"></a>file_type

Výčet pro typy souborů. Podporované hodnoty jsou pravidelné, adresář, not_found a neznámé.

### <a name="syntax"></a>Syntaxe

```cpp
enum class file_type {
    not_found = -1,
    none,
    regular,
    directory,
    symlink,
    block,
    character,
    fifo,
    socket,
    unknown
};
```

### <a name="values"></a>Hodnoty

|Name (Název)|Hodnota|Popis|
|----------|-----------|-----------------|
|`not_found`|-1|Představuje soubor, který neexistuje.|
|`none`|0|Představuje soubor, který nemá žádný atribut typu. (Není podporováno.)|
|`regular`|1|Představuje konvenční soubor disku.|
|`directory`|2|Představuje adresář.|
|`symlink`|3|Představuje symbolický odkaz. (Není podporováno.)|
|`block`|4|Představuje soubor se speciálním blokem v systémech založených na systému UNIX. (Není podporováno.)|
|`character`|5|Představuje soubor se speciálním znakem v systémech založených na systému UNIX. (Není podporováno.)|
|`fifo`|6|Představuje soubor FIFO v systémech založených na systému UNIX. (Není podporováno.)|
|`socket`|7|Představuje soket v systémech založených na systému UNIX. (Není podporováno.)|
|`unknown`|8|Představuje soubor, jehož stav nelze určit.|

## <a name="perm_options"></a><a name="perm_options"></a>perm_options

Zahrnuje `replace`hodnoty `add` `remove`, `nofollow`, a .

```cpp
enum class perm_options;
```

## <a name="perms"></a><a name="perms"></a>trvalá

Příznaky oprávnění k souborům. Podporované hodnoty jsou v podstatě "jen pro čtení" a všechny. Pro soubor jen pro čtení nejsou nastaveny žádné *_write bitů. V `all` opačném případě je nastaven bit (0x0777).

### <a name="syntax"></a>Syntaxe

```cpp
enum class perms {// names for permissions
   none = 0,
   owner_read = 0400,  // S_IRUSR
   owner_write = 0200, // S_IWUSR
   owner_exec = 0100,  // S_IXUSR
   owner_all = 0700,   // S_IRWXU
   group_read = 040,   // S_IRGRP
   group_write = 020,  // S_IWGRP
   group_exec = 010,   // S_IXGRP
   group_all = 070,    // S_IRWXG
   others_read = 04,   // S_IROTH
   others_write = 02,  // S_IWOTH
   others_exec = 01,   // S_IXOTH
   others_all = 07,    // S_IRWXO
   all = 0777,
   set_uid = 04000,    // S_ISUID
   set_gid = 02000,    // S_ISGID
   sticky_bit = 01000, // S_ISVTX
   mask = 07777,
   unknown = 0xFFFF,
   add_perms = 0x10000,
   remove_perms = 0x20000,
   resolve_symlinks = 0x40000
};
```

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<>souborového systému](../standard-library/filesystem.md)
