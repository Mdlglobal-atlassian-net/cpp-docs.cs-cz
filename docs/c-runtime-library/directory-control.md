---
title: Ovládací prvek adresáře
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], directory
- directory control routines
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
ms.openlocfilehash: 640ce8a8665936b604c6e8e6270e358a200c880a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438531"
---
# <a name="directory-control"></a>Ovládací prvek adresáře

Tyto rutiny přistupují, upravují a získávají informace o adresářové struktuře.

## <a name="directory-control-routines"></a>Rutiny ovládacího prvku adresář

|Rutina|Použití|
|-------------|---------|
|[_chdir, _wchdir](../c-runtime-library/reference/chdir-wchdir.md)|Změnit aktuální pracovní adresář|
|[_chdrive](../c-runtime-library/reference/chdrive.md)|Změnit aktuální jednotku|
|[_getcwd, _wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|Získat aktuální pracovní adresář pro výchozí jednotku|
|[_getdcwd, _wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|Získá aktuální pracovní adresář pro zadanou jednotku.|
|[_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|Naplní strukturu **_diskfree_t** informacemi o diskové jednotce.|
|[_getdrive](../c-runtime-library/reference/getdrive.md)|Získat aktuální (výchozí) jednotku|
|[_getdrives](../c-runtime-library/reference/getdrives.md)|Vrátí bitovou masku představující aktuálně dostupné diskové jednotky.|
|[_mkdir, _wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|Vytvořit nový adresář|
|[_rmdir, _wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|Odebrat adresář|
|[_searchenv, _wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md), [_searchenv_s _wsearchenv_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|Vyhledat zadaný soubor v zadaných cestách|

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Zpracování souborů](../c-runtime-library/file-handling.md)<br/>
[Systémová volání](../c-runtime-library/system-calls.md)<br/>
