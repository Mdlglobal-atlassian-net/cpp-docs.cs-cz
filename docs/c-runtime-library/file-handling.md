---
title: Zpracování souborů
ms.date: 11/04/2016
f1_keywords:
- c.files
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
ms.openlocfilehash: e5e43fe2cfcdfe067833d02bda511e8c9cb944ad
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500102"
---
# <a name="file-handling"></a>Zpracování souborů

Tyto rutiny použijte k vytváření, odstraňování a manipulaci se soubory a k nastavení a kontrole oprávnění k přístupu k souborům.

Běhové knihovny jazyka C mají omezení 512 pro počet souborů, které mohou být v jednom okamžiku otevřeny. Při pokusu o otevření více než maximálního počtu popisovačů souborů nebo datových proudů souborů dojde k chybě programu. Toto číslo můžete změnit pomocí [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) .

## <a name="file-handling-routines-file-descriptor"></a>Rutiny zpracování souborů (popisovač souborů)

Tyto rutiny pracují se soubory, které jsou určené popisovačem souboru.

|Rutina|Použití|
|-------------|---------|
|[_chsize](../c-runtime-library/reference/chsize.md),[_chsize_s](../c-runtime-library/reference/chsize-s.md)|Změnit velikost souboru|
|[_filelength, _filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|Získat délku souboru|
|[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|Získat informace o stavu souboru v popisovači|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Vrátit popisovač souborů operačního systému přidružený ke stávajícímu popisovači souboru jazyka C run-time|
|[_isatty](../c-runtime-library/reference/isatty.md)|Kontrolovat znaková zařízení|
|[_locking](../c-runtime-library/reference/locking.md)|Zamknout oblasti souboru|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Přidružit popisovač běhového souboru jazyka C ke stávajícímu popisovači souborů operačního systému|
|[_setmode](../c-runtime-library/reference/setmode.md)|Nastavit režim překladu souborů|

## <a name="file-handling-routines-path-or-filename"></a>Rutiny zpracování souborů (cesta nebo název souboru)

Tyto rutiny pracují se soubory určenými cestou nebo názvem souboru.

|Rutina|Použití|
|-------------|---------|
|[_access, _waccess](../c-runtime-library/reference/access-waccess.md), [_access_s, _waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|Check File – nastavení oprávnění|
|[_chmod, _wchmod](../c-runtime-library/reference/chmod-wchmod.md)|Změnit nastavení oprávnění souboru|
|[_fullpath, _wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|Rozbalení relativní cesty k jejímu názvu absolutní cesty|
|[_makepath, _wmakepath](../c-runtime-library/reference/makepath-wmakepath.md), [_makepath_s, _wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|Sloučit součásti cest do jedné, úplné cesty|
|[_mktemp, _wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md), [_mktemp_s, _wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|Vytvořit jedinečný název souboru|
|[remove, _wremove](../c-runtime-library/reference/remove-wremove.md)|Odstranit soubor|
|[rename, _wrename](../c-runtime-library/reference/rename-wrename.md)|Přejmenovat soubor|
|[_splitpath, _wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md), [_splitpath_s, _wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|Analyzovat cestu k součástem|
|[_stat, _stat64, _stati64, _wstat, _wstat64, _wstati64](../c-runtime-library/reference/stat-functions.md)|Získat informace o stavu souboru u pojmenovaného souboru|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|Nastavte výchozí masku oprávnění pro nové soubory vytvořené programem.|
|[_unlink, _wunlink](../c-runtime-library/reference/unlink-wunlink.md)|Odstranit soubor|

## <a name="file-handling-routines-open-file"></a>Rutiny zpracování souborů (otevřené soubory)

Tyto rutiny otevírají soubory.

|Rutina|Použití|
|-------------|---------|
|[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Otevře soubor a vrátí ukazatel na otevřený soubor.|
|[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|Otevřete datový proud se sdílením souborů a vrátí ukazatel na otevřený soubor.|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Otevře soubor a vrátí popisovač souboru do otevřeného souboru.|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otevřete soubor se sdílením souborů a v otevřeném souboru vrátí popisovač souboru.|
|[_pipe](../c-runtime-library/reference/pipe.md)|Vytvoří kanál pro čtení a zápis.|
|[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s, _wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Změna přiřazení ukazatele souboru.|

Tyto rutiny poskytují způsob, jak změnit reprezentace souboru mezi `FILE` strukturou, popisovačem souboru a popisovačem souboru Win32.

|Rutina|Použití|
|-------------|---------|
|[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|Přidruží datový proud k souboru, který byl dříve otevřen pro vstupně-výstupní operace nízké úrovně, a vrací ukazatel na otevřený datový proud.|
|[_fileno](../c-runtime-library/reference/fileno.md)|Získá popisovač souboru přidružený ke streamu.|
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|Vrátit popisovač souborů operačního systému přidružený ke stávajícímu popisovači souboru jazyka C run-time|
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|Přidruží popisovač souboru jazyka C za běhu s existujícím popisovačem souborů operačního systému.|

Následující funkce Win32 také otevírají soubory a kanály:

- [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilew)

- [CreatePipe](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe)

- [CreateNamedPipe](/windows/win32/api/winbase/nf-winbase-createnamedpipew)

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Ovládací prvek adresáře](../c-runtime-library/directory-control.md)<br/>
[Systémová volání](../c-runtime-library/system-calls.md)<br/>
