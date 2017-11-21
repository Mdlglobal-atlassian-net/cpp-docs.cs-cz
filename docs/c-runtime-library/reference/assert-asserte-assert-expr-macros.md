---
title: "_ASSERT, _asserte –, _ASSERT_EXPR makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
- _ASSERTE
- ASSERTE
- _ASSERT
- _ASSERT_EXPR
dev_langs: C++
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 44141622fa2fa760338109820ad185fb4e1e3ecf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="assert-asserte-assertexpr-macros"></a>_ASSERT, _asserte –, _ASSERT_EXPR makra
Vyhodnocení výrazu a vygenerovat sestavu ladění, když je výsledkem `False` (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_ASSERT_EXPR(  
   booleanExpression,  
   message  
);  
_ASSERT(   
   booleanExpression   
);  
_ASSERTE(   
   booleanExpression   
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Skalární výraz, který (včetně výrazy ukazatelů), která vyhodnotí nenulové hodnoty (pravda) nebo 0 (false).  
  
 `message`  
 Široké řetězec k zobrazení v rámci sestavy.  
  
## <a name="remarks"></a>Poznámky  
 `_ASSERT_EXPR`, `_ASSERT` a `_ASSERTE` makra poskytnout vyčištění a jednoduchý mechanismus pro kontrolu předpokladů během procesu ladění aplikace. Jsou velmi flexibilní, protože není potřeba být uzavřená do `#ifdef` příkazy, aby nebylo volal v prodejní sestavení aplikace. Tato možnost je dosaženo pomocí [_DEBUG –](../../c-runtime-library/debug.md) makro. `_ASSERT_EXPR`, `_ASSERT` a `_ASSERTE` jsou k dispozici pouze při `_DEBUG` je definována v době kompilace. Když `_DEBUG` není definována, volání makra jsou odebrány při předběžném zpracování.  
  
 `_ASSERT_EXPR`, `_ASSERT` a `_ASSERTE` vyhodnotit jejich `booleanExpression` argument a výsledek je `false` (0), budou tisknout diagnostické zprávy a volání [_crtdbgreportw –](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) k vygenerování sestavy ladění. `_ASSERT` Makro vytiskne jednoduché diagnostické zprávy, `_ASSERTE` zahrnuje řetězcovou reprezentaci výrazu se nezdařilo ve zprávě, a `_ASSERT_EXPR` zahrnuje `message` řetězec v diagnostické zprávy. Tyto makra nedělat nic při `booleanExpression` vyhodnocen jako nenulové hodnoty.  
  
 `_ASSERT_EXPR`, `_ASSERT` a `_ASSERTE` vyvolání `_CrtDbgReportW`, což způsobí, že veškerý výstup v široké znaky. `_ASSERTE`správně vytiskne znaky kódování Unicode v `booleanExpression` a `_ASSERT_EXPR` vytiskne znaky kódování Unicode v `message`.  
  
 Protože `_ASSERTE` makro Určuje výraz se nezdařila, a `_ASSERT_EXPR` umožňuje zadat zprávu v vygenerovanou sestavu, umožňují uživatelům určit problém bez odkazující ke zdrojovému kódu aplikace. Ale nevýhodou existuje v tom, že každý `message` tištěné `_ASSERT_EXPR` a každý výraz vyhodnocovaný `_ASSERTE` je zahrnutá ve výstupním souboru (ladicí verze) vaší aplikace jako řetězcová konstanta. Proto pokud velký počet volání `_ASSERT_EXPR` nebo `_ASSERTE`, těchto výrazů může výrazně zvýšit velikost výstupního souboru.  
  
 Pokud neurčíte jinak s [_crtsetreportmode –](../../c-runtime-library/reference/crtsetreportmode.md) a [_crtsetreportfile –](../../c-runtime-library/reference/crtsetreportfile.md) funguje, zprávy se zobrazují v místním dialogovém okně ekvivalentní k nastavení:  
  
`_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);`  
  
 `_CrtDbgReportW`vytváří sestavu ladění a určuje jeho cílového nebo cíle, na základě aktuální režim sestav nebo režimy a soubor definice pro `_CRT_ASSERT` typu Sestava. Ve výchozím nastavení selhání vyhodnocení a chyb jsou směrované okno zprávy ladění. [_Crtsetreportmode –](../../c-runtime-library/reference/crtsetreportmode.md) a [_crtsetreportfile –](../../c-runtime-library/reference/crtsetreportfile.md) funkce slouží k určení cíle pro každý typ sestavy.  
  
 Pokud je cílem okno zprávy ladění a uživatel klikne **opakujte** tlačítko `_CrtDbgReportW` vrátí hodnotu 1, způsobuje `_ASSERT_EXPR`, `_ASSERT` a `_ASSERTE` maker, pro spuštění ladicího programu za předpokladu, že je povolené ladění v běhu (JIT).  
  
 Další informace o procesu vytváření sestav najdete v tématu [_crtdbgreport –, _crtdbgreportw –](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) funkce. Další informace o řešení chyb kontrolní výraz a použití těchto maker jako ladění chyba mechanismu pro zpracování najdete v tématu [pomocí makra pro ověření a vytváření sestav](/visualstudio/debugger/macros-for-reporting).  
  
 Kromě `_ASSERT` makra, [assert](../../c-runtime-library/reference/assert-macro-assert-wassert.md) makro může sloužit k ověření program logiku. Toto makro je k dispozici v ladění a vydání verze knihoven. [_RPT, _RPTF](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) makra ladění jsou také k dispozici pro generování sestavy ladění, ale nevyhodnocují výrazu. `_RPT` Makra generovat jednoduchou sestavu. `_RPTF` Makra obsahují zdrojový soubor a řádku číslo kde byl volán makro sestavy v vygenerovanou sestavu. Široká znaková verze těchto makra jsou k dispozici (`_RPTWn`, `_RPTFWn`). Široká znaková verze jsou shodné s verzí úzké znak s tím rozdílem, že široká znaková řetězce se používají pro všechny parametry řetězce a výstup.  
  
 I když `_ASSERT_EXPR`, `_ASSERT` a `_ASSERTE` jsou makra a jsou k dispozici zahrnutím \<crtdbg.h >, aplikace se musí propojit s verzí ladicí běhové knihovny jazyka C při `_DEBUG` je definován, protože tyto makra volání Další běhové funkce.  
  
## <a name="requirements"></a>Požadavky  
  
|– Makro|Požadovaný hlavičkový soubor|  
|-----------|---------------------|  
|`_ASSERT_EXPR`,                  `_ASSERT`, `_ASSERTE`|\<crtdbg.h >|  
  
## <a name="example"></a>Příklad  
 V tomto programu volání `_ASSERT` a `_ASSERTE` makra, která otestuje podmínku `string1 == string2`. V případě selhání podmínku tyto makra tisk diagnostické zprávy. `_RPTn` a `_RPTFn` skupinu maker je také provést tento program jako alternativu k `printf` funkce.  
  
```C  
// crt_ASSERT_macro.c  
// compile with: /D_DEBUG /MTd /Od /Zi /link /verbose:lib /debug  
//  
// This program uses the _ASSERT and _ASSERTE debugging macros.  
//  
  
#include <stdio.h>  
#include <string.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main()  
{  
   char *p1, *p2;  
  
   // The Reporting Mode and File must be specified  
   // before generating a debug report via an assert  
   // or report macro.  
   // This program sends all report types to STDOUT.  
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);  
   _CrtSetReportFile(_CRT_WARN, _CRTDBG_FILE_STDOUT);  
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);  
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDOUT);  
   _CrtSetReportMode(_CRT_ASSERT, _CRTDBG_MODE_FILE);  
   _CrtSetReportFile(_CRT_ASSERT, _CRTDBG_FILE_STDOUT);  
  
   // Allocate and assign the pointer variables.  
   p1 = (char *)malloc(10);  
   strcpy_s(p1, 10, "I am p1");  
   p2 = (char *)malloc(10);  
   strcpy_s(p2, 10, "I am p2");  
  
   // Use the report macros as a debugging  
   // warning mechanism, similar to printf.  
   // Use the assert macros to check if the   
   // p1 and p2 variables are equivalent.  
   // If the expression fails, _ASSERTE will  
   // include a string representation of the  
   // failed expression in the report.  
   // _ASSERT does not include the  
   // expression in the generated report.  
   _RPT0(_CRT_WARN,  
       "Use the assert macros to evaluate the expression p1 == p2.\n");  
   _RPTF2(_CRT_WARN, "\n Will _ASSERT find '%s' == '%s' ?\n", p1, p2);  
   _ASSERT(p1 == p2);  
  
   _RPTF2(_CRT_WARN, "\n\n Will _ASSERTE find '%s' == '%s' ?\n",  
          p1, p2);  
   _ASSERTE(p1 == p2);  
  
   _RPT2(_CRT_ERROR, "'%s' != '%s'\n", p1, p2);  
  
   free(p2);  
   free(p1);  
  
   return 0;  
}  
```  
  
```Output  
Use the assert macros to evaluate the expression p1 == p2.  
crt_ASSERT_macro.c(54) :   
 Will _ASSERT find 'I am p1' == 'I am p2' ?  
crt_ASSERT_macro.c(55) : Assertion failed!  
crt_ASSERT_macro.c(58) :   
  
 Will _ASSERTE find 'I am p1' == 'I am p2' ?  
crt_ASSERT_macro.c(59) : Assertion failed: p1 == p2  
'I am p1' != 'I am p2'  
```  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [Assert – makro, _assert, _wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [_RPT, _RPTF, _RPTW, _rptfw – makra](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)