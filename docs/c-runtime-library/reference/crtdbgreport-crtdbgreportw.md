---
title: _CrtDbgReport, _CrtDbgReportW
ms.date: 11/04/2016
api_name:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
ms.openlocfilehash: 986777f755a749e858f7e51b5aa19f10090db13a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938838"
---
# <a name="_crtdbgreport-_crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

Vygeneruje sestavu se zprávou ladění a odešle ji do tří možných cílů (pouze ladicí verze).

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
Typ sestavy: **_CRT_WARN**, **_CRT_ERROR**a **_CRT_ASSERT**.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, kde došlo k vyhodnocení/sestavě nebo je **null**.

*číslo řádku*<br/>
Číslo řádku ve zdrojovém souboru, kde došlo k vyhodnocení nebo sestavě nebo je **null**.

*moduleName*<br/>
Ukazatel na název modulu (. exe nebo. dll), kde došlo k vyhodnocení nebo sestavě.

*format*<br/>
Ukazatel na řetězec řízení formátu použitý k vytvoření zprávy uživatele.

*argument*<br/>
Volitelné substituční argumenty používané *formátem*.

## <a name="return-value"></a>Návratová hodnota

U všech cílů sestav **_CrtDbgReport** a **_CrtDbgReportW** vrátí-1, pokud dojde k chybě, a 0, pokud nebyly zjištěny žádné chyby. Pokud je však cílem sestavy okno zprávy ladění a uživatel klikne na tlačítko **Opakovat** , tyto funkce vrátí hodnotu 1. Pokud uživatel klikne na tlačítko **přerušit** v okně zprávy ladění, tyto funkce okamžitě přeruší a nevrátí hodnotu.

Makra [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) ladění volají **_CrtDbgReport** pro generování jejich sestav ladění. Verze těchto maker pro nejrůznější znaky a také [_ASSERT, _ASSERTE](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) a [_RPTFW](rpt-rptf-rptw-rptfw-macros.md)použijte **_CrtDbgReportW** pro generování jejich sestav ladění. Když **_CrtDbgReport** nebo **_CrtDbgReportW** vrátí 1, tato makra spustí ladicí program za předpokladu, že je povoleno ladění JIT (just-in-time).

## <a name="remarks"></a>Poznámky

**_CrtDbgReport** a **_CrtDbgReportW** mohou odeslat sestavu ladění do tří různých umístění: soubor sestavy ladění, monitor ladění (ladicí program sady Visual Studio) nebo okno zprávy ladění. Dvě konfigurační funkce, [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md), se používají k určení cíle nebo cílových umístění pro každý typ sestavy. Tyto funkce umožňují, aby byly cíle a umístění sestav pro jednotlivé typy sestav samostatně ovládány. Například je možné určit, že se *ReportType* **_CRT_WARN** pouze pošle do monitorování ladění, zatímco *ReportType* **_CRT_ASSERT** se pošle oknu zprávy ladění a uživatelem definovaným souborem sestavy.

**_CrtDbgReportW** je verze **_CrtDbgReport**pro nejrůznější znaky. Všechny parametry výstupu a řetězce jsou v řetězcích s velkým znakem; v opačném případě je stejný jako znaková verze s jedním bajtem.

**_CrtDbgReport** a **_CrtDbgReportW** vytvoří uživatelskou zprávu pro sestavu ladění nahrazením argumentů [**n** *] v řetězci* *formátu* pomocí stejných pravidel definovaných v **printf** nebo  **funkce wprintf** Tyto funkce pak vygenerují sestavu ladění a určí cíl nebo cíle na základě aktuálního režimu sestavy a souboru definovaného pro *ReportType*. Když se sestava pošle do okna zprávy ladění, *názvy souborů*, **číslo řádku**a *Module* jsou zahrnuté do informací zobrazených v okně.

Následující tabulka uvádí dostupné možnosti pro režim sestavy nebo režimy a soubor a výsledné chování **_CrtDbgReport** a **_CrtDbgReportW**. Tyto možnosti jsou definovány jako bitové příznaky v \<souboru Crtdbg. h >.

|Režim sestavy|Soubor sestavy|**_CrtDbgReport**, chování **_CrtDbgReportW**|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|Nelze použít|Zapisuje zprávu pomocí rozhraní Windows [OutputDebugString](/windows/win32/api/debugapi/nf-debugapi-outputdebugstringw) API.|
|**_CRTDBG_MODE_WNDW**|Nelze použít|Volá rozhraní Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) API k vytvoření okna se zprávou pro zobrazení zprávy s tlačítky **přerušení**, **Opakovat**a **Ignorovat** . Pokud uživatel klikne na **přerušení**, **_CrtDbgReport** nebo **_CrtDbgReport** se okamžitě přeruší. Pokud uživatel klikne na tlačítko **Opakovat**, vrátí hodnotu 1. Pokud uživatel klikne na **Ignorovat**, provádění pokračuje a **_CrtDbgReport** a **_CrtDbgReportW** vrátí hodnotu 0. Všimněte si, že kliknutí na **Ignorovat** , pokud existuje chybový stav, často vede k nedefinovanému chování.|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Zapíše zprávu do uživatelsky zadaného **popisovače**pomocí rozhraní Windows [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) API a neověřuje platnost popisovače souboru; aplikace zodpovídá za otevření souboru sestavy a předání platného popisovače souboru.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Zapíše zprávu do **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Zapíše zprávu do **stdout**.|

Tato sestava se dá poslat na jednu, dvě nebo tři cíle nebo do žádného cíle. Další informace o tom, jak zadat režim sestavy nebo režimy a soubor sestavy, najdete v tématu funkce [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md) . Další informace o použití maker ladění a funkcí vytváření sestav naleznete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting).

Pokud vaše aplikace potřebuje větší flexibilitu než ta, kterou poskytuje **_CrtDbgReport** a **_CrtDbgReportW**, můžete napsat vlastní funkci vytváření sestav a zapojit ji do mechanismu generování sestav běhové knihovny jazyka C pomocí [_CrtSetReportHook](crtsetreporthook.md) slouží.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport** a **_CrtDbgReportW** jsou rozšíření společnosti Microsoft. Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

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

Příklad, jak změnit funkci sestavy, naleznete v tématu [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
