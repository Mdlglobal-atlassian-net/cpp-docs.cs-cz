---
title: "Zpracování souborů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.files
dev_langs: C++
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e35d3f9a248d280f4ba617da89eb3993414a525
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="file-handling"></a>Zpracování souborů
Tyto rutiny použijte k vytvoření, odstranění a pracovat se soubory a k nastavení a zkontrolujte oprávnění pro přístup k souborům.  
  
 Běhové knihovny jazyka C mít 512 limit pro počet souborů, které lze otevřít v daném okamžiku. Došlo k pokusu o otevření více než maximální počet popisovačů souborů nebo souborů datových proudů způsobí selhání programu. Použití [_setmaxstdio –](../c-runtime-library/reference/setmaxstdio.md) Chcete-li změnit toto číslo.  
  
### <a name="file-handling-routines-file-descriptor"></a>Rutiny zpracování souborů (popisovače souborů)  
  
 Tyto rutiny pracovat soubory určené, které popisovače souborů.  
  
|Rutina|Použití|  
|-------------|---------|  
|[_chsize –](../c-runtime-library/reference/chsize.md),[_chsize_s –](../c-runtime-library/reference/chsize-s.md)|Změnit velikost souboru|  
|[_filelength –, _filelengthi64 –](../c-runtime-library/reference/filelength-filelengthi64.md)|Získat délku souboru|  
|[_fstat –, _fstat32 –, _fstat64 –, _fstati64 –, _fstat32i64 –, _fstat64i32 –](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|Získat stav souboru informace o popisovač|  
|[_get_osfhandle –](../c-runtime-library/reference/get-osfhandle.md)|Manipulační program souboru návratový operační systém přidružený existující popisovače souborů běhu C|  
|[_isatty –](../c-runtime-library/reference/isatty.md)|Kontrola znakových zařízení|  
|[_locking –](../c-runtime-library/reference/locking.md)|Oblasti zámek souboru|  
|[_open_osfhandle –](../c-runtime-library/reference/open-osfhandle.md)|Popisovače souborů běhu C přidružit existující popisovač souboru operačního systému|  
|[_setmode –](../c-runtime-library/reference/setmode.md)|Nastavit režim překladu souboru|  
  
### <a name="file-handling-routines-path-or-filename"></a>Rutiny zpracování souborů (cesta nebo název souboru)  
  
 Tyto rutiny pracovat soubory zadaná cesta nebo název souboru.  
  
|Rutina|Použití|  
|-------------|---------|  
|[_access –, _waccess –](../c-runtime-library/reference/access-waccess.md), [_access_s –, _waccess_s –](../c-runtime-library/reference/access-s-waccess-s.md)|Zkontrolujte nastavení oprávnění souborů|  
|[_chmod –, _wchmod –](../c-runtime-library/reference/chmod-wchmod.md)|Změňte nastavení oprávnění souborů|  
|[_fullpath –, _wfullpath –](../c-runtime-library/reference/fullpath-wfullpath.md)|Rozbalte relativní cesta k jeho název absolutní cesty|  
|[_makepath –, _wmakepath –](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s –, _wmakepath_s –](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|Sloučit komponenty cesty do jednoho, úplná cesta|  
|[_mktemp –, _wmktemp –](../c-runtime-library/reference/mktemp-wmktemp.md), [_mktemp_s –, _wmktemp_s –](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|Vytvořit jedinečný název souboru|  
|[odebrat, _wremove –](../c-runtime-library/reference/remove-wremove.md)|Odstranit soubor|  
|[přejmenování, _wrename –](../c-runtime-library/reference/rename-wrename.md)|Přejmenovat soubor|  
|[_splitpath –, _wsplitpath –](../c-runtime-library/reference/splitpath-wsplitpath.md), [_splitpath_s –, _wsplitpath_s –](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|Analyzovat cestu do komponenty|  
|[_stat –, _stat64 –, _stati64 –, _wstat –, _wstat64 –, _wstati64 –](../c-runtime-library/reference/stat-functions.md)|Získat stav souboru informace v souboru s názvem|  
|[_umask –](../c-runtime-library/reference/umask.md), [_umask_s –](../c-runtime-library/reference/umask-s.md)|Nastavit výchozí masku oprávnění pro nové soubory vytvořené programem|  
|[_unlink –, _wunlink –](../c-runtime-library/reference/unlink-wunlink.md)|Odstranit soubor|  
  
### <a name="file-handling-routines-open-file"></a>Rutiny zpracování souborů (otevřete soubor)  
  
 Tyto rutiny otevřít soubory.  
  
|Rutina|Použití|  
|-------------|---------|  
|[fopen –, _wfopen –](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otevře soubor a vrátí ukazatel k otevření souboru.|  
|[_fsopen –, _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md)|Otevřít datový proud s sdílení souborů a vrací ukazatel na otevření souboru.|  
|[_Otevřít _wopen –](../c-runtime-library/reference/open-wopen.md)|Otevře soubor a vrátí otevřený soubor popisovače souborů.|  
|[_sopen –, _wsopen –](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s –, _wsopen_s –](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otevřete soubor s sdílení souborů a k otevření souboru, vrátí se popisovač souboru.|  
|[_pipe –](../c-runtime-library/reference/pipe.md)|Vytvoří kanálu pro čtení a zápis.|  
|[freopen –, _wfreopen –](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s –, _wfreopen_s –](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Přiřadit ukazatele souboru.|  
  
 Tyto rutiny poskytnout způsob, jak změnit reprezentace souboru mezi `FILE` strukturu, popisovače souborů a popisovač souboru Win32.  
  
|Rutina|Použití|  
|-------------|---------|  
|[_fdopen –, _wfdopen –](../c-runtime-library/reference/fdopen-wfdopen.md)|Přidruží datového proudu souboru, který byl dříve otevřen pro nižší úroveň vstupně-výstupních operací a vrací ukazatel na Otevřít datový proud.|  
|[_fileno –](../c-runtime-library/reference/fileno.md)|Získá popisovače souborů, které jsou přidružené k datového proudu.|  
|[_get_osfhandle –](../c-runtime-library/reference/get-osfhandle.md)|Manipulační program souboru návratový operační systém přidružený existující popisovače souborů běhu C|  
|[_open_osfhandle –](../c-runtime-library/reference/open-osfhandle.md)|Přidruží popisovač soubor spouští za běhu C popisovač existující soubor operačního systému.|  
  
 Následující funkce Win32 také otevřít soubory a kanály:  
  
-   [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858.aspx)  
  
-   [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)  
  
-   [CreateNamedPipe](http://msdn.microsoft.com/library/windows/desktop/aa365150.aspx)  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)   
 [Ovládací prvek adresáře](../c-runtime-library/directory-control.md)   
 [Systémová volání](../c-runtime-library/system-calls.md)