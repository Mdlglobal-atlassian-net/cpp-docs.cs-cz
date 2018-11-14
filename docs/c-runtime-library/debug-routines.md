---
title: Rutiny ladění
ms.date: 04/10/2018
f1_keywords:
- c.debug
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], runtime routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
ms.openlocfilehash: e1281b578435086dc7de04c7962145c2b265277a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329461"
---
# <a name="debug-routines"></a>Rutiny ladění

Ladicí verze knihovny runtime jazyka C poskytuje mnoho diagnostické služby, které usnadnit ladění aplikací a umožňuje vývojářům:

- Vstoupit přímo do běhové funkce během ladění

- Vyřešit kontrolní výrazy, chyby a výjimky

- Trasování přidělení haldy a prevence úniků paměti

- Ladění zprávy pro uživatele

## <a name="debug-versions-of-the-c-runtime-library-routines"></a>Ladění verzí rutiny knihoven runtime jazyka C

Chcete-li použít tyto rutiny [_DEBUG](../c-runtime-library/debug.md) příznak musí být definován. Všechny tyto rutiny Neprovádět žádnou akci v sestavení prodejní verze aplikace. Další informace o tom, jak pomocí nové rutiny ladění, naleznete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

|Rutina|Použití|
|-------------|---------|
|[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Vyhodnocení výrazu a generuje sestavu ladění, pokud je výsledek FALSE|
|[_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Podobně jako **_ASSERT**, ale zahrnuje selhání výrazu v generované sestavě|
|[_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|Potvrdil integritu bloky paměti přidělené v haldě ladění|
|[_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|Nastaví přerušení.|
|[_CrtDbgReport, _CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|Generovat sestavu ladění se zprávou uživatele a odeslat sestavu do tří možných cílů|
|[_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|Voláním funkce poskytované aplikací pro všechny **_CLIENT_BLOCK** typy v haldě|
|[_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|Všechny bloky paměti v haldě ladění výpisu paměti, že došlo k nevracení paměti významné|
|[_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|Ověřte, že blok zadaný paměti umístěn v rámci lokální haldy a, má identifikátor typ bloku platný ladění haldy|
|[_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|Ověří, jestli zadaný ukazatel je v lokální haldy|
|[_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|Ověřte, zda je zadaná paměťová rozsahu platný pro čtení a zápis|
|[_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|Získat aktuální stav haldy ladění a uložit ho do poskytované aplikací **_CrtMemState** struktura|
|[_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|Porovnání dvou stavů – stav paměti pro významné rozdíly a vrátí výsledky|
|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|Vypsat informace o objektech v haldě, protože zadaný kontrolní bod pořízení nebo od začátku spuštění programu|
|[_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|Vypsat informace hlavičky ladění pro zadaná paměťová stav ve formě čitelné pro uživatele|
|[_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|Vrátí bloku přidružený ukazatel bloku haldy ladění daný typ/podtyp.|
|[_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|Nainstalovat funkce klienta definované přidělení zapojení do procesu přidělení paměti ladění za běhu C|
|[_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|Nastavení zarážky na číslo pořadí přidělení zadaný objekt|
|[_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|Načtení nebo změnu stavu **_crtDbgFlag** příznak, který řídí chování přidělení správce hald ladění|
|[_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|Nainstalovat funkci definované aplikací, která je volána pokaždé, když je volána funkce ladění s výpisem paměti pro výpis **_CLIENT_BLOCK** zadejte bloky paměti|
|[_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|Určení souboru nebo datového proudu má být použit jako cíl pro konkrétní typ sestavy podle **_CrtDbgReport**|
|[_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|Nainstalujte klienta definované funkce vytváření sestav podle zapojení do vykazování procesu ladění za běhu C|
|[_CrtSetReportHook2, _CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|Nainstaluje nebo odinstaluje klienta definované funkce vytváření sestav podle zapojení do vykazování procesu ladění za běhu C.|
|[_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|Zadejte obecné příjemcům pro typ konkrétní sestavy generované **_CrtDbgReport**|
|[_RPT&AMP;#91;0,1,2,3,4&AMP;#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Sledovat průběh aplikace generování sestav ladění voláním **_CrtDbgReport** pomocí formátovacího řetězce a proměnný počet argumentů. Poskytuje žádný zdrojový soubor a informace čísla řádku.|
|[_RPTF&AMP;#91;0,1,2,3,4&AMP;#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Podobně jako **_RPTn** makra, ale poskytuje zdrojový soubor název a číslo řádku původu požadavku na sestavu|
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|Přidělit zadaný počet paměťových bloků na haldě s další místo pro ladění záhlaví a přepsat vyrovnávací paměti|
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|Změna velikosti zadaný blok paměti v haldě rozbalením nebo smluvní bloku|
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|Bezplatné blok paměti v haldě|
|[_fullpath_dbg, _wfullpath_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|Vytvoření názvu absolutní nebo úplnou cestu pro zadanou cestu relativní název, pomocí [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) přidělení paměti.|
|[_getcwd_dbg, _wgetcwd_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|Získání aktuálního pracovního adresáře a pomocí [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) přidělení paměti.|
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|Přidělení bloku paměti v haldě s další místo pro ladění záhlaví a přepsat vyrovnávací paměti|
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|Vypočítat velikost bloku paměti v haldě|
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|Přesunutí nebo změně velikosti bloku přidělit jinému uživateli zadaný blok paměti v haldě|
|[_strdup_dbg, _wcsdup_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|Duplicitní řetězce, pomocí [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) přidělení paměti.|
|[_tempnam_dbg, _wtempnam_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|Generovat názvy můžete použít k vytvoření dočasné soubory, pomocí [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) přidělení paměti.|

## <a name="c-runtime-routines-that-are-not-available-in-source-code-form"></a>Zdroj rutin modulu runtime jazyka C, které nejsou k dispozici v podobě kódu

Ladicí program je možné procházet zdrojový kód pro většinu rutin modulu runtime jazyka C během ladění procesu. Ale Microsoft bere v úvahu některé technologie bude proprietární a proto neposkytuje zdrojový kód pro podmnožinu těchto rutin. Většina z těchto rutin patřit do skupiny s plovoucí desetinnou čárkou zpracování nebo zpracování výjimek, ale několik dalších jsou zahrnuté také. V následující tabulce jsou uvedeny tyto rutiny.

||||
|-|-|-|
|[Funkce ACOS](../c-runtime-library/reference/acos-acosf-acosl.md)|[acosh –](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|[ASIN](../c-runtime-library/reference/asin-asinf-asinl.md)|
|[asinh –](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|[Atan, atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[atanh –](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|
|[Besselovy funkce](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[_cabs](../c-runtime-library/reference/cabs.md)|[Ceil –](../c-runtime-library/reference/ceil-ceilf-ceill.md)|
|[_chgsign](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[_control87 – _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|
|[copysign –](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[Cos](../c-runtime-library/reference/cos-cosf-cosl.md)|[COSH –](../c-runtime-library/reference/cosh-coshf-coshl.md)|
|[Exp](../c-runtime-library/reference/exp-expf.md)|[fabs –](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[_finite –](../c-runtime-library/reference/finite-finitef.md)|
|[Dolní mez](../c-runtime-library/reference/floor-floorf-floorl.md)|[Fmod –](../c-runtime-library/reference/fmod-fmodf.md)|[_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|
|[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|[_fpreset](../c-runtime-library/reference/fpreset.md)|[frexp](../c-runtime-library/reference/frexp.md)|
|[_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|
|[protokol](../c-runtime-library/reference/log-logf-log10-log10f.md)|[_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|
|[longjmp](../c-runtime-library/reference/longjmp.md)|[_matherr](../c-runtime-library/reference/matherr.md)|[modf –](../c-runtime-library/reference/modf-modff-modfl.md)|
|[_nextafter](../c-runtime-library/reference/nextafter-functions.md)|[Pow](../c-runtime-library/reference/pow-powf-powl.md)|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_scalb](../c-runtime-library/reference/scalb.md)|[scanf_s](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|[Sin](../c-runtime-library/reference/sin-sinf-sinl.md)|
|[SINH –](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|[_status87 – _statusfp –](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|
|[Tan](../c-runtime-library/reference/tan-tanf-tanl.md)|[TANH –](../c-runtime-library/reference/tanh-tanhf-tanhl.md)||

I když se zdrojový kód je k dispozici pro většinu **printf** a **scanf** rutiny, získávají vnitřní volání pro jiné rutiny pro zdroj, který není k dispozici kódu.

## <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>Rutiny, které se chovají jinak než v ladicím sestavení aplikace

Některé funkce jazyka C za běhu a operátorů jazyka C++ chovat jinak při volání z sestavení pro ladění aplikace. (Všimněte si, že sestavení pro ladění aplikace lze provést definováním buď `_DEBUG` příznak nebo s ladicí verzí knihovny run-time jazyka C pomocí propojení.) Behaviorální rozdíly se obvykle skládají z doplňkových funkcí nebo informace, které poskytuje rutiny pro podporu ladění procesu. V následující tabulce jsou uvedeny tyto rutiny.

|||
|-|-|
|C [přerušit](../c-runtime-library/reference/abort.md) rutina|C++ [odstranit](../cpp/delete-operator-cpp.md) – operátor|
|C [vyhodnocení](../c-runtime-library/reference/assert-macro-assert-wassert.md) rutina|C++ [nové](../cpp/new-operator-cpp.md) – operátor|

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Kontrola chyb za běhu](../c-runtime-library/run-time-error-checking.md)<br/>
