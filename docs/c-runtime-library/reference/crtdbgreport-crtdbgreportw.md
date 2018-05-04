---
title: _Crtdbgreport –, _crtdbgreportw – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
dev_langs:
- C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57290d2985036ea3df2863e175d742c819a3fe03
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

Vytváří sestavu ladění zprávou a odešle sestavy tři možné cíle (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtDbgReport(
   int reportType,
   const char *filename,
   int linenumber,
   const char *moduleName,
   const char *format [,
   argument] ...
);
int _CrtDbgReportW(
   int reportType,
   const wchar_t *filename,
   int linenumber,
   const wchar_t *moduleName,
   const wchar_t *format [,
   argument] ...
);
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ sestavy: **_CRT_WARN**, **_CRT_ERROR**, a **_CRT_ASSERT**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, kde došlo k chybě vyhodnocení či sestavy nebo **NULL**.

*lineNumber*<br/>
Číslo řádku na zdrojový soubor, kde došlo k chybě vyhodnocení či sestavy nebo **NULL**.

*Název modulu*<br/>
Ukazatel na název modulu (.exe nebo .dll) kde assert nebo sestavy došlo k chybě.

*Formát*<br/>
Ukazatel na řetězec formátu – ovládací prvek použitý k vytvoření uživatelské zprávy.

*Argument*<br/>
Nahrazení volitelné argumenty používané *formátu*.

## <a name="return-value"></a>Návratová hodnota

Pro všechny sestavy cílů **_crtdbgreport –** a **_crtdbgreportw –** vrátí -1, pokud dojde k chybě a 0, pokud nedojde k žádným chybám. Ale pokud je cílový sestavy okno zprávy ladění a uživatel klikne **opakujte** tlačítko vrátí tyto funkce 1. Pokud uživatel klikne **Abort** tlačítka v okně zprávy ladění tyto funkce okamžitě přerušit a nevrátí hodnotu.

[_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) ladění makra volání **_crtdbgreport –** jejich ladění generování sestav. Široká charakterová verze těchto makra a také [_ASSERT, _asserte –](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) a [_rptfw –](rpt-rptf-rptw-rptfw-macros.md), použijte **_crtdbgreportw –** na generování sestav jejich ladění. Když **_crtdbgreport –** nebo **_crtdbgreportw –** 1, vrátí tato makra spuštění ladicího programu, za předpokladu, že je povoleno ladění v běhu (JIT).

## <a name="remarks"></a>Poznámky

**_Crtdbgreport –** a **_crtdbgreportw –** můžete odeslat zprávu o ladění tři různé cíle: soubor sestavy ladění, ladění monitorování (ladicího programu sady Visual Studio) nebo okno zprávy ladění. Dvě konfigurace funkce [_crtsetreportmode –](crtsetreportmode.md) a [_crtsetreportfile –](crtsetreportfile.md), slouží k zadání cílového nebo cíle pro každý typ sestavy. Tyto funkce povolit generování sestav cílového nebo cíle pro každý typ sestavy pro samostatně řízení. Například je možné určit, že *reportType* z **_CRT_WARN** pouze se odesílá do monitorování ladění, při *reportType* z **_CRT_ASSERT** odeslat na okno zprávy ladění a soubor vlastní sestavy.

**_Crtdbgreportw –** je verze široká charakterová **_crtdbgreport –**. Všechny její výstup a řetězec parametry jsou v řetězcích široká charakterová; v opačném případě je stejná jako verze znakovou.

**_Crtdbgreport –** a **_crtdbgreportw –** vytvoření uživatelské zprávy ladění sestavy nahrazením *argument*[**n**] argumenty do *formátu* řetězce, pomocí stejných pravidel definované **printf** nebo **wprintf** funkce. Tyto funkce generování sestav o ladění a určení cílového nebo cíle, podle režimů aktuální sestavy, a soubor definované pro *reportType*. Odeslání sestavy do okno zprávy ladění *filename*, **lineNumber**, a *moduleName* jsou součástí informace zobrazené v okně.

V následující tabulce jsou uvedeny dostupné možnosti pro režim sestav nebo režimy souboru a výsledné chování **_crtdbgreport –** a **_crtdbgreportw –**. Tyto možnosti jsou definovány jako bitové příznaky v \<crtdbg.h >.

|Sestava režimu|Soubor sestavy|**_Crtdbgreport –**, **_crtdbgreportw –** chování|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|Nelze použít|Zapíše zprávu pomocí Windows [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) rozhraní API.|
|**_CRTDBG_MODE_WNDW**|Nelze použít|Volání Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) rozhraní API pro vytvoření okno se zprávou k zobrazení zprávy spolu s **Abort**, **opakujte**, a **Ignorovat** tlačítka. Pokud uživatel klikne **Abort**, **_crtdbgreport –** nebo **_crtdbgreport –** hned zruší. Pokud uživatel klikne **opakujte**, vrátí hodnotu 1. Pokud uživatel klikne **Ignorovat**, pokračuje v provádění a **_crtdbgreport –** a **_crtdbgreportw –** vrátit 0. Všimněte si, že kliknete na **Ignorovat** při chybový stav existuje často za následek "nedefinované chování."|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Uživatelem zadané zprávy zápisy **zpracování**, pomocí Windows [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747.aspx) rozhraní API a nemá není ověřte platnost popisovač souboru; aplikace je zodpovědná za otevírání souboru sestavy a předání platný soubor. Obslužná rutina.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Zápisy zprávu **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Zápisy zprávu **stdout**.|

Sestavu lze odesílat na jednu, dvě nebo tři cíle nebo na žádný cíl vůbec. Další informace o zadávání sestavy režim nebo režim a soubor sestavy najdete v tématu [_crtsetreportmode –](crtsetreportmode.md) a [_crtsetreportfile –](crtsetreportfile.md) funkce. Další informace o použití maker ladění a funkce vytváření sestav najdete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting).

Pokud aplikace potřebuje více flexibility než poskytnutá **_crtdbgreport –** a **_crtdbgreportw –**, můžete napsat vlastního reporting funkce a propojte ho do reporting běhové knihovny jazyka C mechanismus pomocí [_crtsetreporthook –](crtsetreporthook.md) funkce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_Crtdbgreport –** a **_crtdbgreportw –** jsou rozšíření Microsoft. Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

```C
// crt_crtdbgreport.c
#include <crtdbg.h>

int main(int argc, char *argv[]) {
#ifdef _DEBUG
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);
#endif
}
```

V tématu [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2) příklad toho, jak změnit funkci sestav.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
