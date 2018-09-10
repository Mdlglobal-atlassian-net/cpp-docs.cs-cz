---
title: Assert – makro, _assert, _wassert | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67fef1231d4488b1714cc2f0f2f0e892737e627d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101934"
---
# <a name="assert-macro-assert-wassert"></a>assert Macro, _assert, _wassert

Vyhodnotí výraz a, pokud je výsledek **false**, vytiskne diagnostickou zprávu a přeruší se, program.

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*Výraz*<br/>
Skalární výraz, který (včetně výrazy ukazatelů), který se vyhodnotí na nenulovou hodnotu (**true**) nebo 0 (**false**).

*message*<br/>
Zpráva, která se má zobrazit

*Název souboru*<br/>
Název zdrojového souboru kontrolního výrazu se nezdařilo.

*Řádek*<br/>
Číslo řádku ve zdrojovém souboru neplatnost kontrolního výrazu.

## <a name="remarks"></a>Poznámky

**Vyhodnocení** – makro se obvykle používá k identifikaci logických chyb během vývoje aplikace. Použít k zastavení vykonávání programu, když dojde k neočekávané podmínky implementací *výraz* argument vyhodnotilo **false** pouze pokud program pracuje správně. Kontrolní výraz kontroly můžete vypnout v době kompilace definováním makro **NDEBUG**. Můžete vypnout **vyhodnocení** – makro beze změny zdrojových souborů s využitím **/DNDEBUG** možnost příkazového řádku. Můžete vypnout **vyhodnocení** makra ve zdrojovém kódu s použitím `#define NDEBUG` direktiv před \<assert.h > je součástí.

**Vyhodnocení** – makro vytiskne diagnostiku zpráv při *výraz* vyhodnotí jako **false** (0) a volání [přerušit](abort.md) k ukončení programu pro spuštění. Pokud nebyla provedena žádná akce *výraz* je **true** (nenulový). Diagnostická zpráva obsahuje selhání výrazu název zdrojový soubor a číslo řádku kde kontrolní výraz je neplatný.

Diagnostické zprávy je vytištěna v širokých znaků. Proto bude fungovat podle očekávání, i když nejsou znaky kódování Unicode ve výrazu.

Cíl diagnostické zprávy závisí na typu aplikace, volá se, rutina. Konzolové aplikace vždy zobrazí zpráva prostřednictvím **stderr**. V aplikaci založené na Windows **vyhodnocení** volá Windows [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) funkce k vytvoření okna zprávy pro zobrazení zprávy spolu s **OK** tlačítko. Když uživatel klepne **OK**, program okamžitě přeruší.

Když je aplikace spojena s ladicí verzí knihovny run-time **vyhodnocení** vytvoří okno se zprávou s tři tlačítka: **přerušit**, **opakujte**a **Ignorovat**. Pokud uživatel klikne **přerušit**, program okamžitě přeruší. Pokud uživatel klikne **opakujte**, se nazývá ladicího programu a uživatele můžete ladit program, pokud je povoleno ladění just-in-time (JIT). Pokud uživatel klikne **Ignorovat**, **vyhodnocení** pokračovat normální spuštění: vytvoření okna se zprávou s **OK** tlačítko. Všimněte si, že kliknete na **Ignorovat** při existenci chybového stavu může vést k nedefinovanému chování.

Další informace o ladění CRT naleznete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

**_Assert** a **_wassert** funkce jsou vnitřní funkce CRT. Pomáhají minimalizovat kód v objektové soubory potřebné k podpoře kontrolní výrazy. Nedoporučujeme přímo volat tyto funkce.

**Vyhodnocení** – makro je povolený v ladění a vydání verze běhových knihoven C při **NDEBUG** není definován. Když **NDEBUG** je definován, makro je k dispozici, ale její argument se nevyhodnocuje a nemá žádný vliv. Pokud je povolena, **vyhodnocení** volání maker **_wassert** pro jeho implementaci. Ostatní makra kontrolní výraz [_ASSERT](assert-asserte-assert-expr-macros.md), [_asserte –](assert-asserte-assert-expr-macros.md) a [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), jsou také k dispozici, ale jenom vyhodnotit výrazy předané k nim, když [_DEBUG](../../c-runtime-library/debug.md) makro bylo definováno a které jsou právě kód spojený s ladicí verze knihoven C run-time.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**Assert –**, **_wassert**|\<assert.h>|

Podpis metody **_assert** funkce není k dispozici v hlavičkovém souboru. Podpis metody **_wassert** funkce je dostupná jenom při **NDEBUG** makro není definované.

## <a name="example"></a>Příklad

V tomto programu **analyze_string** funkce používá **vyhodnocení** – makro testování několik podmínek souvisejících na řetězec a délka. Pokud selže kterákoli z podmínek, program vytiskne zprávu s oznámením, co způsobilo selhání.

```C
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

Po selhání kontrolního výrazu, v závislosti na verzi operačního systému a knihovny run-time mohou se zobrazit okno se zprávou, která obsahuje přibližně takto:

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

Pokud ladicí program je nainstalovali, zvolte **ladění** tlačítko spuštění ladicího programu, nebo **ukončit program** ukončíte.

## <a name="see-also"></a>Viz také:

[Zpracování chyb](../../c-runtime-library/error-handling-crt.md)<br/>
[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
