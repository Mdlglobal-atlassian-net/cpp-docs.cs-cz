---
title: _CrtSetReportMode
ms.date: 11/04/2016
api_name:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: ae7e83ac009d572f8a9f6484519b0cdfb7499ce3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938467"
---
# <a name="_crtsetreportmode"></a>_CrtSetReportMode

Určuje cíl nebo cíle pro konkrétní typ sestavy generovaný **_CrtDbgReport** a všechna makra, která volají [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md), jako je [_ASSERT, _ASSERTE, _ASSERT_EXPR maker](assert-asserte-assert-expr-macros.md), [_ASSERT, _ASSERTE, _ Makra ASSERT_EXPR](assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, _RPTFW makra](rpt-rptf-rptw-rptfw-macros.md)a [_RPT, _RPTF, _RPTW, _RPTFW makra](rpt-rptf-rptw-rptfw-macros.md) (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ sestavy: **_CRT_WARN**, **_CRT_ERROR**a **_CRT_ASSERT**.

*reportMode*<br/>
Nový režim sestavy nebo režimy pro *ReportType*.

## <a name="return-value"></a>Návratová hodnota

Po úspěšném dokončení vrátí **_CrtSetReportMode** předchozí režim nebo režimy sestavy pro typ sestavy zadaný v *ReportType*. Pokud je předána neplatná hodnota jako *ReportType* nebo je zadán neplatný režim pro *ReportMode*, **_CrtSetReportMode** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí-1. Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_CrtSetReportMode** určuje cíl výstupu pro **_CrtDbgReport**. Vzhledem k **tomu, že** makra [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md), [_RPT](rpt-rptf-rptw-rptfw-macros.md)a [_RPTF](rpt-rptf-rptw-rptfw-macros.md) volání **_CrtDbgReport**určuje cíl výstupu textu zadaného pomocí těchto maker.

Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtSetReportMode** se během předběžného zpracování odeberou.

Pokud nevoláte **_CrtSetReportMode** k definování výstupního cíle zpráv, platí následující výchozí hodnoty:

- Selhání kontrolního výrazu a chyby jsou směrovány do okna zprávy ladění.

- Upozornění z aplikací systému Windows jsou odesílána do okna výstupu ladicího programu.

- Upozornění z konzolových aplikací se nezobrazí.

V následující tabulce jsou uvedeny typy sestav definované v souboru Crtdbg. h.

|Typ sestavy|Popis|
|-----------------|-----------------|
|**_CRT_WARN**|Upozornění, zprávy a informace, které nevyžadují okamžitou pozornost.|
|**_CRT_ERROR**|Chyby, neodstranitelné problémy a problémy, které vyžadují okamžitou pozornost.|
|**_CRT_ASSERT**|Chyby kontrolního výrazu (výrazy, které se vyhodnotí jako **NEPRAVDA**)|

Funkce **_CrtSetReportMode** přiřadí nový režim sestavy zadaný v *ReportMode* k typu sestavy určenému v *ReportType* a vrátí dříve definovaný režim sestavy pro *ReportType*. V následující tabulce jsou uvedeny dostupné možnosti pro *ReportMode* a výsledné chování **_CrtDbgReport**. Tyto možnosti jsou definovány jako bitové příznaky v souboru Crtdbg. h.

|Režim sestavy|Chování _CrtDbgReport|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|Zapíše zprávu do okna výstupu ladicího programu.|
|**_CRTDBG_MODE_FILE**|Zapíše zprávu do popisovače souboru zadaného uživatelem. [_CrtSetReportFile](crtsetreportfile.md) by měla být volána k definování konkrétního souboru nebo datového proudu, který chcete použít jako cíl.|
|**_CRTDBG_MODE_WNDW**|Vytvoří okno se zprávou, ve kterém se zobrazí zpráva s tlačítky pro [přerušení](abort.md), **opakování**a **ignorování** .|
|**_CRTDBG_REPORT_MODE**|Vrátí *ReportMode* pro zadaný *ReportType*:<br /><br /> 1   **_CRTDBG_MODE_FILE**<br /><br /> 2   **_CRTDBG_MODE_DEBUG**<br /><br /> 4   **_CRTDBG_MODE_WNDW**|

Každý typ sestavy lze nahlásit pomocí jednoho, dvou nebo tří režimů nebo vůbec bez režimu. Proto je možné pro jeden typ sestavy definovat více než jeden cíl. Například následující fragment kódu způsobí, že chyby kontrolního výrazu budou odesílány do okna zprávy ladění i do **stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

Kromě toho se dá režim generování sestav nebo režimy pro jednotlivé typy sestav řídit samostatně. Například je možné určit, že se má *ReportType* **_CRT_WARN** odeslat do výstupního řetězce ladění, zatímco **_CRT_ASSERT** se zobrazí pomocí okna zprávy ladění a odesláno do **stderr**, jak je uvedeno výše.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

**Knihovna** Ladit verze pouze [funkcí knihoven CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
