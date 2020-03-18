---
title: Zpracování chyb (CRT)
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, C routines for
- logic errors
- error handling, library routines
- testing, for program errors
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
ms.openlocfilehash: d38aaf76a4901b12290782957db90049d815d278
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443317"
---
# <a name="error-handling-crt"></a>Zpracování chyb (CRT)

Pomocí těchto rutin můžete zpracovat chyby programu.

## <a name="error-handling-routines"></a>Rutiny zpracování chyb

|Rutina|Použití|
|-------------|---------|
|[Assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) – makro|Testování pro programové chyby logiky; k dispozici ve verzích pro vydání a ladění v běhové knihovně.|
|[_ASSERT, _ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) maker|Podobný jako **Assert**, ale je k dispozici pouze v ladicích verzích knihovny run-time.|
|[clearerr](../c-runtime-library/reference/clearerr.md)|Resetovat indikátor chyby. Volání metody **Rewind** nebo zavření datového proudu také obnoví indikátor chyby.|
|[_eof](../c-runtime-library/reference/eof.md)|Kontroluje konec souboru v/v nízké úrovně.|
|[feof](../c-runtime-library/reference/feof.md)|Test na konec souboru. Konec souboru je také označen, když **_read** vrátí hodnotu 0.|
|[ferror](../c-runtime-library/reference/ferror.md)|Testování chyb v/v streamování|
|[_RPT, _RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) maker|Vygenerujte sestavu podobnou **printf**, ale pouze k dispozici v ladicích verzích knihovny run-time.|
|[_set_error_mode](../c-runtime-library/reference/set-error-mode.md)|Upraví **__error_mode** k určení nevýchozího umístění, kde doba běhu jazyka C zapíše chybovou zprávu pro chybu, která bude pravděpodobně končit programem.|
|[_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|Nastaví obslužnou rutinu pro volání čistě virtuální funkce.|

## <a name="see-also"></a>Viz také

- [Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)
