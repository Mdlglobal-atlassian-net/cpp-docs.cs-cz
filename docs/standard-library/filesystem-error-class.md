---
title: "filesystem_error – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: filesystem/std::experimental::filesystem::filesystem_error
dev_langs: C++
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0012a895dbda27ce26d50ae49b3752d13963a89f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="filesystemerror-class"></a>filesystem_error – třída
Základní třída pro všechny výjimky, které jsou vyvolány nahlásit nízké úrovně systému přetečení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class filesystem_error    : public system_error;  
```  
  
## <a name="remarks"></a>Poznámky  
 Třída slouží jako základní třída pro všechny výjimky vydané nahlásit chybu v \<filesystem > funkce. Objekt typu řetězec, s názvem mymesg sem pro účely budeme v něm uložena. Ukládá také dva objekty typ cesty, jako mypval1 a mypval2.  
  
## <a name="filesystemerrorfilesystemerror"></a>filesystem_error::filesystem_error –  
  
```  
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,  
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,  
    const path& pval1,
    const path& pval2,
    error_code ec);
```  
  
 První konstruktoru vytvoří jeho zprávu od what_arg a ES. Druhý konstruktor vytvoří také jeho zprávu od pval1, který je uložený v mypval1. Třetí konstruktoru vytvoří také jeho zprávy z pval1, který je uložený v mypval1, a z pval2, který je uložený v mypval2.  
  
## <a name="filesystemerrorpath1"></a>filesystem_error::path1  
  
```  
const path& path1() const noexcept;  
```  
  
 Vrátí mypval1 – členská funkce  
  
## <a name="filesystemerrorpath2"></a>filesystem_error::path2  
  
```  
const path& path2() const noexcept;  
```  
  
 Vrátí mypval2 – členská funkce  
  
## <a name="filesystemerrorwhat"></a>filesystem_error::What  
  
```  
const char *what() const noexcept;  
```  
  
 Členská funkce vrátí ukazatel NTBS, pokud možno skládá z runtime_error::what(), system_error::what(), mymesg, mypval1.native_string() a mypval2.native_string().  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<filesystem >  
  
 **Namespace:** std::experimental::filesystem  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [system_error – třída](../standard-library/system-error-class.md)   
 [\<FileSystem >](../standard-library/filesystem.md)   
 [\<Výjimka >](../standard-library/exception.md)

