---
title: Zpracování souborů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.files
dev_langs:
- C++
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a54e0ba354e76996d03503e116008aa200b0905b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199354"
---
# <a name="file-handling"></a>Zpracování souborů

Pomocí těchto rutin můžete vytvořit, odstranit a pracovat se soubory a nastavit a zkontrolovat oprávnění přístupu k souborům.

Běhové knihovny jazyka C mají 512 omezení pro počet souborů, které se dají otevřít v daný okamžik. Došlo k pokusu o otevření více než maximální počet popisovače souborů nebo datových proudů souboru způsobuje selhání programu. Použití [_setmaxstdio –](../c-runtime-library/reference/setmaxstdio.md) toto číslo.

## <a name="file-handling-routines-file-descriptor"></a>Rutiny zpracování souborů (popisovač souboru)

Tyto rutiny pracují se soubory určené popisovač souboru.

|Rutina|Použití|
|-------------|---------|
|[_chsize –](../c-runtime-library/reference/chsize.md),[_chsize_s –](../c-runtime-library/reference/chsize-s.md)|Změnit velikost souboru|
|[_filelength, _filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|Získání délky souboru|
|[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|Získání informací o stavu souboru na popisovač|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Popisovač návratový souboru operačního systému přidružený k existující popisovač souboru za běhu C|
|[_isatty](../c-runtime-library/reference/isatty.md)|Vyhledat znakovým zařízením|
|[_locking](../c-runtime-library/reference/locking.md)|Uzamčení oblasti souboru|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Popisovač souboru za běhu C přidružit existující popisovač souboru operačního systému|
|[_setmode](../c-runtime-library/reference/setmode.md)|Nastavit režim překladu souboru|

## <a name="file-handling-routines-path-or-filename"></a>Rutiny zpracování souboru (cestu nebo název souboru)

Tyto rutiny pracují se soubory určené cestu nebo název souboru.

|Rutina|Použití|
|-------------|---------|
|[_přístupový _waccess –](../c-runtime-library/reference/access-waccess.md), [_access_s – _waccess_s –](../c-runtime-library/reference/access-s-waccess-s.md)|Zkontrolujte nastavení soubor permission|
|[_chmod, _wchmod](../c-runtime-library/reference/chmod-wchmod.md)|Změnit oprávnění souboru nastavení|
|[_fullpath, _wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|Rozbalte relativní cestu na jeho název absolutní cesta|
|[_makepath – _wmakepath –](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s – _wmakepath_s –](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|Sloučit součásti cesty do jednoho, úplnou cestu|
|[_mktemp – _wmktemp –](../c-runtime-library/reference/mktemp-wmktemp.md), [_mktemp_s – _wmktemp_s –](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|Vytvořit jedinečný název souboru|
|[remove, _wremove](../c-runtime-library/reference/remove-wremove.md)|Odstranit soubor|
|[rename, _wrename](../c-runtime-library/reference/rename-wrename.md)|Přejmenovat soubor|
|[_splitpath – _wsplitpath –](../c-runtime-library/reference/splitpath-wsplitpath.md), [_splitpath_s – _wsplitpath_s –](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|Parsovat cestu do komponenty|
|[_stat, _stat64, _stati64, _wstat –, _wstat64, _wstati64](../c-runtime-library/reference/stat-functions.md)|Umožňuje získat informace o stavu souboru s názvem souboru|
|[_umask –](../c-runtime-library/reference/umask.md), [_umask_s –](../c-runtime-library/reference/umask-s.md)|Nastavit výchozí oprávnění maska pro nové soubory vytvořené programem|
|[_unlink, _wunlink](../c-runtime-library/reference/unlink-wunlink.md)|Odstranit soubor|

## <a name="file-handling-routines-open-file"></a>Rutiny zpracování souborů (otevřít soubor)

Tyto rutiny otevírání souborů.

|Rutina|Použití|
|-------------|---------|
|[fopen _wfopen –](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s _wfopen_s –](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otevře soubor a vrátí ukazatel na otevřený soubor.|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Otevřít datový proud s sdílení souborů a vrátí ukazatel na otevřený soubor.|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Otevře soubor a vrátí popisovač souboru otevřený soubor.|
|[_sopen _wsopen –](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s – _wsopen_s –](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otevřete soubor pomocí sdílení souborů a vrátí popisovač souboru pro otevření souboru.|
|[_pipe](../c-runtime-library/reference/pipe.md)|Vytvoří kanál pro čtení a zápis.|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s – _wfreopen_s –](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Změnit přiřazení ukazatel souboru.|

Tyto rutiny představují způsob, jak změnit reprezentaci souboru mezi `FILE` strukturu, popisovač souboru a popisovač souboru Win32.

|Rutina|Použití|
|-------------|---------|
|[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Přidruží datového proudu souboru, který byl dříve otevřen pro vstupně-výstupních operací nízké úrovně a vrací ukazatel na Otevřít datový proud.|
|[_fileno](../c-runtime-library/reference/fileno.md)|Získá popisovač souboru přidruženého datového proudu.|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Popisovač návratový souboru operačního systému přidružený k existující popisovač souboru za běhu C|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Přidruží popisovač souboru za běhu C existující popisovač souboru operačního systému.|

 Následující funkce Win32 také otevřít soubory a kanály:

- [CreateFile](/windows/desktop/api/fileapi/nf-fileapi-createfilea)

- [CreatePipe](https://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)

- [CreateNamedPipe](/windows/desktop/api/winbase/nf-winbase-createnamedpipea)

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Ovládací prvek adresáře](../c-runtime-library/directory-control.md)<br/>
[Systémová volání](../c-runtime-library/system-calls.md)<br/>
