---
title: Rutiny ladění | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- c.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], runtime routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7637c012b29c89352d62ac470ff635b090b719ad
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="debug-routines"></a>Rutiny ladění

Ladicí verze běhové knihovny jazyka C poskytuje mnoho diagnostické služby, které snazší ladění programů a umožňují vývojářům:

- Krok přímo do běhové funkce během ladění

- Vyřešte kontrolní výrazy, chyb a výjimek

- Přidělení haldy trasování a zabránit nevracení paměti

- Sestava zprávy ladění pro uživatele

## <a name="debug-versions-of-the-c-runtime-library-routines"></a>Ladicí verze rutiny knihovny za běhu C

Pro použití těchto rutin, [_DEBUG –](../c-runtime-library/debug.md) příznak musí být definován. Všechny tyto rutiny nedělat nic prodejní sestavení aplikace. Další informace o tom, jak používat nové rutiny ladění najdete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

|Rutina|Použití|
|-------------|---------|
|[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Vyhodnocení výrazu a generuje sestavy ladění, když je výsledkem FALSE|
|[_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Podobně jako **_ASSERT**, ale zahrnuje selhání výrazu v vygenerovanou sestavu.|
|[_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|Potvrdil integritu bloky paměti přidělené v haldě ladění|
|[_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|Nastaví přerušení.|
|[_CrtDbgReport, _CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|Vygenerování sestavy ladění zprávou uživatele a odeslat zprávu o tři možné cíle|
|[_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|Volání funkce poskytované aplikací pro všechny **_client_block –** typy v haldě|
|[_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|Vypsat všechny bloky paměti v haldě ladění při došlo k úniku velké paměti|
|[_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|Ověřte, zda blok zadaná paměťová se nachází v rámci lokální haldy a že má identifikátor typ bloku haldy platný ladění|
|[_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|Ověřuje, že je zadaný ukazatel v lokální haldy|
|[_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|Ověřte, zda zadaná paměťová rozsah je platný pro čtení a zápis|
|[_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|Získání aktuálního stavu haldy ladění a uložte ho aplikaci zadané **_crtmemstate –** struktura|
|[_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|Porovnání dvou stavů – stav paměti pro významné rozdíly a vrátí výsledky|
|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|Dump informace o objektech v haldě od doby pořízení zadaný kontrolní bod nebo od začátku spuštění programu|
|[_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|Dump informace ze záhlaví ladění stavu zadaná paměťová uživatelem čitelný formuláře|
|[_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|Vrátí bloku přidružené ukazatel bloku haldy ladění daný typ nebo dílčí.|
|[_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|Nainstalovat funkce definované klienta přidělení zapojování do procesu přidělení paměti běhové ladění C|
|[_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|Nastavit zarážky pořadové číslo zadaný objekt přidělení|
|[_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|Načtení nebo změně stavu **_crtdbgflag –** příznak můžete řídit chování přidělení správce halda ladění|
|[_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|Instalace funkce definované aplikací, která je volána pokaždé, když je volána funkce výpis ladění pro výpis **_client_block –** zadejte bloky paměti|
|[_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|Určení souboru nebo datový proud, který se má použít jako cíl pro konkrétní typ sestavy podle **_crtdbgreport –**|
|[_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|Zapojování do ladění C spuštění procesu vytváření sestav nainstalovat klienta definované funkce vytváření sestav|
|[_CrtSetReportHook2, _CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|Instaluje nebo odinstaluje klienta definované funkce vytváření sestav podle zapojování do ladění C spuštění procesu vytváření sestav.|
|[_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|Zadejte obecné příjemcům pro konkrétní typ sestavy generované **_crtdbgreport –**|
|[_RPT&AMP;#91;0,1,2,3,4&AMP;#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Sledovat průběh aplikace pomocí generování sestavy ladění voláním **_crtdbgreport –** s řetězec formátu a proměnný počet argumentů. Poskytuje zdrojové souborové služby a řádku číslo informace.|
|[_RPTF&AMP;#91;0,1,2,3,4&AMP;#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Podobně jako **_rptn –** makra, ale poskytuje číslo zdrojového souboru název a řádek, kde požadavku na sestavu vytvořena|
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Přidělit zadaný počet bloky paměti v haldě s další místo pro hlavičku ladění a přepsání vyrovnávací paměti|
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Změnit velikost zadaný blok paměti v haldě rozšiřování nebo smluvní bloku|
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Volné paměti v haldě blok|
|[_fullpath_dbg, _wfullpath_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|Vytvoření názvu absolutní nebo úplnou cestu pro zadanou cestu relativní název, pomocí [_malloc_dbg –](../c-runtime-library/reference/malloc-dbg.md) přidělit paměť.|[System::IO::file:: vytvořit](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|
|[_getcwd_dbg, _wgetcwd_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|Získání aktuálního pracovního adresáře pomocí [_malloc_dbg –](../c-runtime-library/reference/malloc-dbg.md) přidělit paměť.|
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Přidělit blok paměti v haldě s další místo pro hlavičku ladění a přepsání vyrovnávací paměti|
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Vypočítat velikost bloku paměti v haldě|
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Znovu přidělte zadaný blok paměti v haldě přesunutí nebo změna velikosti bloku|
|[_strdup_dbg, _wcsdup_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|Duplikuje řetězce, pomocí [_malloc_dbg –](../c-runtime-library/reference/malloc-dbg.md) přidělit paměť.|
|[_tempnam_dbg, _wtempnam_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|Generování názvů můžete použít k vytvoření dočasné soubory pomocí [_malloc_dbg –](../c-runtime-library/reference/malloc-dbg.md) přidělit paměť.|

## <a name="c-runtime-routines-that-are-not-available-in-source-code-form"></a>Rutiny C runtime, která nejsou k dispozici v zdrojového kódu formuláře

Ladicí program můžete použít ke kroku prostřednictvím zdrojového kódu pro většinu rutiny C runtime během procesu ladění. Ale Microsoft zvažuje některé technologie, jako vlastní a, tedy neposkytuje zdrojový kód pro podmnožinu těchto rutiny. Většina těchto rutin, patří výjimek nebo skupiny s plovoucí desetinnou čárkou zpracování, ale některých jiných jsou zahrnuty také. Následující tabulka uvádí tyto rutiny.

||||
|-|-|-|
|[ACOS](../c-runtime-library/reference/acos-acosf-acosl.md)|[acosh –](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|[ASIN](../c-runtime-library/reference/asin-asinf-asinl.md)|
|[asinh –](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|[Atan atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[atanh –](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|
|[Besselovy funkce](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[_cabs](../c-runtime-library/reference/cabs.md)|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|
|[_chgsign](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[_control87, _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|
|[copysign –](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[Cos](../c-runtime-library/reference/cos-cosf-cosl.md)|[COSH](../c-runtime-library/reference/cosh-coshf-coshl.md)|
|[Exp](../c-runtime-library/reference/exp-expf.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[_finite –](../c-runtime-library/reference/finite-finitef.md)|
|[Floor](../c-runtime-library/reference/floor-floorf-floorl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[_fpclass –](../c-runtime-library/reference/fpclass-fpclassf.md)|
|[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|[_fpreset](../c-runtime-library/reference/fpreset.md)|[frexp](../c-runtime-library/reference/frexp.md)|
|[_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|
|[Protokolu](../c-runtime-library/reference/log-logf-log10-log10f.md)|[_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|
|[longjmp](../c-runtime-library/reference/longjmp.md)|[_matherr](../c-runtime-library/reference/matherr.md)|[modf –](../c-runtime-library/reference/modf-modff-modfl.md)|
|[_nextafter](../c-runtime-library/reference/nextafter-functions.md)|[Pow](../c-runtime-library/reference/pow-powf-powl.md)|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_scalb](../c-runtime-library/reference/scalb.md)|[scanf_s](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|[Sin](../c-runtime-library/reference/sin-sinf-sinl.md)|
|[SINH](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|[_status87 –, _statusfp –](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|
|[Tan](../c-runtime-library/reference/tan-tanf-tanl.md)|[TANH](../c-runtime-library/reference/tanh-tanhf-tanhl.md)||

I když zdrojový kód je k dispozici pro většinu **printf** a **scanf** rutiny, provádění interního volání do jiné rutiny pro zdroj, který není zadaný kód.

## <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>Rutiny, které se chovají jinak ladění sestavení aplikace

Některé funkce runtime jazyka C a C++ operátory chovat jinak při volání z sestavení ladicí verze aplikace. (Všimněte si, že sestavení ladicí verze aplikace lze provést tak, že buď definujete `_DEBUG` příznak nebo pomocí propojení s verzí ladicí běhové knihovny jazyka C.) Chování rozdíly obvykle obsahovat další funkce nebo informace, které poskytuje rutina pro podporu procesu ladění. Následující tabulka uvádí tyto rutiny.

|||
|-|-|
|C [abort](../c-runtime-library/reference/abort.md) rutiny|C++ [odstranit](../cpp/delete-operator-cpp.md) – operátor|
|C [assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) rutiny|C++ [nové](../cpp/new-operator-cpp.md) – operátor|

## <a name="see-also"></a>Viz také

[Univerzální C runtime rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Kontrola chyb za běhu](../c-runtime-library/run-time-error-checking.md)<br/>
