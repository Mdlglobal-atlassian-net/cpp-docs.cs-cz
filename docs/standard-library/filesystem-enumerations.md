---
title: "&lt;FileSystem&gt; výčty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6a6d7dcb0e0b0a8e655acbda0624f7fa5b70a8a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;FileSystem&gt; výčty
Toto téma popisuje výčty v hlavičce systému souborů.

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<experimentální/filesystem >    
 **Namespace:** std::experimental::filesystem  

##  <a name="copy_options"></a>  copy_options
Výčet hodnot maskování bitů, které se používá s [kopie](http://msdn.microsoft.com/en-us/4af7a9b0-8861-45ed-b84e-0307f0669d60) a [copy_file –](http://msdn.microsoft.com/en-us/4af7a9b0-8861-45ed-b84e-0307f0669d60) funkce pro určení chování.  
  
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
|`skip_existing`|Pokud soubor již existuje, nekopírovat Neoznamovat k chybě.|  
|`overwrite_existing`|Soubor přepište, pokud již existuje.|  
|`update_existing`|Soubor přepište, pokud již existuje a je starší než nahrazení.|  
|`recursive`|Rekurzivnímu kopírování podadresářů a jejich obsah.|  
|`copy_symlinks`|Zkopírujte symbolické odkazy jako symbolické odkazy, namísto kopírování souborů, které odkazují.|  
|`skip_symlinks`|Ignorujte symbolické odkazy.|  
|`directories_only`|Pouze iterace v adresářích, ignorovat soubory.|  
|`create_symlinks`|Ujistěte se, symbolické odkazy místo kopírování souborů. Absolutní cesta musí být použít jako zdrojovou cestu, pokud cíl je to aktuální adresář.|  
|`create_hard_links`|Ujistěte se, pevné odkazy místo kopírování souborů.|  
  

##  <a name="directory_options"></a> directory_options
Určuje, jestli podle symbolické odkazy na adresáře nebo je ignorovat.  
  
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
|`none`|Výchozí chování: Ignorovat symbolické odkazy na adresáře. Bylo odepřeno oprávnění je chyba.|  
|`follow_directory_symlink`|Považovat za symbolické odkazy na adresáře skutečné adresáře.|  
  
##  <a name="file_type"></a>  file_type
Výčet pro typy souborů. Podporované hodnoty jsou regular, adresář, not_found a neznámý.  
  
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
|`directory`|2|Představuje adresář.|  
|`symlink`|3|Představuje symbolický odkaz. (Není podporováno.)|  
|`block`|4|Představuje soubor zvláštní bloku v systémech UNIX. (Není podporováno.)|  
|`character`|5|Představuje soubor zvláštní znak v systémech UNIX. (Není podporováno.)|  
|`fifo`|6|Představuje soubor FIFO v systémech UNIX. (Není podporováno.)|  
|`socket`|7|Představuje soketu v systémech UNIX na základě. (Není podporováno.)|  
|`unknown`|8|Představuje soubor, jejichž stav nelze určit.|  
  
##  <a name="perms"></a>  oprávnění
Příznaky pro oprávnění k souboru. Podporované hodnoty jsou v podstatě "jen pro čtení" a všechny. Pro soubor určený jen pro čtení, žádný z * jsou nastaveny _Write – bits. V opačném případě `all` je nastaven bit (0x0777).  
  
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
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem>](../standard-library/filesystem.md)

