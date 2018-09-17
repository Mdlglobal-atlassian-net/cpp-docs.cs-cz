---
title: '&lt;systém souborů&gt; výčty | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
dev_langs:
- C++
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff655573f77b901725fe18c2346c46306c9b853a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716804"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;systém souborů&gt; výčty

Toto téma popisuje výčty v hlavičce systému souborů.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<experimentální/filesystem >

**Namespace:** std::experimental::filesystem

## <a name="copy_options"></a>  copy_options

Výčet hodnot bitová maska, které se používá s [kopírování](filesystem-functions.md#copy) a [copy_file –](filesystem-functions.md#copy_file) funkce k určení chování.

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
|`none`|Pro tuto operaci proveďte výchozí.|
|`skip_existing`|Pokud soubor již existuje, nekopírujte nehlásí chybu.|
|`overwrite_existing`|Přepište soubor, pokud již existuje.|
|`update_existing`|Přepište soubor, pokud již existuje a je starší než nahrazení.|
|`recursive`|Podadresáře rekurzivně kopírovat a jejich obsah.|
|`copy_symlinks`|Kopírovat jako symbolické odkazy, namísto kopírování souborů, které ukazují na symbolické odkazy.|
|`skip_symlinks`|Ignorujte symbolické odkazy.|
|`directories_only`|Pouze iterovat adresáře, ignorování souborů.|
|`create_symlinks`|Vytvořte symbolické odkazy namísto kopírování souborů. Absolutní cesta musí použít jako zdrojovou cestu, pokud cíl je aktuální adresář.|
|`create_hard_links`|Ujistěte se, pevné odkazy namísto kopírování souborů.|


## <a name="directory_options"></a> directory_options –

Určuje, zda chcete postupovat podle symbolické odkazy na adresáře nebo je chcete ignorovat.

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
|`none`|Výchozí chování: Ignorovat symbolické odkazy na adresáře. Oprávnění byla odepřena se o chybu.|
|`follow_directory_symlink`|Považovat za symbolické odkazy k adresářům skutečné adresáře.|

## <a name="file_type"></a>  file_type –

Výčet pro typy souborů. Podporované hodnoty jsou standardní, adresář, not_found a neznámý.

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
|`none`|0|Představuje soubor, který nemá žádné atributy typu. (Není podporováno.)|
|`regular`|1|Představuje soubor konvenční disku.|
|`directory`|2|Představuje adresáře.|
|`symlink`|3|Představuje symbolický odkaz. (Není podporováno.)|
|`block`|4|Představuje soubor speciálních bloku na systémech UNIX. (Není podporováno.)|
|`character`|5|Představuje soubor speciálních znaků v systémech UNIX. (Není podporováno.)|
|`fifo`|6|Představuje soubor FIFO na systémech UNIX. (Není podporováno.)|
|`socket`|7|Představuje soketu v systémech UNIX založené. (Není podporováno.)|
|`unknown`|8|Představuje soubor nelze zjistit jejichž stav.|

## <a name="perms"></a>  oprávnění

Příznaky pro oprávnění k souboru. Podporované hodnoty jsou v podstatě "jen pro čtení" a všechny. Pro soubor jen pro čtení, žádný z * _write bity jsou nastaveny. V opačném případě `all` nastaven bit (0x0777).

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

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
