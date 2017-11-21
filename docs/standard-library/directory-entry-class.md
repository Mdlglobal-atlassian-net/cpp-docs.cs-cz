---
title: "directory_entry – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
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
ms.openlocfilehash: f79999e2913bb0058a62f112d4450e89daf456e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="directoryentry-class"></a>directory_entry – třída
Popisuje objekt, který je vrácen rutinou `*X`, kde *X* je [directory_iterator](../standard-library/directory-iterator-class.md) nebo [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class directory_entry;  
```  
  
## <a name="remarks"></a>Poznámky  
 Třída uloží objekt typu [cestu](../standard-library/path-class.md). Uložených `path` může být instance [path – třída](../standard-library/path-class.md) nebo typu, který je odvozený od `path`. Také ukládá dvě [file_type](../standard-library/filesystem-enumerations.md#file_type) hodnoty; ten, který představuje známým o stavu názvu uloženého souboru a jiné, který představuje známým o stavu symbolický odkaz názvu souboru.  
  
 Další informace a příklady kódu najdete v tématu [navigační systému souborů (C++)](../standard-library/file-system-navigation.md).  
  
## <a name="assign"></a>přiřazení  
  
```  
void assign(const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 Členská funkce pval přiřadí cesta, stat k mystat a symstat k mysymstat.  
  
## <a name="directoryentry"></a>directory_entry  
  
```  
directory_entry() = default;  
directory_entry(const directory_entry&) = default;  
directory_entry(directory_entry&&) noexcept = default;  
explicit directory_entry(const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 Uvedena konstruktory chovat podle očekávání. Čtvrtý konstruktor inicializuje cesta k pval, mystat k stat_arg a mysymstat k symstat_arg.  
  
## <a name="operator"></a>operator!=  
  
```  
bool operator!=(const directory_entry& right) const noexcept;  
```  
  
 Členská funkce vrátí! (* to == vpravo).  
  
## <a name="operator"></a>operator=  
  
```  
directory_entry& operator=(const directory_entry&) = default;  
directory_entry& operator=(directory_entry&&) noexcept = default;  
```  
  
 Operátory přiřazení uvedena člen chovat podle očekávání.  
  
## <a name="operator"></a>operator==  
  
```  
bool operator==(const directory_entry& right) const noexcept;  
```  
  
 Členská funkce vrátí cesta == right.mypath.  
  
## <a name="operatorlt"></a>operátor&lt;  
  
```  
bool operator<(const directory_entry& right) const noexcept;  
```  
  
 Členská funkce vrátí cesta &lt; right.mypath.  
  
## <a name="operatorlt"></a>operátor&lt;=  
  
```  
bool operator&lt;=(const directory_entry& right) const noexcept;  
```  
  
 Členská funkce vrátí! (vpravo \< * to).  
  
## <a name="operatorgt"></a>operátor&gt;  
  
```  
bool operator&gt;(const directory_entry& right) const noexcept;  
```  
  
 Členská funkce vrátí právo \< * to.  
  
## <a name="operatorgt"></a>operátor&gt;=  
  
```  
bool operator&gt;=(const directory_entry& right) const noexcept;  
```  
  
 Členská funkce vrátí! (* to \< vpravo).  
  
## <a name="operator-const-pathtype"></a>operátor – konstanta path_type &  
  
``` 
 operator const std::experimental::filesystem::path&() const; 
```  
  
 Operátor členů vrátí cesta.  
  
## <a name="path"></a>cesta  
  
```  
const std::experimental::filesystem::path& path() const noexcept;  
```  
  
 Členská funkce vrátí cesta.  
  
## <a name="replacefilename"></a>replace_filename  
  
```  
void replace_filename(
    const std::experimental::filesystem::path& pval,  
    file_status stat_arg = file_status(),  
    file_status symstat_arg = file_status());
```  
  
 Členská funkce nahradí mypath.parent_path() cesta / pval mystat s stat_arg a mysymstat s symstat_arg  
  
## <a name="status"></a>stav  
  
```  
file_status status() const; 
file_status status(error_code& ec) const noexcept;  
```  
  
 Obě členské funkce vrátí mystat pravděpodobně nejprve změnit takto:  
  
1.  Pokud status_known(mystat) pak neprovede žádnou akci.  
  
2.  Jinak pokud! status_known(mysymstat) & &! is_symlink(mysymstat) pak mystat = mysymstat.  
  
## <a name="symlinkstatus"></a>symlink_status –  
  
```  
file_status symlink_status() const; 
file_status symlink_status(error_code& ec) const noexcept;  
```  
  
 Obě členské funkce vrátí mysymstat pravděpodobně nejprve změnit jako status_known(mysymstat) způsobem: Pokud potom nic nestane. Jinak hodnota mysymstat = symlink_status(mypval).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<experimentální nebo systému souborů&gt;  
  
 **Namespace:** std::experimental::filesystem  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<systém souborů&gt;](../standard-library/filesystem.md)

