---
title: "Assert – makro, _assert, _wassert | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- assert
- _assert
- _wassert
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
dev_langs: C++
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1033ca0767eb84b896e641db4c5ba3b296a7fae1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="assert-macro-assert-wassert"></a>Assert – makro, _assert, _wassert
Vyhodnocuje na výrazu a pokud je výsledek `false`, vytiskne hlášení diagnostiky a zruší program.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
assert(   
   expression   
);  
void _assert(  
   char const* message,  
   char const* filename,  
   unsigned line  
);  
void _wassert(  
   wchar_t const* message,  
   wchar_t const* filename,  
   unsigned line  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `expression`  
 Skalární výraz (včetně výrazy ukazatelů), která vyhodnotí na nenulové hodnoty (`true`) nebo 0 (`false`).  
  
 `message`  
 Zpráva, která se má zobrazit  
  
 `filename`  
 Název zdrojového souboru kontrolní výraz se nezdařilo.  
  
 `line`  
 Číslo řádku ve zdrojovém souboru selhání kontrolního výrazu.  
  
## <a name="remarks"></a>Poznámky  
 `assert` Makro se obvykle používá k identifikaci logické chyby během vývoje aplikace. Použít k zastavení spuštění programu, když dojde k neočekávané podmínky implementací `expression` argument pro vyhodnocení `false` pouze když program pracuje správně. Kontrolní výraz kontroly může být vypnuto v době kompilace definováním makro `NDEBUG`. Můžete vypnout `assert` makro beze změny zdrojových souborů pomocí **/DNDEBUG** možnost příkazového řádku. Můžete vypnout `assert` makro ve zdrojovém kódu pomocí `#define NDEBUG` direktivy před \<assert.h > je součástí.  
  
 `assert` Makro výtisků Diagnostika při zpracování zprávy `expression` vyhodnotí jako `false` (0) a volání [abort](../../c-runtime-library/reference/abort.md) ukončit spuštění programu. Pokud nebyla provedena žádná akce `expression` je `true` (nenulové hodnoty). Diagnostické zprávy je i neúspěšné výrazu, název souboru a řádku číslo zdrojového kde kontrolní výraz se nezdařilo.  
  
 Diagnostické zprávy je vytištěna v široké znaky. Proto bude fungovat podle očekávání, i když jsou ve výrazu znaky znakové sady Unicode.  
  
 Cíl diagnostiky zprávy závisí na typu aplikace, která volá rutiny. Konzolové aplikace vždy zobrazí se zpráva prostřednictvím `stderr`. V aplikaci systému Windows `assert` volá Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) funkce vytvořit okno se zprávou k zobrazení zprávy spolu s **OK** tlačítko. Když uživatel klikne na **OK**, program zruší okamžitě.  
  
 Když aplikace je spojená s verzí ladicí běhové knihovny `assert` vytvoří okno se zprávou s tři tlačítka: **Abort**, **opakujte**, a **Ignorovat**. Pokud uživatel klikne na **Abort**, program zruší okamžitě. Pokud uživatel klikne na **opakujte**, se nazývá ladicího programu a uživatele můžete ladit program, pokud je povoleno ladění v běhu (JIT). Pokud uživatel klikne na **Ignorovat**, `assert` pokračuje v jeho normální spuštění: vytváření zprávou s **OK** tlačítko. Všimněte si, že kliknete na **Ignorovat** když existuje chybový stav může vést k nedefinované chování.  
  
 Další informace o ladění CRT najdete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).  
  
 `_assert` a `_wassert` funkce jsou interní CRT funkce. Pomáhají minimalizovat kód v objektu soubory potřebné k podpoře kontrolní výrazy. Nedoporučujeme přímo volat tyto funkce.  
  
 `assert` Makro je povoleno ladění a vydání verze běhové knihovny jazyka C při `NDEBUG` není definován. Když `NDEBUG` je definován, makro je k dispozici, ale nelze vyhodnotit její argument a nemá žádný vliv. Pokud je povolena, `assert` makro volání `_wassert` pro jeho implementace. Ostatní makra assertion [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), [_asserte –](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) a [_ASSERT_EXPR](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), jsou také k dispozici, ale pouze vyhodnocení výrazů předaný je při [_DEBUG –](../../c-runtime-library/debug.md) makro již byl definován, když se kód spojený s verzí ladicí běhové knihovny jazyka C.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`assert`, `_wassert`|\<Assert.h >|  
  
 Podpis `_assert` funkce není k dispozici v záhlaví souboru. Podpis `_wassert` funkce je k dispozici pouze při `NDEBUG` makro není definován.  
  
## <a name="example"></a>Příklad  
 V tomto programu `analyze_string` využívá `assert` makro k testování několik podmínek související s řetězec a délka. Pokud některá z podmínek selže, program zobrazí zprávu s upozorněním, co způsobilo selhání.  
  
```  
// crt_assert.c  
// compile by using: cl /W4 crt_assert.c  
#include <stdio.h>  
#include <assert.h>  
#include <string.h>  
  
void analyze_string( char *string );   // Prototype  
  
int main( void )  
{  
   char  test1[] = "abc", *test2 = NULL, test3[] = "";  
  
   printf ( "Analyzing string '%s'\n", test1 ); fflush( stdout );  
   analyze_string( test1 );  
   printf ( "Analyzing string '%s'\n", test2 ); fflush( stdout );  
   analyze_string( test2 );  
   printf ( "Analyzing string '%s'\n", test3 ); fflush( stdout );  
   analyze_string( test3 );  
}  
  
// Tests a string to see if it is NULL,   
// empty, or longer than 0 characters.  
void analyze_string( char * string )  
{  
   assert( string != NULL );        // Cannot be NULL  
   assert( *string != '\0' );       // Cannot be empty  
   assert( strlen( string ) > 2 );  // Length must exceed 2  
}  
```  
  
 Program generuje tento výstup:  
  
```Output  
Analyzing string 'abc'  
Analyzing string '(null)'  
Assertion failed: string != NULL, file crt_assert.c, line 25  
```  
  
 Po selhání assertion, v závislosti na verzi operačního systému a běhové knihovny může se zobrazit okno se zprávou, která obsahuje přibližně takto:  
  
```Output  
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.  
```  
  
 Pokud je nainstalovaná ladicí program, vyberte **ladění** tlačítko spuštění ladicího programu, nebo **ukončení programu** ukončíte.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování chyb](../../c-runtime-library/error-handling-crt.md)   
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [vyvolat](../../c-runtime-library/reference/raise.md)   
 [signál](../../c-runtime-library/reference/signal.md)   
 [_ASSERT, _asserte –, _ASSERT_EXPR makra](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [_DEBUG –](../../c-runtime-library/debug.md)