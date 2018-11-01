---
title: _CrtSetReportMode
ms.date: 11/04/2016
apiname:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: 2096d39a8ba316fc76c97517a16e34231940e7f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595530"
---
# <a name="crtsetreportmode"></a>_CrtSetReportMode

Určuje cíle nebo cílů pro typ konkrétní sestavy generované **_CrtDbgReport** a makra, které volají [_CrtDbgReport _crtdbgreportw –](crtdbgreport-crtdbgreportw.md), jako například [_ASSERT, _asserte –, Makra _ASSERT_EXPR](assert-asserte-assert-expr-macros.md), [_ASSERT, _asserte –, _ASSERT_EXPR makra](assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, _rptfw – makra](rpt-rptf-rptw-rptfw-macros.md), a [_RPT, _RPTF, _RPTW, _rptfw – makra](rpt-rptf-rptw-rptfw-macros.md) (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ sestavy: **_CRT_WARN**, **_CRT_ERROR**, a **_CRT_ASSERT**.

*ReportMode.*<br/>
Nová sestava režim nebo režimy *reportType*.

## <a name="return-value"></a>Návratová hodnota

Při úspěšném dokončení **_CrtSetReportMode** vrátí předchozí sestavu režimu nebo režimů pro typ sestavy určený v *reportType*. Pokud je předána neplatná hodnota jako *reportType* nebo je zadaný neplatný režim pro *ReportMode*, **_CrtSetReportMode** vyvolá obslužnou rutinu neplatného parametru, jako popsané v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_CrtSetReportMode** Určuje cíl výstupu **_CrtDbgReport**. Protože makra [_ASSERT](assert-asserte-assert-expr-macros.md), [_asserte –](assert-asserte-assert-expr-macros.md), [_RPT](rpt-rptf-rptw-rptfw-macros.md), a [_RPTF](rpt-rptf-rptw-rptfw-macros.md) volání **_CrtDbgReport**, **_CrtSetReportMode** Určuje cíl výstupu textu zadaným makra.

Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtSetReportMode** odstraněna během předběžného zpracování.

Pokud není volána **_CrtSetReportMode** definovat cíl výstupu zpráv, pak následující výchozí hodnoty jsou aktivní:

- Chyby a selhání kontrolního výrazu jsou směrované na okno zprávy ladění.

- Upozornění z aplikace Windows se odesílají do okna výstup ladicího programu.

- Upozornění z konzolové aplikace nejsou zobrazeny.

Následující tabulka uvádí typy sestav, které jsou definovány v souboru Crtdbg.h.

|Typ sestavy|Popis|
|-----------------|-----------------|
|**_CRT_WARN**|Upozornění, zprávy a informace, které nejsou vyžadují okamžitou pozornost.|
|**_CRT_ERROR**|Chyby, neodstranitelné chyby a problémy, které vyžadují okamžitou pozornost.|
|**_CRT_ASSERT**|Selhání kontrolního výrazu (s prohlašovanou výrazy, které vedou k **FALSE**).|

**_CrtSetReportMode** funkce přiřadí nový režim sestavy podle *ReportMode* typ sestavy určený v *reportType* a vrátí dříve definované režim sestavy pro *reportType*. V následující tabulce jsou uvedeny dostupné možnosti pro *ReportMode* a výsledné chování **_CrtDbgReport**. Tyto možnosti jsou definovány jako bitové příznaky v souboru Crtdbg.h.

|Režim sestavy|_CrtDbgReport chování|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|Zapíše zprávu do okna výstup ladicího programu.|
|**_CRTDBG_MODE_FILE**|Zapíše popisovač souboru uživatelem zadané zprávy. [_CrtSetReportFile](crtsetreportfile.md) by měla být volána pro definování konkrétního souboru nebo datový proud použít jako cíl.|
|**_CRTDBG_MODE_WNDW**|Vytvoří okno se zprávou pro zobrazení zprávy spolu s [přerušit](abort.md), **opakujte**, a **Ignorovat** tlačítka.|
|**_CRTDBG_REPORT_MODE**|Vrátí *ReportMode* pro zadaný rozbočovač *reportType*:<br /><br /> 1 **_CRTDBG_MODE_FILE**<br /><br /> 2 **_CRTDBG_MODE_DEBUG**<br /><br /> 4 **_CRTDBG_MODE_WNDW**|

Každý typ sestavy mohou být zaznamenány vůbec pomocí jedna, dvě nebo tři režimy nebo žádný. Proto je možné mít víc než jeden cíl definovaného pro typ jednu sestavu. Například následující fragment kódu způsobí selhání kontrolního výrazu k odeslání do obou okno zprávy ladění a **stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

Kromě toho vytváření sestav režimu nebo režimů pro každý typ sestavy lze ovládat samostatně. Například je možné určit, že *reportType* z **_CRT_WARN** být odeslána jako výstupní řetězec ladění, zatímco **_CRT_ASSERT** se zobrazí okno zprávy ladění pomocí a odesílat **stderr**, dřív ilustrované.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

**Knihovny:** ladicí verze [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
