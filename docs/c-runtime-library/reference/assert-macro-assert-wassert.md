---
title: assert Macro, _assert, _wassert
ms.date: 11/04/2016
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
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
ms.openlocfilehash: a2cc780fbc93aa66bd7fd613c3e155cda27eb7f9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500340"
---
# <a name="assert-macro-_assert-_wassert"></a>assert Macro, _assert, _wassert

Vyhodnotí výraz a, pokud je výsledek **false**, vytiskne diagnostickou zprávu a program přeruší.

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

*vyjádření*<br/>
Skalární výraz (včetně výrazů ukazatelů), který vyhodnocuje nenulovou hodnotu (**true**) nebo 0 (**false**).

*message*<br/>
Zpráva, která se má zobrazit

*Bitmap*<br/>
Název zdrojového souboru, ve kterém se kontrolní výraz nezdařil.

*Link*<br/>
Číslo řádku ve zdrojovém souboru kontrolního výrazu, který selhal.

## <a name="remarks"></a>Poznámky

Makro **Assert** se obvykle používá k identifikaci logických chyb během vývoje programu. Použijte ji k zastavení provádění programu, pokud dojde k neočekávaným podmínkám implementací argumentu *výrazu* pro vyhodnocení na **hodnotu false** pouze v případě, že program pracuje nesprávně. Kontroly kontrolního výrazu mohou být v době kompilace vypnuty definováním makra **NDEBUG**. Makro **kontrolního výrazu** můžete vypnout bez změny zdrojových souborů pomocí možnosti příkazového řádku **/DNDEBUG** . Makro **Assert** ve zdrojovém kódu můžete vypnout pomocí `#define NDEBUG` direktivy před \<Assert. h > je zahrnuto.

Makro **Assert** vytiskne diagnostickou zprávu, když se *výraz* vyhodnotí jako **false** (0), a volání přeruší k ukončení provádění programu. [](abort.md) Pokud je *výraz* **true** (nenulový), není provedena žádná akce. Diagnostická zpráva obsahuje výraz, který selhal, název zdrojového souboru a číslo řádku, kde se kontrolní výraz nezdařil.

Diagnostická zpráva se tiskne v rámci velkých znaků. Proto bude fungovat podle očekávání i v případě, že ve výrazu jsou znaky Unicode.

Cíl diagnostické zprávy závisí na typu aplikace, která rutinu volala. Konzolové aplikace vždy obdrží zprávu přes **stderr**. V aplikaci pro Windows vyhodnotí volání funkce [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) systému Windows k vytvoření okna se zprávou pro zobrazení zprávy s tlačítkem **OK** . Když uživatel klikne na **tlačítko OK**, program se okamžitě přeruší.

Pokud je aplikace propojena s ladicí verzí knihoven za běhu, **vyhodnocení** vytvoří okno se zprávou se třemi tlačítky: **Přerušit**, **Opakovat**a **Ignorovat**. Pokud uživatel kliknena možnost přerušit, program se okamžitě zruší. Pokud uživatel klikne na tlačítko **Opakovat**, bude volán ladicí program a uživatel může ladit program, pokud je povoleno ladění JIT (just-in-time). Pokud uživatel klikne na možnost **Ignorovat**, **kontrolní** výraz pokračuje s jeho normálním spuštěním: vytvoření okna se zprávou pomocí tlačítka **OK** . Všimněte si, že kliknutí na **Ignorovat** , pokud existuje chybový stav, může mít za následek nedefinované chování.

Další informace o ladění CRT naleznete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

Funkce **_ASSERT** a **_wassert** jsou interní funkce CRT. Pomůžou minimalizovat kód vyžadovaný v souborech objektů pro podporu kontrolních výrazů. Nedoporučujeme tyto funkce volat přímo.

Makro **Assert** je povoleno v verzích verze i ladění běhových knihoven jazyka C, pokud není definován **NDEBUG** . Je-li definována **NDEBUG** , je makro k dispozici, ale nevyhodnocuje jeho argument a nemá žádný vliv. Pokud je povoleno, makro **kontrolního výrazu** zavolá **_wassert** pro jeho implementaci. K dispozici jsou také další makra kontrolního výrazu, [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md) a [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), ale vyhodnocují pouze ty výrazy, které jsou předány, když je definováno makro [_DEBUG](../../c-runtime-library/debug.md) a když jsou v kódu propojeném s laděním. verze knihoven run-time jazyka C.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**assert**, **_wassert**|\<assert.h>|

Podpis funkce **_ASSERT** není v hlavičkovém souboru k dispozici. Signatura funkce **_wassert** je k dispozici pouze v případě, že není definováno makro **NDEBUG** .

## <a name="example"></a>Příklad

V tomto programu používá funkce **analyze_string** makro **Assert** k testování několika podmínek souvisejících s řetězcem a délkou. Pokud některá z podmínek selže, program vytiskne zprávu s informacemi o tom, co způsobilo chybu.

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

Program vygeneruje tento výstup:

```Output
Analyzing string 'abc'
Analyzing string '(null)'
Assertion failed: string != NULL, file crt_assert.c, line 25
```

Po selhání kontrolního výrazu v závislosti na verzi operačního systému a běhové knihovny se může zobrazit okno se zprávou, které obsahuje něco podobného jako následující:

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

Pokud je nainstalován ladicí program, klikněte na tlačítko **ladit** a spusťte ladicí program nebo **Ukončete program** , který chcete ukončit.

## <a name="see-also"></a>Viz také:

[Zpracování chyb](../../c-runtime-library/error-handling-crt.md)<br/>
[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
