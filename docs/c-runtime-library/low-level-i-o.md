---
title: I/O nízké úrovně | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0da1e604a901c09897c8b504d7fbdbf41057af37
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="low-level-io"></a>I/O nízké úrovně

Tyto funkce vyvolání operačního systému přímo pro operaci nižší úrovni než poskytované datového proudu vstupně-výstupní operace. Nízké úrovně vstup a výstup volání provést vyrovnávací paměti nebo formát data.

 Nízké úrovně rutiny mají přístup k standardní datové proudy otevřít při spuštění programu pomocí následující předdefinované soubor popisovače.

|Stream|Popisovače souborů|
|------------|---------------------|
|**stdin –**|0|
|**STDOUT**|1|
|**STDERR**|2|

 Sada rutiny nízké úrovně vstupně-výstupních operací [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) globální proměnná, když dojde k chybě. Musí zahrnovat STDIO. H pouze v případě, že aplikace vyžaduje konstanta, která je definována v STDIO použijete funkce na nižší úrovni. H, jako je například indikátoru end souborového (**EOF**).

## <a name="low-level-io-functions"></a>Funkce vstupně-výstupní operace nízké úrovně

|Funkce|Použití|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|Zavřete soubor|
|[_commit](../c-runtime-library/reference/commit.md)|Vyprázdnění souborů na disk|
|[_creat, _wcreat](../c-runtime-library/reference/creat-wcreat.md)|Vytvoření souboru|
|[_dup –](../c-runtime-library/reference/dup-dup2.md)|Návratový další dostupné sdílené popisovač pro danou souboru|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|Vytvořit druhý popisovač pro danou souboru|
|[_eof](../c-runtime-library/reference/eof.md)|Test pro konec souboru|
|[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|Změna umístění souboru ukazatel na zadané umístění|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Otevřete soubor|
|[_read](../c-runtime-library/reference/read.md)|Čtení dat ze souboru|
|[_sopen –, _wsopen –](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s –, _wsopen_s –](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otevřete soubor pro sdílení souborů|
|[_tell, _telli64](../c-runtime-library/reference/tell-telli64.md)|Získat aktuální pozici ukazatele souboru|
|[_umask –](../c-runtime-library/reference/umask.md), [_umask_s –](../c-runtime-library/reference/umask-s.md)|Nastavení oprávnění souborů masky|
|[_write](../c-runtime-library/reference/write.md)|Zapisovat data do souboru|

 **_dup –** a **_dup2 –** jsou obvykle používány pro přidružení předdefinovaného souboru popisovače různých souborů.

## <a name="see-also"></a>Viz také

[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
 [Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
 [Systémová volání](../c-runtime-library/system-calls.md)<br/>
