---
title: I/O nízké úrovně
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
ms.openlocfilehash: acf07682e9045800bb04aa4c9d6abc5ae4376280
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443102"
---
# <a name="low-level-io"></a>I/O nízké úrovně

Tyto funkce vyvolají operační systém přímo pro operaci nižší úrovně, než která je poskytována v/v datového proudu. Vstupní a výstupní volání nízké úrovně neukládají do vyrovnávací paměti nebo formátují data.

Rutiny nízké úrovně mají přístup ke standardním datovým proudům otevřeným při spuštění programu pomocí následujících předdefinovaných popisovačů souborů.

|Datový proud|Popisovač souboru|
|------------|---------------------|
|**standardního**|0|
|**STDOUT**|1|
|**stderr**|2|

Rutiny I/O nízké úrovně nastaví globální proměnnou [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) , když dojde k chybě. Musíte zahrnout STDIO. H při použití funkcí nízké úrovně pouze v případě, že program vyžaduje konstantu, která je definována v STDIO. H, jako je například indikátor konce souboru (**EOF**).

## <a name="low-level-io-functions"></a>Vstupně-výstupní funkce nízké úrovně

|Funkce|Použití|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|Zavřít soubor|
|[_commit](../c-runtime-library/reference/commit.md)|Vyprázdnit soubor na disk|
|[_creat, _wcreat](../c-runtime-library/reference/creat-wcreat.md)|Vytvořit soubor|
|[_dup](../c-runtime-library/reference/dup-dup2.md)|Vrátit další dostupný popisovač souboru pro daný soubor|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|Vytvořit druhý popisovač pro daný soubor|
|[_eof](../c-runtime-library/reference/eof.md)|Test konce souboru|
|[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|Změnit umístění ukazatele na soubor do daného umístění|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Otevřít soubor|
|[_read](../c-runtime-library/reference/read.md)|Číst data ze souboru|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otevřít soubor pro sdílení souborů|
|[_tell, _telli64](../c-runtime-library/reference/tell-telli64.md)|Získá aktuální pozici ukazatele na soubor.|
|[_umask](../c-runtime-library/reference/umask.md) [_umask_s](../c-runtime-library/reference/umask-s.md)|Nastavit soubor – maska oprávnění|
|[_write](../c-runtime-library/reference/write.md)|Zapsat data do souboru|

**_dup** a **_dup2** se obvykle používají k přidružení předdefinovaných popisovačů souborů k různým souborům.

## <a name="see-also"></a>Viz také

[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Systémová volání](../c-runtime-library/system-calls.md)<br/>
