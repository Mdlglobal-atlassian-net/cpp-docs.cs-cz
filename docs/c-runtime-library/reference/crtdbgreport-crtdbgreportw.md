---
title: _CrtDbgReport _crtdbgreportw – | Dokumentace Microsoftu
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
ms.openlocfilehash: 5aa7efb7881b00933afab92a7157c09e0f769605
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204420"
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

Vygeneruje sestavu se zprávou ladicího programu a odešle zprávu do tří možných cílů (pouze ladicí verze).

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
Ukazatel na název zdrojového souboru, kde došlo k vyhodnocení/sestavě nebo **NULL**.

*Číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde došlo k vyhodnocení/sestavě nebo **NULL**.

*Název modulu:*<br/>
Ukazatel na název modulu (.exe nebo .dll) Pokud kontrolní výraz nebo došlo k sestavě.

*Formát*<br/>
Ukazatel na řetězec řízení formátu použitý k vytvoření zprávy pro uživatele.

*Argument*<br/>
Volitelné argumenty nahrazení použité ve *formátu*.

## <a name="return-value"></a>Návratová hodnota

Pro všechna místa určení sestavy **_CrtDbgReport** a **_crtdbgreportw –** vrátí -1, pokud dojde k chybě a 0, pokud nedojde k žádným chybám. Nicméně, pokud je cílem sestavy okno zprávy ladění a uživatel klikne **opakujte** tlačítko, vrátí tyto funkce 1. Pokud uživatel klikne **přerušit** tlačítka v okně zprávy ladění, tyto funkce okamžitě zrušit a nesmí vracet hodnotu.

[_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) ladění volání makra **_CrtDbgReport** ladění generování sestav. Verze širokými znaky těchto maker a také [_ASSERT, _asserte –](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) a [_rptfw –](rpt-rptf-rptw-rptfw-macros.md), použijte **_crtdbgreportw –** do generování svých sestav ladění. Když **_CrtDbgReport** nebo **_crtdbgreportw –** vrátí 1, tato makra spustí ladicí program, za předpokladu, že je povoleno ladění just-in-time (JIT).

## <a name="remarks"></a>Poznámky

**_CrtDbgReport** a **_crtdbgreportw –** mohou zaslat sestavu ladění na tři různé cíle: soubor sestavy ladění, sledování ladění (ladicí program sady Visual Studio) nebo okno zprávy ladění. Dvě konfigurační funkce [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md), se používají k určení cíle nebo cílů pro každý typ sestavy. Tyto funkce umožňují vytváření sestav cíle nebo cílů pro každý typ sestavy chcete ovládat samostatně. Například je možné určit, že *reportType* z **_CRT_WARN** pouze se odesílá do sledování ladění, zatímco *reportType* z **_CRT_ASSERT** odešlou do okna zpráv ladění a soubor sestavy definovaný uživatelem.

**_Crtdbgreportw –** je verze širokého znaku **_CrtDbgReport**. Jsou všechny jeho parametry výstupu a řetězce v řetězce širokého znaku; jinak je stejná jako verze jednobajtových znaků.

**_CrtDbgReport** a **_crtdbgreportw –** vytvoří uživatelskou zprávu pro sestavu ladění nahrazením *argument*[**n**] argumenty do *formátu* řetězce, pomocí stejných pravidel definovaných funkcemi **printf** nebo **wprintf** funkce. Tyto funkce potom vygenerují sestavu ladění a určí cíl nebo cíle založené na aktuálních režimech sestavy a souboru definovaném pro *reportType*. Při odesílání sestavy oknu zprávy ladění, *filename*, **lineNumber**, a *moduleName* jsou zahrnuty v informacích zobrazených v okně.

Následující tabulka uvádí dostupné možnosti pro sestavu režimu nebo režimů a souborovou službu a výsledné chování **_CrtDbgReport** a **_crtdbgreportw –**. Tyto možnosti jsou definovány jako bitové příznaky v \<crtdbg.h >.

|Režim sestavy|Soubor sestavy|**_CrtDbgReport**, **_crtdbgreportw –** chování|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|Nelze použít|Zapíše zprávu s použitím Windows [OutputDebugString](https://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) rozhraní API.|
|**_CRTDBG_MODE_WNDW**|Nelze použít|Volání Windows [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) rozhraní API k vytvoření okna zprávy pro zobrazení zprávy spolu s **přerušit**, **opakujte**, a **Ignorovat** tlačítka. Pokud uživatel klikne **přerušit**, **_CrtDbgReport** nebo **_CrtDbgReport** ihned přeruší. Pokud uživatel klikne **opakujte**, vrátí hodnotu 1. Pokud uživatel klikne **Ignorovat**, provádění pokračuje a **_CrtDbgReport** a **_crtdbgreportw –** vrátí 0. Všimněte si, že kliknete na **Ignorovat** při existenci chybového stavu má často za následek "nedefinované chování".|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Zapíše zprávu do uživatelem zadané **zpracování**, pomocí Windows [WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile) rozhraní API a neověřuje platnost popisovače souboru; aplikace je zodpovědná za otevření souboru sestavy a předání platný soubor Obslužná rutina.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Zapíše zprávu do **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Zapíše zprávu do **stdout**.|

Sestavu lze odesílat na jeden, dva nebo tři cíle nebo žádný cíl vůbec. Další informace o zadávání sestava režimu nebo režimů a soubor sestavy naleznete v tématu [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md) funkce. Další informace o použití maker ladění a funkcí vykazování viz [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting).

Pokud vaše aplikace potřebuje více flexibility než poskytuje **_CrtDbgReport** a **_crtdbgreportw –**, můžete napsat vlastní funkci vykazování a zapojit ji do vykazování běhové knihovny jazyka C mechanismus pomocí [_CrtSetReportHook](crtsetreporthook.md) funkce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport** a **_crtdbgreportw –** jsou rozšíření společnosti Microsoft. Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

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

Zobrazit [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2) příklad toho, jak změnit funkci sestavy.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
