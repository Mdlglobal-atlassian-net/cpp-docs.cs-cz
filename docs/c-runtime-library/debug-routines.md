---
title: "Rutiny ladění | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.debug
dev_langs: C++
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], run-time routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 158a3b782ffedc7bd206f400c066c052062ad402
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="debug-routines"></a>Rutiny ladění
Ladicí verze běhové knihovny jazyka C poskytuje mnoho diagnostické služby, které snazší ladění programů a umožňují vývojářům:  
  
-   Krok přímo do běhové funkce během ladění  
  
-   Vyřešte kontrolní výrazy, chyb a výjimek  
  
-   Přidělení haldy trasování a zabránit nevracení paměti  
  
-   Sestava zprávy ladění pro uživatele  
  
 Pro použití těchto rutin, [_DEBUG –](../c-runtime-library/debug.md) příznak musí být definován. Všechny tyto rutiny nedělat nic prodejní sestavení aplikace. Další informace o tom, jak používat nové rutiny ladění najdete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).  
  
### <a name="debug-versions-of-the-c-run-time-library-routines"></a>Ladicí verze rutiny běhové knihovny jazyka C  
  
|Rutina|Použití|  
|-------------|---------|  
|[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Vyhodnocení výrazu a generuje sestavy ladění, když je výsledkem FALSE|  
|[_ASSERTE –](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|Podobně jako `_ASSERT`, ale zahrnuje selhání výrazu v vygenerovanou sestavu.|  
|[_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|Potvrdil integritu bloky paměti přidělené v haldě ladění|  
|[_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|Nastaví přerušení.|  
|[_CrtDbgReport, _CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|Vygenerování sestavy ladění zprávou uživatele a odeslat zprávu o tři možné cíle|  
|[_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|Volání funkce poskytované aplikací pro všechny `_CLIENT_BLOCK` typy v haldě|  
|[_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|Vypsat všechny bloky paměti v haldě ladění při došlo k úniku velké paměti|  
|[_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|Ověřte, zda blok zadaná paměťová se nachází v rámci lokální haldy a že má identifikátor typ bloku haldy platný ladění|  
|[_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|Ověřuje, že je zadaný ukazatel v lokální haldy|  
|[_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|Ověřte, zda zadaná paměťová rozsah je platný pro čtení a zápis|  
|[_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|Získání aktuálního stavu haldy ladění a uložte ho aplikaci zadané `_CrtMemState` struktura|  
|[_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|Porovnání dvou stavů – stav paměti pro významné rozdíly a vrátí výsledky|  
|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|Dump informace o objektech v haldě od doby pořízení zadaný kontrolní bod nebo od začátku spuštění programu|  
|[_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|Dump informace ze záhlaví ladění stavu zadaná paměťová uživatelem čitelný formuláře|  
|[_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|Vrátí bloku přidružené ukazatel bloku haldy ladění daný typ nebo dílčí.|  
|[_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|Nainstalovat funkce definované klienta přidělení zapojování do procesu přidělení paměti běhové ladění C|  
|[_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|Nastavit zarážky pořadové číslo zadaný objekt přidělení|  
|[_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|Načtení nebo změně stavu `_crtDbgFlag` příznak můžete řídit chování přidělení správce halda ladění|  
|[_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|Instalace funkce definované aplikací, která je volána pokaždé, když je volána funkce výpis ladění pro výpis `_CLIENT_BLOCK` zadejte bloky paměti|  
|[_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|Určení souboru nebo datový proud, který se má použít jako cíl pro konkrétní typ sestavy podle`_CrtDbgReport`|  
|[_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|Zapojování do ladění C spuštění procesu vytváření sestav nainstalovat klienta definované funkce vytváření sestav|  
|[_CrtSetReportHook2, _CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|Instaluje nebo odinstaluje klienta definované funkce vytváření sestav podle zapojování do ladění C spuštění procesu vytváření sestav.|  
|[_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|Zadejte obecné příjemcům pro konkrétní typ sestavy generované`_CrtDbgReport`|  
|[_RPT &#91; 0,1,2,3,4 &#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Sledovat průběh aplikace pomocí generování sestavy ladění voláním `_CrtDbgReport` s řetězec formátu a proměnný počet argumentů. Poskytuje zdrojové souborové služby a řádku číslo informace.|  
|[_RPTF &#91; 0,1,2,3,4 &#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|Podobně jako `_RPTn` makra, ale poskytuje číslo zdrojového souboru název a řádek, kde požadavku na sestavu vytvořena|  
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
  
 Rutiny ladění lze použít ke kroku prostřednictvím zdrojového kódu pro většinu dalších C běhové rutiny během procesu ladění. Ale Microsoft zvažuje některé technologie, jako vlastní a, tedy neposkytuje zdrojový kód pro tyto rutiny. Většina těchto rutin, patří výjimek nebo skupiny s plovoucí desetinnou čárkou zpracování, ale některých jiných jsou zahrnuty také. Následující tabulka uvádí tyto rutiny.  
  
### <a name="c-run-time-routines-that-are-not-available-in-source-code-form"></a>Běhové rutiny C, která nejsou k dispozici v podobě zdrojového kódu  
  
||||  
|-|-|-|  
|[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|[_fpclass –](../c-runtime-library/reference/fpclass-fpclassf.md)|[_nextafter –](../c-runtime-library/reference/nextafter-functions.md)|  
|[ASIN](../c-runtime-library/reference/asin-asinf-asinl.md)|[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|[Pow](../c-runtime-library/reference/pow-powf-powl.md)|  
|[Atan atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[_fpreset](../c-runtime-library/reference/fpreset.md)|[printf _printf_l –, wprintf, _wprintf_l –](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [printf_s –, _printf_s_l –, wprintf_s –, _wprintf_s_l –](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)*|  
|[_cabs](../c-runtime-library/reference/cabs.md)|[frexp](../c-runtime-library/reference/frexp.md)|[_scalb](../c-runtime-library/reference/scalb.md)|  
|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|[_hypot –](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[scanf, _scanf_l –, wscanf, _wscanf_l –](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), [scanf_s –, _scanf_s_l –, wscanf_s –, _wscanf_s_l –](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)*|  
|[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[_isnan –](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|  
|[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[_j0](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[Sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[_control87, _controlfp, \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[_j1](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[SINH](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[_jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[Sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[Cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|[_status87 –, _statusfp –](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|  
|[COSH](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[protokolu](../c-runtime-library/reference/log-logf-log10-log10f.md)|[Tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[Exp](../c-runtime-library/reference/exp-expf.md)|[LOG10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[TANH](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[_logb –](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[_y0](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[_finite –](../c-runtime-library/reference/finite-finitef.md)|[longjmp](../c-runtime-library/reference/longjmp.md)|[_y1](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[Floor](../c-runtime-library/reference/floor-floorf-floorl.md)|[_matherr](../c-runtime-library/reference/matherr.md)|[_yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[modf –](../c-runtime-library/reference/modf-modff-modfl.md)||  
  
 \*I když zdrojový kód je k dispozici pro většinu této rutiny, provede interní volání jiné rutiny, pro který není zadaný zdrojový kód.  
  
 Některé funkce runtime jazyka C a C++ operátory chovat jinak při volání z sestavení ladicí verze aplikace. (Všimněte si, že sestavení ladicí verze aplikace lze provést tak, že buď definujete `_DEBUG` příznak nebo pomocí propojení s verzí ladicí běhové knihovny jazyka C.) Chování rozdíly obvykle obsahovat další funkce nebo informace, které poskytuje rutina pro podporu procesu ladění. Následující tabulka uvádí tyto rutiny.  
  
### <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>Rutiny, které se chovají jinak ladění sestavení aplikace  
  
|||  
|-|-|  
|C [abort](../c-runtime-library/reference/abort.md) rutiny|C++ [odstranit](../cpp/delete-operator-cpp.md) – operátor|  
|C [assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) rutiny|C++ [nové](../cpp/new-operator-cpp.md) – operátor|  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)   
 [Kontrola chyb za běhu](../c-runtime-library/run-time-error-checking.md)