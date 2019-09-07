---
title: Makra _ASSERT, _ASSERTE, _ASSERT_EXPR
ms.date: 11/04/2016
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
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
ms.openlocfilehash: d2d83c3afa8e22c1f75480fe2afefa8bf68be858
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740013"
---
# <a name="_assert-_asserte-_assert_expr-macros"></a>Makra _ASSERT, _ASSERTE, _ASSERT_EXPR

Vyhodnoťte výraz a vygenerujte sestavu ladění, pokud je výsledek **nepravdivý** (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Skalární výraz (včetně výrazů ukazatelů), který vyhodnocuje nenulovou hodnotu (true) nebo 0 (false).

*message*<br/>
Celý řetězec, který se má zobrazit jako součást sestavy.

## <a name="remarks"></a>Poznámky

Makra **_ASSERT_EXPR**, **_ASSERT** a **_ASSERTE** poskytují aplikaci s čistým a jednoduchým mechanismem pro kontrolu předpokladů během procesu ladění. Jsou velmi flexibilní, protože nemusí být uzavřeny do `#ifdef` příkazů, aby se zabránilo jejich volání v maloobchodním sestavení aplikace. Tato flexibilita se dosahuje pomocí makra [_DEBUG](../../c-runtime-library/debug.md) . **_ASSERT_EXPR**, **_ASSERT** a **_ASSERTE** jsou k dispozici, pouze pokud je **_DEBUG** definováno v době kompilace. Když není definovaný **_DEBUG** , volání těchto maker se během předběžného zpracování odeberou.

**_ASSERT_EXPR**, **_ASSERT** a **_ASSERTE** vyhodnotí svůj argument *booleanExpression* a pokud je výsledek **false** (0), vytiskněte diagnostickou zprávu a zavolejte [_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) pro vygenerování sestavy ladění. Makro **_ASSERT** vytiskne jednoduchou diagnostickou zprávu, **_ASSERTE** zahrnuje řetězcovou reprezentaci neúspěšného výrazu ve zprávě a **_ASSERT_EXPR** zahrnuje řetězec *zprávy* v diagnostice zprávě. Tato makra nedělají nic, když se *booleanExpression* vyhodnotí jako nenulové.

**_ASSERT_EXPR**, **_ASSERT** a **_ASSERTE** vyvolávají **_CrtDbgReportW**, což způsobí, že veškerý výstup bude v celých znacích. **_ASSERTE** správně tiskne znaky Unicode v *booleanExpression* a **_ASSERT_EXPR** tiskne znaky Unicode ve *zprávě*.

Protože makro **_ASSERTE** určuje výraz, který selhal, a **_ASSERT_EXPR** umožňuje určit zprávu ve vygenerované sestavě, umožní uživatelům identifikovat problém bez odkazování na zdrojový kód aplikace. Nicméně nevýhody existuje v tom, že každá *zpráva* vytištěná pomocí **_ASSERT_EXPR** a každý výraz vyhodnocený **_ASSERTE** je obsažen ve výstupním souboru (ladicí verze) aplikace jako řetězcová konstanta. Proto pokud je proveden velký počet volání **_ASSERT_EXPR** nebo **_ASSERTE**, mohou tyto výrazy významně zvětšit velikost výstupního souboru.

Pokud neurčíte jinak s funkcemi [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md) , zobrazí se zprávy v automaticky otevíraném dialogovém okně, které odpovídá nastavení:

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW** vygeneruje sestavu ladění a určí její cíl nebo cíl na základě aktuálního režimu sestavy nebo režimů a souboru definovaného pro typ sestavy **_CRT_ASSERT** . Ve výchozím nastavení jsou chyby kontrolního výrazu a chyby směrovány do okna zprávy ladění. Funkce [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md) slouží k definování cílových umístění pro každý typ sestavy.

Když je cílem okno zprávy ladění a uživatel klikne na tlačítko **Opakovat** , vrátí **_CrtDbgReportW** hodnotu 1, což způsobí, že makra **_ASSERT_EXPR**, **_ASSERT** a **_ASSERTE** spustí ladicí program, který poskytuje. ladění JIT (just-in-time) je povoleno.

Další informace o procesu vytváření sestav najdete v tématu funkce [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) . Další informace o řešení selhání kontrolního výrazu a použití těchto maker jako mechanismu pro zpracování chyb ladění naleznete v tématu [použití maker pro ověřování a vytváření sestav](/visualstudio/debugger/macros-for-reporting).

Kromě maker **_ASSERT** lze použít makro [Assert](assert-macro-assert-wassert.md) k ověření logiky programu. Toto makro je k dispozici jak v ladicích, tak ve verzích verze knihoven. [_RPT,](rpt-rptf-rptw-rptfw-macros.md) makra ladění _RPTF jsou také k dispozici pro generování sestavy ladění, ale nevyhodnotí výraz. Makra **_RPT** generují jednoduchou sestavu. Makra **_RPTF** zahrnují zdrojový soubor a číslo řádku, kde bylo makro sestavy voláno ve vygenerované sestavě. K dispozici jsou verze pro nejrůznější znaky těchto maker ( **_RPTW**, **_RPTFW**). Verze s velkým znakem jsou stejné jako úzké znakové verze s tím rozdílem, že řetězce s velkým znakem se používají pro všechny řetězcové parametry a výstupy.

I když jsou **_ASSERT_EXPR**, **_ASSERT** a **_ASSERTE** makra \<a jsou k dispozici pomocí příkazu souboru Crtdbg. h >, aplikace musí propojit s ladicí verzí knihovny run-time jazyka C, pokud je definována **_DEBUG** , protože Tato makra volají jiné běhové funkce.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-----------|---------------------|
|**_ASSERT_EXPR**, **_ASSERT**, **_ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>Příklad

V tomto programu jsou voláním makra **_ASSERT** a **_ASSERTE** pro otestování podmínky `string1 == string2`. Pokud se podmínka nezdařila, tyto makra vytiskněte diagnostickou zprávu. Skupina **_RPT** a **_RPTF** maker je také vykonávána v tomto programu, jako alternativa k funkci **printf** .

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
