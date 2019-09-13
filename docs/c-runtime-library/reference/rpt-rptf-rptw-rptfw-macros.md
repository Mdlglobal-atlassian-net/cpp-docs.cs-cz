---
title: _RPT, _RPTF, _RPTW, _RPTFW – makra
ms.date: 11/04/2016
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 567fe0a68f5adad6f5d90ef3da9d673a75bb83a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949088"
---
# <a name="_rpt-_rptf-_rptw-_rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW – makra

Sleduje průběh aplikace vygenerováním sestavy ladění (pouze ladicí verze). Počítejte s tím, že *n* určuje počet argumentů *v* argumentech a může být 0, 1, 2, 3, 4 nebo 5.

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
Typ sestavy: **_CRT_WARN**, **_CRT_ERROR**nebo **_CRT_ASSERT**.

*format*<br/>
Řetězec řízení formátu použitý k vytvoření zprávy uživatele.

*argumentů*<br/>
Argumenty nahrazení používané *formátem*

## <a name="remarks"></a>Poznámky

Všechna tato makra přijímají parametry *ReportType* a *Format* . Kromě toho mohou také trvat až čtyři další argumenty, které jsou označeny číslem připojené k názvu makra. Například **_RPT0** a **_RPTF0** nevyužívají žádné další argumenty, **_RPT1** a **_RPTF1** přijmout *arg1*, **_RPT2** a **_RPTF2** přijmout *arg1* a **arg2**atd.

Makra **_RPT** a **_RPTF** jsou podobná funkci [printf](printf-printf-l-wprintf-wprintf-l.md) , protože je lze použít ke sledování pokroku aplikace během procesu ladění. Tato makra jsou však pružnější než **printf** , protože nemusí být uzavřena v příkazech **#ifdef** , aby bylo zabráněno jejich volání v maloobchodním sestavení aplikace. Tato flexibilita se dosahuje pomocí makra [_DEBUG](../../c-runtime-library/debug.md) ; makra **_RPT** a **_RPTF** jsou k dispozici pouze v případě, že je definován příznak **_DEBUG** . Když není definovaný **_DEBUG** , volání těchto maker se během předběžného zpracování odeberou.

Makra **_RPTW** a **_RPTFW** jsou verze s nejrůznějšími znaky těchto maker. Jsou jako **wprintf** a jako argumenty přebírají řetězce s velkým znakem.

Makra **_RPT** volají funkci [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) pro generování sestavy ladění s uživatelskou zprávou. Makra **_RPTW** volají funkci **_CrtDbgReportW** , která vygeneruje stejnou sestavu s velkým množstvím znaků. Makra **_RPTF** a **_RPTFW** vytvoří sestavu ladění se zdrojovým souborem a číslem řádku, kde bylo makro sestavy voláno, a také uživatelskou zprávou. Zpráva uživatele je vytvořena nahrazením argumentů **arg**[*n*] do řetězce *formátu* pomocí stejných pravidel definovaných funkcí [printf](printf-printf-l-wprintf-wprintf-l.md) .

**_CrtDbgReport** nebo **_CrtDbgReportW** vygeneruje sestavu ladění a určí její umístění na základě aktuální režimy sestavy a souboru definovaného pro *ReportType*. Funkce [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md) slouží k definování cílových umístění pro každý typ sestavy.

Pokud je voláno makro **_RPT** a nebyl volán ani **_CrtSetReportMode** ani **_CrtSetReportFile** , zobrazí se zprávy následujícím způsobem.

|Typ sestavy|Cíl výstupu|
|-----------------|------------------------|
|**_CRT_WARN**|Text upozornění není zobrazen.|
|**_CRT_ERROR**|Automaticky otevírané okno. Stejné, jako `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` kdyby byla zadána.|
|**_CRT_ASSERT**|Stejné jako **_CRT_ERROR**.|

Když je cílem okno zprávy ladění a uživatel klikne na tlačítko **Opakovat** , **_CrtDbgReport** nebo **_CrtDbgReportW** vrátí 1, což způsobí, že tato makra spustí ladicí program za předpokladu, že je povoleno ladění JIT (just-in-time). Další informace o použití těchto maker jako mechanismu pro zpracování chyb ladění najdete v tématu [použití maker pro ověřování a vytváření sestav](/visualstudio/debugger/macros-for-reporting).

Existují dvě další makra, která generují sestavu ladění. Makro [_ASSERT](assert-asserte-assert-expr-macros.md) vygeneruje sestavu, ale pouze v případě, že je její argument výrazu vyhodnocen jako false. [_ASSERTE](assert-asserte-assert-expr-macros.md) je přesně stejně jako **_ASSERT**, ale obsahuje výraz, který se nezdařil, ve vygenerované sestavě.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-----------|---------------------|
|Makra **_RPT**|\<crtdbg.h>|
|Makra **_RPTF**|\<crtdbg.h>|
|Makra **_RPTW**|\<crtdbg.h>|
|Makra **_RPTFW**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

I když se jedná o makra a jsou získána zahrnutím souboru Crtdbg. h, aplikace musí propojit s jednou z knihoven ladění, protože tato makra volají jiné běhové funkce.

## <a name="example"></a>Příklad

Podívejte se na příklad v tématu [_ASSERT](assert-asserte-assert-expr-macros.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
