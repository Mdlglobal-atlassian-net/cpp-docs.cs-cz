---
title: _ASSERT, _asserte –, _ASSERT_EXPR makra | Dokumentace Microsoftu
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
- _ASSERTE
- ASSERTE
- _ASSERT
- _ASSERT_EXPR
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 254550acf94acb846826bc0efe76ef26753c54b8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107585"
---
# <a name="assert-asserte-assertexpr-macros"></a>_ASSERT, _asserte –, _ASSERT_EXPR makra

Vyhodnocení výrazu a vygenerovat sestavu ladění, když je výsledkem **False** (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Skalární výraz, který (včetně výrazy ukazatelů), který se vyhodnotí nenulová (pravda), nebo 0 (false).

*message*<br/>
Široký řetězec k zobrazení jako součást sestavy.

## <a name="remarks"></a>Poznámky

**_ASSERT_EXPR**, **_ASSERT** a **_asserte –** makra poskytnout přehledné a jednoduchý mechanismus kontroly předpokladů během procesu ladění aplikace. Jsou flexibilní, protože není potřeba nacházet v `#ifdef` příkazy tak tomu, aby se volá v sestavení prodejní verze aplikace. Díky této flexibilitě se dosahuje prostřednictvím využití [_DEBUG](../../c-runtime-library/debug.md) – makro. **_ASSERT_EXPR**, **_ASSERT** a **_asserte –** jsou k dispozici pouze při **_DEBUG** je definován v době kompilace. Když **_DEBUG** není definován, volání makra jsou odstraněna během předběžného zpracování.

**_ASSERT_EXPR**, **_ASSERT** a **_asserte –** vyhodnotit jejich *booleanExpression* argument a výsledkem je **false**(0), vytiskne diagnostickou zprávu a volání [_crtdbgreportw –](crtdbgreport-crtdbgreportw.md) k vygenerování sestav ladění. **_ASSERT** – makro vytiskne jednoduché diagnostickou zprávu **_asserte –** zahrnuje řetězcové vyjádření neúspěšné výraz ve zprávě, a **_ASSERT_EXPR** zahrnuje *zpráva* řetězec v diagnostické zprávě. Tato makra Neprovádět žádnou akci při *booleanExpression* vyhodnocen na nenulovou hodnotu.

**_ASSERT_EXPR**, **_ASSERT** a **_asserte –** vyvolat **_crtdbgreportw –**, což způsobí, že veškerý výstup v širokých znaků. **_Asserte –** správně zobrazí znaky Unicode v *booleanExpression* a **_ASSERT_EXPR** vytiskne znaky kódování Unicode v *zpráva*.

Protože **_asserte –** – makro Určuje výraz, se nezdařilo, a **_ASSERT_EXPR** umožňuje zadat zprávu v generované sestavě, umožňují uživatelům identifikovat problém bez ohledu zdrojový kód aplikace. Nevýhodou existuje však v, které každý *zpráva* zprávy vytištěné funkcí **_ASSERT_EXPR** a každý výraz vyhodnocovaný **_asserte –** je součástí výstupu (ladicí verze) soubor aplikace jako řetězcová konstanta. Proto pokud velký počet volání **_ASSERT_EXPR** nebo **_asserte –**, tyto výrazy může výrazně zvýšit velikost výstupního souboru.

Pokud neurčíte jinak se [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md) funguje, zprávy se zobrazují v místním dialogovém ekvivalentní nastavení:

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_Crtdbgreportw –** generuje sestavu ladění a určuje jeho cíle nebo cílů, na základě aktuální režim sestavy nebo režimech a soubor definice pro **_CRT_ASSERT** typ sestavy. Ve výchozím nastavení chyby a selhání kontrolního výrazu jsou směrované na okno zprávy ladění. [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md) funkce se používají k definování cíle pro každý typ sestavy.

Pokud je cíl okno zprávy ladění a uživatel klikne **opakujte** tlačítko, **_crtdbgreportw –** vrátí hodnotu 1, způsobí **_ASSERT_EXPR**, **_ Kontrolní VÝRAZ** a **_asserte –** makra spuštění ladicího programu, za předpokladu, že je povoleno ladění just-in-time (JIT).

Další informace o procesu vytváření sestav najdete v tématu [_CrtDbgReport _crtdbgreportw –](crtdbgreport-crtdbgreportw.md) funkce. Další informace o řešení selhání kontrolního výrazu a použití těchto maker jako ladění chyba mechanismu pro zpracování, naleznete v tématu [použití maker pro ověřování a vytváření sestav](/visualstudio/debugger/macros-for-reporting).

Kromě **_ASSERT** makra, [vyhodnocení](assert-macro-assert-wassert.md) – makro je použít k ověření logiku programu. Toto makro je k dispozici v ladění a vydání verze knihoven. [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) maker ladění k dispozici také pro generování sestav ladění, ale jejich nelze vyhodnotit výraz. **_RPT** makra generovat jednoduchou sestavu. **_RPTF** makra patří zdrojový soubor a číslo řádku kde byla volána – makro sestavy v generované sestavě. Jsou k dispozici verze širokými znaky těchto maker (**_RPTW**, **_rptfw –**). Verze širokého znaku jsou shodné s verzemi úzkými znaky, s tím rozdílem, že řetězce širokého znaku se používají pro všechny parametry řetězce a výstup.

I když **_ASSERT_EXPR**, **_ASSERT** a **_asserte –** jsou makra a dají se zahrnutím \<crtdbg.h >, je třeba propojit aplikaci s ladění verze knihovny run-time C při **_DEBUG** je definován, protože tato makra volání dalších funkcí za běhu.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-----------|---------------------|
|**_ASSERT_EXPR**, **_ASSERT**, **_ASSERTE –**|\<crtdbg.h>|

## <a name="example"></a>Příklad

V rámci tohoto programu, volání **_ASSERT** a **_asserte –** makra otestuje podmínku `string1 == string2`. Pokud podmínka selže, tato makra vytisknout diagnostickou zprávu. **_RPT** a **_RPTF** skupiny maker se také provede v rámci tohoto programu, jako alternativu k **printf** funkce.

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

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[assert Macro, _assert, _wassert](assert-macro-assert-wassert.md)<br/>
[_RPT, _RPTF, _RPTW, _RPTFW – makra](rpt-rptf-rptw-rptfw-macros.md)<br/>
