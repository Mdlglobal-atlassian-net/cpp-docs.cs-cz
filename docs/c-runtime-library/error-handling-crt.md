---
title: Zpracování chyb (CRT)
ms.date: 11/04/2016
f1_keywords:
- c.errors
helpviewer_keywords:
- error handling, C routines for
- logic errors
- error handling, library routines
- testing, for program errors
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
ms.openlocfilehash: 7b3a5676c9297b1d7805f92b3a15cc71518ecd65
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289868"
---
# <a name="error-handling-crt"></a>Zpracování chyb (CRT)

Tyto rutiny použijte ke zpracování chyby programu.

## <a name="error-handling-routines"></a>Rutiny zpracování chyb

|Rutina|Použití|
|-------------|---------|
|[vyhodnocení](../c-runtime-library/reference/assert-macro-assert-wassert.md) – makro|Test pro programování logických chyb; k dispozici ve verzi a ladicí verze knihovny run-time.|
|[_ASSERT, _asserte –](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra|Podobně jako **vyhodnocení**, ale k dispozici pouze v ladicí verze knihovny run-time.|
|[clearerr](../c-runtime-library/reference/clearerr.md)|Resetování označení chyb. Volání **rewind** nebo zavření datového proudu také obnoví označení chyb.|
|[_eof](../c-runtime-library/reference/eof.md)|Kontrola pro konec souboru začal v vstupně-výstupních operací nízké úrovně.|
|[feof](../c-runtime-library/reference/feof.md)|Test konce souboru. Konec souboru se také uvedeno, kdy **_read** vrátí hodnotu 0.|
|[ferror](../c-runtime-library/reference/ferror.md)|Testování chyb datového proudu vstupně-výstupních operací.|
|[_RPT, _RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) makra|Vygenerovat sestavu podobný **printf**, ale k dispozici pouze v ladicí verze knihovny run-time.|
|[_set_error_mode](../c-runtime-library/reference/set-error-mode.md)|Upraví **__error_mode** určit jiné než výchozí umístění, kde C běhu zapíše chybovou zprávu pro chybu, která bude pravděpodobně ukončit program.|
|[_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|Nastaví obslužnou rutinu volání čistě virtuální funkce.|

## <a name="see-also"></a>Viz také:

- [Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)
