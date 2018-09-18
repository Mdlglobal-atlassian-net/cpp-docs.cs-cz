---
title: I/O nízké úrovně | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d263d1d61a6dcc6921d6918db2b89386e918551
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018311"
---
# <a name="low-level-io"></a>I/O nízké úrovně

Tyto funkce vyvolají operačního systému přímo pro operaci nižší úrovně, než poskytuje datový proud vstupně-výstupních operací. Nižší vstupní a výstupní vyrovnávací paměti nebo formátu dat proveďte volání.

Rutiny nízké úrovně můžete přístup z více vláken standardní otevře při spuštění programu pomocí následující předdefinovaných souboru popisovače.

|Stream|Popisovač souboru|
|------------|---------------------|
|**stdin**|0|
|**STDOUT**|1|
|**STDERR**|2|

Sada rutiny nízké úrovně vstupně-výstupních operací [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) globální proměnné, když dojde k chybě. Je nutné uvést STDIO. H pouze v případě, že váš program vyžaduje konstantu, která je definována v STDIO použijete funkce nízké úrovně. H, jako je například indikátor konce souboru (**EOF**).

## <a name="low-level-io-functions"></a>I/O nízké úrovně funkce

|Funkce|Použití|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|Zavřít soubor|
|[_commit](../c-runtime-library/reference/commit.md)|Vyprázdnění souboru na disk|
|[_creat, _wcreat](../c-runtime-library/reference/creat-wcreat.md)|Vytvoření souboru|
|[_dup –](../c-runtime-library/reference/dup-dup2.md)|Návratový další popisovače souborů pro daný soubor|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|Vytvořte druhý popisovač pro danou souboru|
|[_eof](../c-runtime-library/reference/eof.md)|Test pro konec souboru|
|[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|Změna umístění souboru ukazatel na daném umístění|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Otevřít soubor|
|[_read](../c-runtime-library/reference/read.md)|Čtení dat ze souboru|
|[_sopen _wsopen –](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s – _wsopen_s –](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otevřít soubor pro sdílení souborů|
|[_tell, _telli64](../c-runtime-library/reference/tell-telli64.md)|Získejte aktuální pozici ukazatele na soubor|
|[_umask –](../c-runtime-library/reference/umask.md), [_umask_s –](../c-runtime-library/reference/umask-s.md)|Nastavení oprávnění souboru masky|
|[_write](../c-runtime-library/reference/write.md)|Zápis dat do souboru|

 **_dup –** a **_dup2 –** jsou obvykle slouží k přidružení předdefinovaného souboru popisovače různé soubory.

## <a name="see-also"></a>Viz také

[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Systémová volání](../c-runtime-library/system-calls.md)<br/>
