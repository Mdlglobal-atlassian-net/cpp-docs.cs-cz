---
title: _beginthread, _beginthreadex
ms.date: 4/2/2020
api_name:
- _beginthread
- _beginthreadex
- _o__beginthread
- _o__beginthreadex
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- beginthread
- _beginthread
- beginthreadex
- _beginthreadex
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
ms.openlocfilehash: 2d2851a7e76a43501145b1e55e8028b72c2a8afb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348679"
---
# <a name="_beginthread-_beginthreadex"></a>_beginthread, _beginthreadex

Vytvoří vlákno.

## <a name="syntax"></a>Syntaxe

```cpp
uintptr_t _beginthread( // NATIVE CODE
   void( __cdecl *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthread( // MANAGED CODE
   void( __clrcall *start_address )( void * ),
   unsigned stack_size,
   void *arglist
);
uintptr_t _beginthreadex( // NATIVE CODE
   void *security,
   unsigned stack_size,
   unsigned ( __stdcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
uintptr_t _beginthreadex( // MANAGED CODE
   void *security,
   unsigned stack_size,
   unsigned ( __clrcall *start_address )( void * ),
   void *arglist,
   unsigned initflag,
   unsigned *thrdaddr
);
```

### <a name="parameters"></a>Parametry

*start_address*<br/>
Spusťte adresu rutiny, která začíná provádění nového vlákna. Pro **_beginthread**je konvence volání [buď __cdecl](../../cpp/cdecl.md) (pro nativní kód) nebo [__clrcall](../../cpp/clrcall.md) (pro spravovaný kód); pro **_beginthreadex**je [buď __stdcall](../../cpp/stdcall.md) (pro nativní kód) nebo [__clrcall](../../cpp/clrcall.md) (pro spravovaný kód).

*stack_size*<br/>
Velikost zásobníku pro nové vlákno nebo 0.

*arglist*<br/>
Seznam argumentů, který má být předán novému vláknu nebo **null**.

*Zabezpečení*<br/>
Ukazatel na [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) struktury, která určuje, zda vrácený popisovač může být zděděn podřízenými procesy. Pokud *zabezpečení* je **NULL**, popisovač nelze zdědit. Musí být **null** pro aplikace systému Windows 95.

*initflag*<br/>
Příznaky, které řídí počáteční stav nového vlákna. Nastavte *initflag* na 0 spustit okamžitě nebo **CREATE_SUSPENDED** k vytvoření podprocesu v pozastaveném stavu; použijte [ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread) ke spuštění vlákna. Nastavte *initflag* **na STACK_SIZE_PARAM_IS_A_RESERVATION** příznak použít *stack_size* jako počáteční rezervní velikost zásobníku v bajtů; Pokud tento příznak není zadán, *stack_size* určuje velikost potvrzení.

*thrdaddr řekl:*<br/>
Odkazuje na 32bitovou proměnnou, která obdrží identifikátor vlákna. Pokud je **null**, není použit.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, každá z těchto funkcí vrátí popisovač nově vytvořenému vláknu; pokud však nově vytvořené vlákno ukončí příliš rychle, **_beginthread** nemusí vrátit platný popisovač. (Viz diskuse v sekci Poznámky.) Při chybě **vrátí _beginthread** -1L a **errno** je nastavena na **EAGAIN,** pokud existuje příliš mnoho podprocesů, na **EINVAL,** pokud je argument neplatný nebo velikost zásobníku je nesprávná, nebo **EACCES,** pokud jsou nedostatečné prostředky (například paměť). Při chybě **vrátí _beginthreadex** 0 a jsou **nastaveny chyby** a **_doserrno.**

Pokud *je start_address* **null**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce nastavit **errno** **eINVAL** a vrátit -1.

Další informace o těchto a dalších návratových kódech naleznete [v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Další informace o uintptr_t naleznete **v** [tématu Standardní typy](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Poznámky

Funkce **_beginthread** vytvoří vlákno, které zahájí provádění rutiny v *start_address*. Rutina na *start_address* musí používat **__cdecl** (pro nativní kód) nebo **__clrcall** (pro spravovaný kód) konvence volání a by neměla mít žádnou vrácenou hodnotu. Když se vlákno vrátí z této rutiny, je automaticky ukončeno. Další informace o vláknech naleznete v [tématu Podpora více vláken pro starší kód (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** se podobá Rozhraní API [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) Win32 více než **_beginthread.** **_beginthreadex** se liší od **_beginthread** následujícími způsoby:

- **_beginthreadex** má tři další parametry: *initflag*, *Security*a **threadaddr**. Nové vlákno lze vytvořit v pozastaveném stavu se zadaným zabezpečením a lze k němu přistupovat pomocí *thrdaddr*, což je identifikátor vlákna.

- Rutina na *start_address,* která je předána **_beginthreadex** musí používat **__stdcall** (pro nativní kód) nebo **__clrcall** (pro spravovaný kód) konvence volání a musí vrátit ukončovací kód vlákna.

- **_beginthreadex** vrátí 0 na selhání, spíše než -1L.

- Podproces vytvořený pomocí **_beginthreadex** je ukončen voláním [_endthreadex](endthread-endthreadex.md).

Funkce **_beginthreadex** poskytuje větší kontrolu nad tím, jak je vlákno vytvořeno, než **_beginthread.** Funkce **_endthreadex** je také flexibilnější. Například s **_beginthreadex**můžete použít informace o zabezpečení, nastavit počáteční stav vlákna (spuštěné nebo pozastavené) a získat identifikátor vlákna nově vytvořeného vlákna. Můžete také použít popisovač vlákna, který je vrácen **_beginthreadex** se synchronizačními rozhraními API, což nelze provést s **_beginthread**.

Je bezpečnější používat **_beginthreadex** než **_beginthread**. Pokud vlákno, které je generováno **_beginthread** rychle ukončí, popisovač, který je vrácen volajícímu **_beginthread** může být neplatný nebo přejděte na jiné vlákno. Popisovač, který je vrácen **a _beginthreadex** musí být uzavřen volající m **_beginthreadexj** **_beginthreadex.**

Můžete volat [_endthread](endthread-endthreadex.md) nebo **_endthreadex** explicitně ukončit vlákno; _endthread **nebo** **_endthreadex** je však volána automaticky, když se vlákno vrátí z rutiny, která je předána jako parametr. Ukončení vlákna s voláním **_endthread** nebo **_endthreadex** pomáhá zajistit správné obnovení prostředků, které jsou přiděleny pro vlákno.

**_endthread** automaticky zavře úchyt závitu, zatímco **_endthreadex** nikoli. Proto při použití **_beginthread** a **_endthread**, není explicitně zavřete popisovač vlákna voláním rozhraní API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) Win32. Toto chování se liší od rozhraní API [Win32 ExitThread.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread)

> [!NOTE]
> Pro spustitelný soubor propojený s Libcmt.lib nevolejte rozhraní API **Win32 ExitThread,** abyste nezabránili systému run-time v rekultivaci přidělených prostředků. **_endthread** a **_endthreadex** znovu získat přidělené prostředky vlákna a potom volat **ExitThread**.

Operační systém zpracovává přidělení zásobníku při **volání _beginthread** nebo **_beginthreadex;** není třeba předat adresu zásobníku podprocesů do jedné z těchto funkcí. Kromě toho *stack_size* argument může být 0, v takovém případě operační systém používá stejnou hodnotu jako zásobník, který je určen pro hlavní vlákno.

*arglist* je parametr, který má být předán nově vytvořenému vláknu. Obvykle se jedná o adresu datové položky, například řetězec znaků. *arglist* může být **NULL,** pokud není potřeba, ale **_beginthread** a **_beginthreadex** musí být uvedeny některé hodnoty předat nové vlákno. Všechna vlákna jsou ukončena, pokud všechna volání [podprocesu přerušit](abort.md), **exit**, **_exit**nebo **ExitProcess**.

Národní prostředí nového vlákna je inicializováno pomocí informací o globálním národním národním prostředí pro jednotlivý proces. Pokud národní prostředí pro vlastní vlákno je povoleno voláním [_configthreadlocale](configthreadlocale.md) (globálně nebo pouze pro nová vlákna), podproces může změnit své národní prostředí nezávisle na jiných vláknech voláním **setlocale** nebo **_wsetlocale**. Vlákna, která nemají sadu příznaku národního prostředí pro vlákno, mohou ovlivnit informace o národním prostředí ve všech ostatních vláknech, která také nemají nastavenpříznak národního prostředí pro vlákno, stejně jako všechna nově vytvořená vlákna. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Pro **/clr** **kód, _beginthread** a **_beginthreadex** každý mají dvě přetížení. Jeden má nativní ukazatel funkce konvence volání a druhý má **ukazatel funkce __clrcall.** První přetížení není bezpečné pro doménu aplikace a nikdy nebude. Pokud píšete **/clr** kód, musíte zajistit, že nové vlákno zadá správnou doménu aplikace před tím, než přistupuje ke spravovaným prostředkům. Můžete to provést například pomocí [funkce call_in_appdomain](../../dotnet/call-in-appdomain-function.md). Druhé přetížení je bezpečné pro doménu aplikace; nově vytvořené vlákno vždy skončí v aplikační doméně volajícího **_beginthread** nebo **_beginthreadex**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Verze s více vlákny pouze [knihoven c run-time.](../../c-runtime-library/crt-library-features.md)

Chcete-li použít **_beginthread** nebo **_beginthreadex**, musí být aplikace propojena s jednou z vícevláknových knihoven run-time c.

## <a name="example"></a>Příklad

Následující příklad používá **_beginthread** a **_endthread**.

```C
// crt_BEGTHRD.C
// compile with: /MT /D "_X86_" /c
// processor: x86
#include <windows.h>
#include <process.h>    /* _beginthread, _endthread */
#include <stddef.h>
#include <stdlib.h>
#include <conio.h>

void Bounce( void * );
void CheckKey( void * );

// GetRandom returns a random integer between min and max.
#define GetRandom( min, max ) ((rand() % (int)(((max) + 1) - (min))) + (min))
// GetGlyph returns a printable ASCII character value
#define GetGlyph( val ) ((char)((val + 32) % 93 + 33))

BOOL repeat = TRUE;                 // Global repeat flag
HANDLE hStdOut;                     // Handle for console window
CONSOLE_SCREEN_BUFFER_INFO csbi;    // Console information structure

int main()
{
    int param = 0;
    int * pparam = &param;

    // Get display screen's text row and column information.
    hStdOut = GetStdHandle( STD_OUTPUT_HANDLE );
    GetConsoleScreenBufferInfo( hStdOut, &csbi );

    // Launch CheckKey thread to check for terminating keystroke.
    _beginthread( CheckKey, 0, NULL );

    // Loop until CheckKey terminates program or 1000 threads created.
    while( repeat && param < 1000 )
    {
        // launch another character thread.
        _beginthread( Bounce, 0, (void *) pparam );

        // increment the thread parameter
        param++;

        // Wait one second between loops.
        Sleep( 1000L );
    }
}

// CheckKey - Thread to wait for a keystroke, then clear repeat flag.
void CheckKey( void * ignored )
{
    _getch();
    repeat = 0;    // _endthread implied
}

// Bounce - Thread to create and control a colored letter that moves
// around on the screen.
//
// Params: parg - the value to create the character from
void Bounce( void * parg )
{
    char       blankcell = 0x20;
    CHAR_INFO  ci;
    COORD      oldcoord, cellsize, origin;
    DWORD      result;
    SMALL_RECT region;

    cellsize.X = cellsize.Y = 1;
    origin.X = origin.Y = 0;

    // Generate location, letter and color attribute from thread argument.
    srand( _threadid );
    oldcoord.X = region.Left = region.Right =
        GetRandom(csbi.srWindow.Left, csbi.srWindow.Right - 1);
    oldcoord.Y = region.Top = region.Bottom =
        GetRandom(csbi.srWindow.Top, csbi.srWindow.Bottom - 1);
    ci.Char.AsciiChar = GetGlyph(*((int *)parg));
    ci.Attributes = GetRandom(1, 15);

    while (repeat)
    {
        // Pause between loops.
        Sleep( 100L );

        // Blank out our old position on the screen, and draw new letter.
        WriteConsoleOutputCharacterA(hStdOut, &blankcell, 1, oldcoord, &result);
        WriteConsoleOutputA(hStdOut, &ci, cellsize, origin, &region);

        // Increment the coordinate for next placement of the block.
        oldcoord.X = region.Left;
        oldcoord.Y = region.Top;
        region.Left = region.Right += GetRandom(-1, 1);
        region.Top = region.Bottom += GetRandom(-1, 1);

        // Correct placement (and beep) if about to go off the screen.
        if (region.Left < csbi.srWindow.Left)
            region.Left = region.Right = csbi.srWindow.Left + 1;
        else if (region.Right >= csbi.srWindow.Right)
            region.Left = region.Right = csbi.srWindow.Right - 2;
        else if (region.Top < csbi.srWindow.Top)
            region.Top = region.Bottom = csbi.srWindow.Top + 1;
        else if (region.Bottom >= csbi.srWindow.Bottom)
            region.Top = region.Bottom = csbi.srWindow.Bottom - 2;

        // If not at a screen border, continue, otherwise beep.
        else
            continue;
        Beep((ci.Char.AsciiChar - 'A') * 100, 175);
    }
    // _endthread given to terminate
    _endthread();
}
```

Stisknutím libovolné klávesy ukončite ukázkovou aplikaci.

## <a name="example"></a>Příklad

Následující ukázkový kód ukazuje, jak můžete použít popisovač vlákna, který je vrácen **_beginthreadex** s synchronizačním rozhraním API [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject). Hlavní vlákno čeká na ukončení druhého vlákna, než bude pokračovat. Když druhý podproces volá **_endthreadex**, způsobí, že jeho objekt podprocesu přejít do signalizovaného stavu. To umožňuje primární vlákno pokračovat v běhu. To nelze provést pomocí **_beginthread** a **_endthread**, protože **_endthread** volá **CloseHandle**, který zničí objekt vlákna před jej lze nastavit do signalizovaného stavu.

```cpp
// crt_begthrdex.cpp
// compile with: /MT
#include <windows.h>
#include <stdio.h>
#include <process.h>

unsigned Counter;
unsigned __stdcall SecondThreadFunc( void* pArguments )
{
    printf( "In second thread...\n" );

    while ( Counter < 1000000 )
        Counter++;

    _endthreadex( 0 );
    return 0;
}

int main()
{
    HANDLE hThread;
    unsigned threadID;

    printf( "Creating second thread...\n" );

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc, NULL, 0, &threadID );

    // Wait until second thread terminates. If you comment out the line
    // below, Counter will not be correct because the thread has not
    // terminated, and Counter most likely has not been incremented to
    // 1000000 yet.
    WaitForSingleObject( hThread, INFINITE );
    printf( "Counter should be 1000000; it is-> %d\n", Counter );
    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
Creating second thread...
In second thread...
Counter should be 1000000; it is-> 1000000
```

## <a name="see-also"></a>Viz také

- [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)
- [_endthread, _endthreadex](endthread-endthreadex.md)
- [Přerušení](abort.md)
- [exit, _Exit, _exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
