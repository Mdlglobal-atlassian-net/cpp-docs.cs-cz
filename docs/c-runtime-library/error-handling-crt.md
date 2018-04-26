---
title: Zpracování chyb (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.errors
dev_langs:
- C++
helpviewer_keywords:
- error handling, C routines for
- logic errors
- error handling, library routines
- testing, for program errors
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5cb2c46318cc64403c51d5c6c751ec77897e97f2
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="error-handling-crt"></a>Zpracování chyb (CRT)

Použijte tyto rutiny pro zpracování chyby programu.

## <a name="error-handling-routines"></a>Rutiny zpracování chyb

|Rutina|Použití|
|-------------|---------|
|[Assert –](../c-runtime-library/reference/assert-macro-assert-wassert.md) – makro|Test pro programování logické chyby; k dispozici ve verzi a ladění verze běhové knihovny.|
|[_ASSERT, _asserte –](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra|Podobně jako **assert**, ale k dispozici pouze ve verzích ladicí běhové knihovny.|
|[clearerr](../c-runtime-library/reference/clearerr.md)|Resetování označení chyb. Volání metody **rewind** nebo ukončování datového proudu také obnoví označení chyb.|
|[_eof](../c-runtime-library/reference/eof.md)|Zkontrolujte, zda konec souboru v nízké úrovně vstupně-výstupních operací.|
|[feof](../c-runtime-library/reference/feof.md)|Test pro konec souboru. Konec souboru je také uvedeno, kdy **_Zobrazit** vrátí hodnotu 0.|
|[ferror](../c-runtime-library/reference/ferror.md)|Testování pro datový proud vstupně-výstupní chyby.|
|[_RPT, _RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) makra|Vygenerování sestavy podobná **printf**, ale k dispozici pouze ve verzích ladicí běhové knihovny.|
|[_set_error_mode](../c-runtime-library/reference/set-error-mode.md)|Upraví **__error_mode** určit jiné než výchozí umístění, kde C běh zapíše chybovou zprávu pro chybu, která se pravděpodobně ukončí program.|
|[_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|Nastaví obslužnou rutinu pro volání čistý virtuální funkce.|

## <a name="see-also"></a>Viz také

[Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
