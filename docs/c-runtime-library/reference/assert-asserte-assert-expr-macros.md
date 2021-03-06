---
title: _ASSERT, _ASSERTE _ASSERT_EXPR maker
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
- _ASSERTE
- ASSERTE
- _ASSERT_EXPR
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
ms.openlocfilehash: 26a1439e4de8824edd11af1afd455d2b2c31c088
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443073"
---
# <a name="_assert-_asserte-_assert_expr-macros"></a>_ASSERT, _ASSERTE _ASSERT_EXPR maker

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

Makra **_ASSERT_EXPR**, **_ASSERT** a **_ASSERTE** poskytují aplikaci s čistým a jednoduchým mechanismem pro kontrolu předpokladů během procesu ladění. Jsou velmi flexibilní, protože nemusí být uzavřeny v `#ifdef` příkazy, aby se zabránilo jejich volání v maloobchodním sestavení aplikace. Tato flexibilita se dosahuje pomocí [_DEBUGho](../../c-runtime-library/debug.md) makra. **_ASSERT_EXPR** **_ASSERT** a **_ASSERTE** jsou k dispozici, pouze pokud **_DEBUG** je definována v době kompilace. Pokud není definován **_DEBUG** , volání těchto maker budou během předběžného zpracování odebrána.

**_ASSERT_EXPR**, **_ASSERT** a **_ASSERTE** vyhodnotí svůj argument *booleanExpression* a pokud je výsledek **false** (0), vytiskněte diagnostickou zprávu a zavolejte [_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) pro vygenerování sestavy ladění. **_ASSERT** makro vytiskne jednoduchou diagnostickou zprávu, **_ASSERTE** zahrnuje řetězcové vyjádření neúspěšného výrazu ve zprávě a **_ASSERT_EXPR** obsahuje řetězec *zprávy* v diagnostice zprávě. Tato makra nedělají nic, když se *booleanExpression* vyhodnotí jako nenulové.

**_ASSERT_EXPR**, **_ASSERT** a **_ASSERTE** vyvolání **_CrtDbgReportW**, což způsobí, že veškerý výstup bude v celých znacích. **_ASSERTE** správně tisknou znaky Unicode v *booleanExpression* a **_ASSERT_EXPR** ve *zprávě*tiskne znaky Unicode.

Protože makro **_ASSERTE** určuje výraz, který selhal, a **_ASSERT_EXPR** umožňuje určit zprávu ve vygenerované sestavě, umožní uživatelům identifikovat problém bez odkazu na zdrojový kód aplikace. Nevýhoda však existuje v tom, že každá *zpráva* vytištěná **_ASSERT_EXPR** a každý výraz vyhodnocený **_ASSERTE** je obsažen ve výstupním souboru (ladicí verze) aplikace jako řetězcová konstanta. Proto pokud je proveden velký počet volání **_ASSERT_EXPR** nebo **_ASSERTE**, mohou tyto výrazy významně zvětšit velikost výstupního souboru.

Pokud neurčíte jinak pomocí funkce [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md) , zprávy se zobrazí v automaticky otevíraném dialogovém okně, které odpovídá nastavení:

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW** vygeneruje sestavu ladění a určí její cíl nebo umístění na základě aktuálního režimu sestavy nebo režimů a souboru definovaného pro **_CRT_ASSERT** typ sestavy. Ve výchozím nastavení jsou chyby kontrolního výrazu a chyby směrovány do okna zprávy ladění. Funkce [_CrtSetReportMode](crtsetreportmode.md) a [_CrtSetReportFile](crtsetreportfile.md) slouží k definování cílových umístění pro každý typ sestavy.

Když je cílem okno zprávy ladění a uživatel klikne na tlačítko **Opakovat** , **_CrtDbgReportW** vrátí hodnotu 1, což **_ASSERT_EXPR**, **_ASSERT** a makra **_ASSERTE** spustí ladicí program za předpokladu, že je povoleno ladění JIT (just-in-time).

Další informace o procesu vytváření sestav naleznete v části [_CrtDbgReport _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) Function. Další informace o řešení selhání kontrolního výrazu a použití těchto maker jako mechanismu pro zpracování chyb ladění naleznete v tématu [použití maker pro ověřování a vytváření sestav](/visualstudio/debugger/macros-for-reporting).

Kromě makra **_ASSERT** lze použít makro [Assert](assert-macro-assert-wassert.md) k ověření logiky programu. Toto makro je k dispozici jak v ladicích, tak ve verzích verze knihoven. [_RPT _RPTF](rpt-rptf-rptw-rptfw-macros.md) ladicí makra jsou také k dispozici pro generování sestavy ladění, ale nevyhodnotí výraz. Makra **_RPT** generují jednoduchou sestavu. **_RPTF** makra zahrnují zdrojový soubor a číslo řádku, kde bylo makro sestavy voláno ve vygenerované sestavě. Verze libovolného znaku těchto maker jsou k dispozici **_RPTW**(_RPTW **_RPTFW**). Verze s velkým znakem jsou stejné jako úzké znakové verze s tím rozdílem, že řetězce s velkým znakem se používají pro všechny řetězcové parametry a výstupy.

I když **_ASSERT_EXPR**, **_ASSERT** a **_ASSERTE** jsou makra a jsou k dispozici, zahrnutím \<souboru Crtdbg. h >, aplikace musí propojit s ladicí verzí knihovny run-time jazyka C, pokud je definována **_DEBUG** , protože tato makra volají jiné běhové funkce.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-----------|---------------------|
|**_ASSERT_EXPR**, **_ASSERT** **_ASSERTE**|\<souboru Crtdbg. h >|

## <a name="example"></a>Příklad

V tomto programu jsou volána volání **_ASSERT** a **_ASSERTE** makra pro otestování podmínky `string1 == string2`. Pokud se podmínka nezdařila, tyto makra vytiskněte diagnostickou zprávu. V tomto programu je také vykonávána skupina **_RPT** a **_RPTF** maker, jako alternativa k funkci **printf** .

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

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[assert Macro, _assert, _wassert](assert-macro-assert-wassert.md)<br/>
[_RPT, _RPTF, _RPTW, _RPTFW – makra](rpt-rptf-rptw-rptfw-macros.md)<br/>
