---
title: Ovládací prvek adresáře
ms.date: 11/04/2016
f1_keywords:
- c.programs
helpviewer_keywords:
- controls [C++], directory
- directory control routines
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
ms.openlocfilehash: 327647ee2eee7e149ec0e9ebfc71883a8a3643d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343911"
---
# <a name="directory-control"></a>Ovládací prvek adresáře

Tyto rutiny přístup, upravit a získat informace o struktuře adresářů.

## <a name="directory-control-routines"></a>Rutiny pro ovládací prvek adresáře

|Rutina|Použití|
|-------------|---------|
|[_chdir, _wchdir](../c-runtime-library/reference/chdir-wchdir.md)|Změňte aktuální pracovní adresář|
|[_chdrive](../c-runtime-library/reference/chdrive.md)|Změnit aktuální jednotku|
|[_getcwd, _wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|Získání aktuálního pracovního adresáře pro výchozí jednotka|
|[_getdcwd, _wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|Získat aktuální pracovní adresář pro vybranou jednotku|
|[_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|Naplní **_diskfree_t –** struktura s informacemi o diskové jednotce.|
|[_getdrive](../c-runtime-library/reference/getdrive.md)|Získat aktuální jednotku (výchozí)|
|[_getdrives](../c-runtime-library/reference/getdrives.md)|Vrátí bitová maska představující disky aktuálně k dispozici.|
|[_mkdir, _wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|Vytvořit nový adresář|
|[_rmdir, _wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|Odebrat adresář|
|[_searchenv, _wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md), [_searchenv_s, _wsearchenv_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|Hledání pro daný soubor na zadané cesty|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Zpracování souborů](../c-runtime-library/file-handling.md)<br/>
[Systémová volání](../c-runtime-library/system-calls.md)<br/>
