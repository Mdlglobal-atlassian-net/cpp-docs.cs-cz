---
title: "Ovládací prvek adresáře | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.programs
dev_langs: C++
helpviewer_keywords:
- controls [C++], directory
- directory control routines
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 74d0bd9011c77d67383e36b15817a71f853a409b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="directory-control"></a>Ovládací prvek adresáře
Tyto rutiny přístup, upravit a získat informace o strukturu adresáře.  
  
### <a name="directory-control-routines"></a>Rutiny pro ovládací prvek adresáře  
  
|Rutina|Použití|  
|-------------|---------|  
|[_chdir –, _wchdir –](../c-runtime-library/reference/chdir-wchdir.md)|Změnit aktuální pracovní adresář|  
|[_chdrive –](../c-runtime-library/reference/chdrive.md)|Změnit aktuální jednotku|  
|[_getcwd –, _wgetcwd –](../c-runtime-library/reference/getcwd-wgetcwd.md)|Získat aktuální pracovní adresář pro výchozí jednotce|  
|[_getdcwd –, _wgetdcwd –](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|Získat aktuální pracovní adresář pro vybranou jednotku|  
|[_getdiskfree –](../c-runtime-library/reference/getdiskfree.md)|Naplní `_diskfree_t` struktura s informacemi o diskové jednotce.|  
|[_getdrive –](../c-runtime-library/reference/getdrive.md)|Získat aktuální jednotce (výchozí)|  
|[_getdrives –](../c-runtime-library/reference/getdrives.md)|Vrátí bitová maska představující aktuálně k dispozici disky.|  
|[_mkdir –, _wmkdir –](../c-runtime-library/reference/mkdir-wmkdir.md)|Ujistěte se, nový adresář|  
|[_rmdir –, _wrmdir –](../c-runtime-library/reference/rmdir-wrmdir.md)|Odebrat adresář|  
|[_searchenv –, _wsearchenv –](../c-runtime-library/reference/searchenv-wsearchenv.md), [_searchenv_s –, _wsearchenv_s –](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|Vyhledejte daný soubor na zadané cesty|  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)   
 [Zpracování souborů](../c-runtime-library/file-handling.md)   
 [Systémová volání](../c-runtime-library/system-calls.md)