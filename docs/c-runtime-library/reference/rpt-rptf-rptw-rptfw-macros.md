---
title: _RPT, _RPTF, _RPTW, _RPTFW – makra
ms.date: 11/04/2016
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- RPT3
- RPTF4
- _RPT4
- RPT1
- _RPTF0
- RPTF3
- _RPTF4
- RPTF1
- RPT4
- _RPT1
- _RPT0
- RPT0
- _RPTF2
- RPTF0
- _RPT3
- _RPT2
- _RPTF3
- RPT2
- _RPTF1
helpviewer_keywords:
- debugging [CRT], using macros
- _RPTW3 macro
- _RPT0 macro
- RPTW4 macro
- _RPTF3 macro
- _RPTW4 macro
- RPTF4 macro
- RPTFW2 macro
- RPTW macros
- RPT1 macro
- _RPTF macros
- RPTFW3 macro
- _RPTW0 macro
- _RPTF0 macro
- macros, debugging with
- _RPTW2 macro
- RPTF3 macro
- RPT3 macro
- RPT0 macro
- _RPT macros
- RPTW3 macro
- _RPTFW macros
- debug reporting macros
- RPTF macros
- RPT macros
- _RPTW macros
- RPTF2 macro
- _RPTF1 macro
- _RPT1 macro
- _RPT4 macro
- _RPTFW2 macro
- _RPTFW1 macro
- RPTF0 macro
- _RPT2 macro
- RPTFW macros
- _RPTW1 macro
- _RPTFW0 macro
- RPT4 macro
- _RPT3 macro
- _RPTFW3 macro
- _RPTF4 macro
- _RPTFW4 macro
- _RPTF2 macro
- RPTW0 macro
- RPTFW4 macro
- RPTFW0 macro
- RPTW2 macro
- RPTF1 macro
- RPT2 macro
- RPTFW1 macro
- RPTW1 macro
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
ms.openlocfilehash: 61748cca2cdfcc2d72b6943bfeedd9597009e20b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440091"
---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW – makra

Sleduje průběh aplikace generování sestav ladění (pouze ladicí verze). Všimněte si, že *n* určuje počet argumentů v *args* a může být 0, 1, 2, 3, 4 nebo 5.

## <a name="syntax"></a>Syntaxe

```C
_RPT
      n
      (
   reportType,
   format,
...[args]
);
_RPTFn(
   reportType,
   format,
   [args]
);
_RPTWn(
   reportType,
   format
   [args]
);
_RPTFWn(
   reportType,
   format
   [args]
);
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ sestavy: **_CRT_WARN**, **_CRT_ERROR**, nebo **_CRT_ASSERT**.

*Formát*<br/>
Řetězec řízení formátu se používá k vytvoření zprávy pro uživatele.

*argumenty*<br/>
Argumenty nahrazení použité příkazem *formátu*.

## <a name="remarks"></a>Poznámky

Tato makra trvat *reportType* a *formátu* parametry. Kromě toho se může trvat až čtyři další argumenty, které jsou označeny číslo připojeným k názvu makra. Například **_RPT0** a **_RPTF0** nepřebírají žádné další argumenty **_RPT1** a **_RPTF1** trvat *arg1*, **_RPT2** a **_RPTF2** trvat *arg1* a **arg2**, a tak dále.

**_RPT** a **_RPTF** makra jsou podobné [printf](printf-printf-l-wprintf-wprintf-l.md) fungovat, protože slouží ke sledování pokroku vaší aplikace během ladění procesu. Tato makra jsou však flexibilnější, než **printf** vzhledem k tomu, že není potřeba nacházet v **#ifdef** příkazy tak tomu, aby se volá v sestavení prodejní verze aplikace. Díky této flexibilitě se dosahuje prostřednictvím využití [_DEBUG](../../c-runtime-library/debug.md) – makro; **_RPT** a **_RPTF** makra jsou k dispozici pouze pokud **_DEBUG** příznak je definice. Když **_DEBUG** není definován, volání makra jsou odstraněna během předběžného zpracování.

**_RPTW** a **_rptfw –** makra jsou širokoznaké verze těchto maker. Jsou jako **wprintf** a přijímají řetězce širokého znaku jako argumenty.

**_RPT** volání makra [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) funkci generování sestav ladění se zprávou uživatele. **_RPTW** volání makra **_crtdbgreportw –** funkce k vytvoření stejné sestavy pomocí široké znaky. **_RPTF** a **_rptfw –** makra vytvořit sestavu ladění s zdrojový soubor a číslo řádku kde byla volána – makro sestavy, kromě uživatele zprávu. Vytvoření uživatelské zprávy nahrazením **arg**[*n*] argumenty do *formátu* řetězce, pomocí stejných pravidel definovaných funkcemi [printf](printf-printf-l-wprintf-wprintf-l.md)funkce.

**_CrtDbgReport** nebo **_crtdbgreportw –** generuje sestavu ladění a určí své cíle založené na aktuálních režimech sestavy a soubor definice pro *reportType*. [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md) funkce se používají k definování cíle pro každý typ sestavy.

Pokud **_RPT** makro zavolalo a ani **_CrtSetReportMode** ani **_CrtSetReportFile** byla volána, zprávy se zobrazují následujícím způsobem.

|Typ sestavy|Cíl výstupu|
|-----------------|------------------------|
|**_CRT_WARN**|Text upozornění se nezobrazí.|
|**_CRT_ERROR**|Automaticky otevírané okno. Stejné jako `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` kdyby nebyl zadán.|
|**_CRT_ASSERT**|Stejné jako **_CRT_ERROR**.|

Pokud cíl je okno zprávy ladění a uživatel klikne **opakujte** tlačítko, **_CrtDbgReport** nebo **_crtdbgreportw –** vrátí hodnotu 1 způsobí tato makra spustit ladicí program, za předpokladu, že je povoleno ladění just-in-time (JIT). Další informace o použití těchto maker jako ladění chyba mechanismu pro zpracování, naleznete v tématu [použití maker pro ověřování a vytváření sestav](/visualstudio/debugger/macros-for-reporting).

Existují dvě další makra, které generují sestavu ladění. [_ASSERT](assert-asserte-assert-expr-macros.md) – makro generuje sestavu, ale pouze pokud její argument výraz nevyhodnotí jako FALSE. [_Asserte –](assert-asserte-assert-expr-macros.md) je přesně like **_ASSERT**, ale zahrnuje selhání výrazu v generované sestavě.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-----------|---------------------|
|**_RPT** makra|\<crtdbg.h>|
|**_RPTF** makra|\<crtdbg.h>|
|**_RPTW** makra|\<crtdbg.h>|
|**_Rptfw –** makra|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

I když jsou makra a získávají se zahrnutím souboru Crtdbg.h, musí aplikace propojit s jednou z knihovny ladění, protože tato makra volání dalších funkcí za běhu.

## <a name="example"></a>Příklad

Podívejte se na příklad v [_ASSERT](assert-asserte-assert-expr-macros.md) tématu.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
