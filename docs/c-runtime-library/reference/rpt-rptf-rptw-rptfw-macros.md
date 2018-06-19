---
title: _RPT, _RPTF, _RPTW, _rptfw – makra | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a53a069138b4e54988be008917e5ca2b24fa0a6c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411881"
---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW – makra

Sleduje aplikace probíhá generování sestavy ladění (pouze ladicí verze). Všimněte si, že *n* určuje počet argumentů *argumentů* a může být 0, 1, 2, 3, 4 nebo 5.

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

*reportType* typ sestavy: **_CRT_WARN**, **_CRT_ERROR**, nebo **_CRT_ASSERT**.

*Formát* řetězec formátu – ovládací prvek použitý k vytvoření uživatelské zprávy.

*argumentů* argumenty nahrazení používá *formátu*.

## <a name="remarks"></a>Poznámky

Všechny tyto makra trvat *reportType* a *formát* parametry. Kromě toho se může trvat až čtyři další argumenty, které jsou označeny číslo připojeným k názvu makro. Například **_rpt0 –** a **_rptf0 –** nepřebírají žádné další argumenty, **_rpt1 –** a **_rptf1 –** trvat *arg1*, **_Rpt2 –** a **_rptf2 –** trvat *arg1* a **arg2**a tak dále.

**_RPT** a **_RPTF** makra jsou podobné [printf](printf-printf-l-wprintf-wprintf-l.md) fungovat, protože je možné použít ke sledování průběhu aplikace během procesu ladění. Tyto makra jsou však flexibilnější než **printf** vzhledem k tomu, že není potřeba být uzavřená do **#ifdef** příkazy, aby nebylo volal v prodejní sestavení aplikace. Tuto flexibilitu potřebují dosáhnete pomocí [_DEBUG –](../../c-runtime-library/debug.md) makro; **_RPT** a **_RPTF** makra jsou k dispozici pouze při **_DEBUG –** příznak je definován. Když **_DEBUG –** není definována, volání makra jsou odebrány při předběžném zpracování.

**_RPTW** a **_rptfw –** makra jsou široká charakterová verze těchto makra. Jsou jako **wprintf** a přijímají řetězce široká charakterová jako argumenty.

**_RPT** makra volání [_crtdbgreport –](crtdbgreport-crtdbgreportw.md) funkce k vygenerování sestavy ladění zprávou uživatele. **_RPTW** makra volání **_crtdbgreportw –** funkce při generování sestav o stejné s široké znaky. **_RPTF** a **_rptfw –** makra vytvoření sestavy ladění se zdrojový soubor a řádku číslem kde makro sestava byla volána, kromě uživatele zprávu. Vytvoří zprávu uživatele nahraďte **arg**[*n*] argumenty do *formátu* řetězce, pomocí stejných pravidel definované [printf](printf-printf-l-wprintf-wprintf-l.md)funkce.

**_Crtdbgreport –** nebo **_crtdbgreportw –** generuje sestavu, ladění a určí jeho cíle podle režimů aktuální sestavy a soubor definice pro *reportType*. [_Crtsetreportmode –](crtsetreportmode.md) a [_crtsetreportfile –](crtsetreportfile.md) funkce slouží k určení cíle pro každý typ sestavy.

Pokud **_RPT** makro nazývá a ani **_crtsetreportmode –** ani **_crtsetreportfile –** byla volána, zprávy se zobrazují následujícím způsobem.

|Typ sestavy|Cíl výstupu|
|-----------------|------------------------|
|**_CRT_WARN**|Text upozornění se nezobrazí.|
|**_CRT_ERROR**|Automaticky otevírané okno. Stejné jako `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` určen.|
|**_CRT_ASSERT**|Stejné jako **_CRT_ERROR**.|

Když cílové okno zprávy ladění a uživatel vybere **opakujte** tlačítko **_crtdbgreport –** nebo **_crtdbgreportw –** vrátí hodnotu 1, příčinou těchto makra spustit ladicí program, za předpokladu, že je povoleno ladění za běhu (JIT). Další informace o použití těchto maker jako ladění chyba mechanismu pro zpracování najdete v tématu [pomocí makra pro ověření a vytváření sestav](/visualstudio/debugger/macros-for-reporting).

Existují dva další makra, které vygenerovat sestavu, ladění. [_ASSERT](assert-asserte-assert-expr-macros.md) makro generuje sestavy, ale jenom v případě, že její argument výrazu vyhodnocena jako FALSE. [_Asserte –](assert-asserte-assert-expr-macros.md) je přesně například **_ASSERT**, ale zahrnuje selhání výrazu v vygenerovanou sestavu.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-----------|---------------------|
|**_RPT** makra|\<crtdbg.h>|
|**_RPTF** makra|\<crtdbg.h>|
|**_RPTW** makra|\<crtdbg.h>|
|**_Rptfw –** makra|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

I když jsou makra a jsou získány zahrnutím Crtdbg.h, musí aplikace propojit s jedním z knihovny ladění, protože tyto makra volat jiné běhové funkce.

## <a name="example"></a>Příklad

Podívejte se na příklad v [_ASSERT](assert-asserte-assert-expr-macros.md) tématu.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
