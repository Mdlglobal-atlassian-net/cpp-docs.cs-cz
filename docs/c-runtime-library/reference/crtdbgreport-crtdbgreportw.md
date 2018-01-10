---
title: "_Crtdbgreport –, _crtdbgreportw – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a2f148b031312db10449c6f33c67b94f6e171c5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW
Vytváří sestavu ladění zprávou a odešle sestavy tři možné cíle (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `reportType`  
 Typ sestavy: `_CRT_WARN`, `_CRT_ERROR`, a `_CRT_ASSERT`.  
  
 `filename`  
 Ukazatel na název zdrojového souboru, kde došlo k chybě vyhodnocení či sestavy nebo `NULL`.  
  
 `linenumber`  
 Číslo řádku na zdrojový soubor, kde došlo k chybě vyhodnocení či sestavy nebo `NULL`.  
  
 `moduleName`  
 Ukazatel na název modulu (.exe nebo .dll) kde assert nebo sestavy došlo k chybě.  
  
 `format`  
 Ukazatel na řetězec formátu – ovládací prvek použitý k vytvoření uživatelské zprávy.  
  
 `argument`  
 Nahrazení volitelné argumenty používané `format`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pro všechny sestavy cílů `_CrtDbgReport` a `_CrtDbgReportW` vrátí -1, pokud dojde k chybě a 0, pokud nedojde k žádným chybám. Ale pokud je cílový sestavy okno zprávy ladění a uživatel klikne **opakujte** tlačítko vrátí tyto funkce 1. Pokud uživatel klikne **Abort** tlačítka v okně zprávy ladění tyto funkce okamžitě přerušit a nevrátí hodnotu.  
  
 [_RPT, _RPTF](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) ladění makra volání `_CrtDbgReport` jejich ladění generování sestav. Široká charakterová verze těchto makra a také [_ASSERT &#91; V &#93; ](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), `_RPTW n` a `_RPTFW n`, použijte `_CrtDbgReportW` jejich ladění generování sestav. Když `_CrtDbgReport` nebo `_CrtDbgReportW` 1, vrátí tato makra spuštění ladicího programu, za předpokladu, že je povoleno ladění v běhu (JIT).  
  
## <a name="remarks"></a>Poznámky  
 `_CrtDbgReport`a `_CrtDbgReportW` můžete odeslat zprávu o ladění tři různé cíle: soubor sestavy ladění, ladění monitorování ( [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] ladicí program), nebo okno zprávy ladění. Dvě konfigurace funkce [_crtsetreportmode –](../../c-runtime-library/reference/crtsetreportmode.md) a [_crtsetreportfile –](../../c-runtime-library/reference/crtsetreportfile.md), slouží k zadání cílového nebo cíle pro každý typ sestavy. Tyto funkce povolit generování sestav cílového nebo cíle pro každý typ sestavy pro samostatně řízení. Například je možné určit, že `reportType` z `_CRT_WARN` pouze se odesílá do monitorování ladění, při `reportType` z `_CRT_ASSERT` odeslat na okno zprávy ladění a soubor vlastní sestavy.  
  
 `_CrtDbgReportW`je verze široká charakterová `_CrtDbgReport`. Všechny její výstup a řetězec parametry jsou v řetězcích široká charakterová; v opačném případě je stejná jako verze znakovou.  
  
 `_CrtDbgReport`a `_CrtDbgReportW` vytvoření uživatelské zprávy ladění sestavy nahrazením `argument`[`n`] argumenty do `format` řetězce, pomocí stejných pravidel definované `printf` nebo `wprintf` funkce. Tyto funkce generování sestav o ladění a určení cílového nebo cíle, podle režimů aktuální sestavy, a soubor definované pro `reportType`. Odeslání sestavy do okno zprávy ladění `filename`, `lineNumber`, a `moduleName` jsou součástí informace zobrazené v okně.  
  
 V následující tabulce jsou uvedeny dostupné možnosti pro režim sestav nebo režimy souboru a výsledné chování `_CrtDbgReport` a `_CrtDbgReportW`. Tyto možnosti jsou definovány jako bitové příznaky v \<crtdbg.h >.  
  
|Sestava režimu|Soubor sestavy|`_CrtDbgReport`, `_CrtDbgReportW` chování|  
|-----------------|-----------------|------------------------------------------------|  
|`_CRTDBG_MODE_DEBUG`|Nelze použít|Zapíše zprávu pomocí Windows [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) rozhraní API.|  
|`_CRTDBG_MODE_WNDW`|Nelze použít|Volání Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) rozhraní API pro vytvoření okno se zprávou k zobrazení zprávy spolu s **Abort**, **opakujte**, a **Ignorovat** tlačítka. Pokud uživatel klikne **Abort**, `_CrtDbgReport` nebo `_CrtDbgReport` hned zruší. Pokud uživatel klikne **opakujte**, vrátí hodnotu 1. Pokud uživatel klikne **Ignorovat**, pokračuje v provádění a `_CrtDbgReport` a `_CrtDbgReportW` vrátit 0. Všimněte si, že kliknete na **Ignorovat** při chybový stav existuje často za následek "nedefinované chování."|  
|`_CRTDBG_MODE_FILE`|`__HFILE`|Uživatelem zadané zprávy zápisy `HANDLE`, pomocí Windows [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747.aspx) rozhraní API a nemá není ověřte platnost popisovač souboru; aplikace je zodpovědná za otevírání souboru sestavy a předání popisovač platný soubor.|  
|`_CRTDBG_MODE_FILE`|`_CRTDBG_FILE_STDERR`|Zápisy zprávu `stderr`.|  
|`_CRTDBG_MODE_FILE`|`_CRTDBG_FILE_STDOUT`|Zápisy zprávu `stdout`.|  
  
 Sestavu lze odesílat na jednu, dvě nebo tři cíle nebo na žádný cíl vůbec. Další informace o zadávání sestavy režim nebo režim a soubor sestavy najdete v tématu [_crtsetreportmode –](../../c-runtime-library/reference/crtsetreportmode.md) a [_crtsetreportfile –](../../c-runtime-library/reference/crtsetreportfile.md) funkce. Další informace o použití maker ladění a funkce vytváření sestav najdete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting).  
  
 Pokud aplikace potřebuje více flexibility než poskytnutá `_CrtDbgReport` a `_CrtDbgReportW`, můžete napsat vlastního reporting funkce a propojte ho do běhové knihovny jazyka C reporting mechanismus pomocí [_crtsetreporthook –](../../c-runtime-library/reference/crtsetreporthook.md)funkce.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_CrtDbgReport`|\<crtdbg.h >|  
|`_CrtDbgReportW`|\<crtdbg.h >|  
  
 `_CrtDbgReport`a `_CrtDbgReportW` jsou rozšíření Microsoft. Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_crtdbgreport.c  
#include <crtdbg.h>  
  
int main(int argc, char *argv[]) {  
#ifdef _DEBUG  
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);  
#endif  
}  
```  
  
 V tématu [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167) příklad toho, jak změnit funkci sestav.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_Crtsetreportmode –](../../c-runtime-library/reference/crtsetreportmode.md)   
 [_Crtsetreportfile –](../../c-runtime-library/reference/crtsetreportfile.md)   
 [printf, _printf_l –, wprintf, _wprintf_l –](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [_DEBUG](../../c-runtime-library/debug.md)