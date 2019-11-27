---
title: '&lt;výčet&gt; systému souborů'
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
ms.openlocfilehash: f148347cd132a604622415c65bb3e0352f5308eb
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303500"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;výčet&gt; systému souborů

Toto téma popisuje výčty v hlavičce systému souborů.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<experimentální/FileSystem >

**Obor názvů:** std:: experimentální:: FileSystem

## <a name="copy_options"></a>copy_options

Výčet hodnot bitových kopií, které se používají s funkcemi [kopírování](filesystem-functions.md#copy) a [copy_file](filesystem-functions.md#copy_file) k určení chování.

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
|`none`|Pro operaci proveďte výchozí chování.|
|`skip_existing`|Nekopírovat, pokud soubor již existuje, Neoznamovat chybu.|
|`overwrite_existing`|Přepsat soubor, pokud již existuje.|
|`update_existing`|Přepsat soubor, pokud již existuje a je starší než náhrada.|
|`recursive`|Rekurzivně kopíruje podadresáře a jejich obsah.|
|`copy_symlinks`|Zkopírujte symbolické odkazy jako symbolické odkazy namísto kopírování souborů, na které odkazuje.|
|`skip_symlinks`|Ignorovat symbolické odkazy.|
|`directories_only`|Iterujte jenom přes adresáře a Ignorujte soubory.|
|`create_symlinks`|Místo kopírování souborů zajistěte symbolické odkazy. Absolutní cesta musí být použita jako zdrojová cesta, pokud cíl není aktuální adresář.|
|`create_hard_links`|Místo kopírování souborů je třeba provést pevné odkazy.|

## <a name="directory_options"></a>directory_options

Určuje, zda se mají sledovat symbolické odkazy na adresáře nebo ignorovat.

### <a name="syntax"></a>Syntaxe

```cpp
enum class directory_options {
   none = 0,
   follow_directory_symlink
};
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`none`|Výchozí chování: ignorovat symbolické odkazy na adresáře. Odepření oprávnění je chyba.|
|`follow_directory_symlink`|Považovat symbolické odkazy na adresáře jako skutečné adresáře.|

## <a name="file_type"></a>file_type

Výčet pro typy souborů. Podporované hodnoty jsou Regular, Directory, not_found a Unknown.

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

|Název|Hodnota|Popis|
|----------|-----------|-----------------|
|`not_found`|-1|Představuje soubor, který neexistuje.|
|`none`|0|Představuje soubor, který nemá žádný atribut typu. (Není podporováno.)|
|`regular`|1|Představuje soubor konvenčního disku.|
|`directory`|2|Představuje adresář.|
|`symlink`|3|Představuje symbolický odkaz. (Není podporováno.)|
|`block`|4|Představuje zvláštní blokový soubor v systémech založených na systému UNIX. (Není podporováno.)|
|`character`|5|Představuje speciální znakový soubor v systémech založených na systému UNIX. (Není podporováno.)|
|`fifo`|6|Představuje soubor FIFO v systémech UNIX. (Není podporováno.)|
|`socket`|7|Představuje soket v systémech UNIX. (Není podporováno.)|
|`unknown`|8|Představuje soubor, jehož stav nelze určit.|

## <a name="perm_options"></a>perm_options

Zahrnuje hodnoty `replace`, `add`, `remove`a `nofollow`.

```cpp
enum class perm_options;
```

## <a name="perms"></a>oprávnění

Příznaky pro oprávnění k souborům Podporované hodnoty jsou v podstatě "ReadOnly" a všechny. U souboru jen pro čtení není nastavená žádná z těchto * _write bitů. V opačném případě je nastaven bit `all` (0x0777).

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

## <a name="see-also"></a>Viz také:

\ [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[\<> systému souborů](../standard-library/filesystem.md)
