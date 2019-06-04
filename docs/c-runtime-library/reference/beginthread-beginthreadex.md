---
title: _beginthread, _beginthreadex
ms.date: 02/27/2018
apiname:
- _beginthread
- _beginthreadex
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
ms.openlocfilehash: f64fd7b945fc8ea2e5c111d300266e07faade0e7
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504543"
---
# <a name="beginthread-beginthreadex"></a>_beginthread, _beginthreadex

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
Počáteční adresa rutiny, která začíná spuštění nového vlákna. Pro **_beginthread**, je konvence volání buď [__cdecl](../../cpp/cdecl.md) (pro nativní kód) nebo [__clrcall](../../cpp/clrcall.md) (pro spravovaný kód); pro **_beginthreadex**, je buď [__stdcall](../../cpp/stdcall.md) (pro nativní kód) nebo [__clrcall](../../cpp/clrcall.md) (pro spravovaný kód).

*stack_size*<br/>
Velikost zásobníku pro nové vlákno, nebo 0.

*arglist*<br/>
Seznam argumentů, které se mají předat nové vlákno, nebo **NULL**.

*Zabezpečení*<br/>
Ukazatel [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) struktura, která určuje, zda lze Vrácený popisovač Zdědit podřízenými procesy. Pokud *zabezpečení* je **NULL**, popisovač nelze dědit. Musí být **NULL** pro aplikace Windows 95.

*initflag*<br/>
Příznaky, které řídí počáteční stav nového vlákna. Nastavte *initflag* 0 spustit okamžitě, nebo k **CREATE_SUSPENDED** k vytvoření vlákna v pozastaveném stavu; použijte [ResumeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-resumethread) ke spuštění vlákna. Nastavte *initflag* k **STACK_SIZE_PARAM_IS_A_RESERVATION** příznak pro použití *stack_size* jako počáteční rezervovat velikost zásobníku v bajtech; Pokud je tento příznak není zadán, *stack_size* Určuje velikost potvrzení změn.

*thrdaddr*<br/>
Odkazuje na 32bitové proměnné, který přijímají identifikátor vlákna. Pokud je **NULL**, se nepoužívá.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, každá z těchto funkcí vrací popisovač do nově vytvořeného vlákna; Nicméně, pokud nově vytvořený podproces skončí příliš rychle **_beginthread** nemusí vrátit platný popisovač. (Viz diskuze v části poznámky.) V případě chyby **_beginthread** vrátí hodnotu-1 L a **errno** je nastavena na **EAGAIN** pokud existuje příliš mnoho vláken na **EINVAL** Pokud je argumentem Neplatný nebo velikost zásobníku je správné, nebo **EACCES** Pokud není dostatek prostředků (např. paměti). V případě chyby **_beginthreadex** vrátí hodnotu 0, a **errno** a **_doserrno** jsou nastavené.

Pokud *start_address* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátí hodnotu -1.

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Další informace o **uintptr_t –** , naleznete v tématu [standardní typy](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Poznámky

**_Beginthread** funkce vytvoří vlákno, které spustí rutinu na *start_address*. Rutina v *start_address* musí použít **__cdecl** (pro nativní kód) nebo **__clrcall** (pro spravovaný kód) konvence volání a musí mít žádnou návratovou hodnotu. Pokud se podproces vrací z této rutiny, bude automaticky ukončen. Další informace o vláknech naleznete v tématu [podpora multithreadingu ve starším kódu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** vypadá podobně jako Win32 [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) další rozhraní API než **_beginthread** nepodporuje. **_beginthreadex** se liší od **_beginthread** následujícími způsoby:

- **_beginthreadex** má tři další parametry: *initflag*, *zabezpečení*, a **threadaddr**. Nové vlákno lze vytvořit v pozastaveném stavu se zadaným zabezpečením a je přístupný pomocí *thrdaddr*, což není identifikátor vlákna.

- Rutina v *start_address* , který je předán **_beginthreadex** musí použít **__stdcall** (pro nativní kód) nebo **__clrcall** (pro spravovaný kód) konvence volání a musí vrátit ukončovací kód vlákna.

- **_beginthreadex** vrátí při selhání, spíše než-1 L hodnotu 0.

- Podproces, který je vytvořen pomocí **_beginthreadex** je ukončen voláním [_endthreadex](endthread-endthreadex.md).

**_Beginthreadex** funkce vám dává větší kontrolu nad způsob vytvoření vlákna než **_beginthread** nepodporuje. **_Endthreadex** funkce je také flexibilnější. Třeba index Mei **_beginthreadex**, můžete použít informace o zabezpečení, nastavit počáteční stav podprocesu (spuštěno nebo pozastaveno) a získat identifikátor nově vytvořeného vlákna. Můžete také použít popisovač podprocesu, který je vrácen **_beginthreadex** se synchronizací rozhraní API, které nelze použít s **_beginthread**.

Je bezpečnější používat **_beginthreadex** než **_beginthread**. Pokud podproces, který je generován **_beginthread** rychle ukončí zpracování, který je vrácen volajícímu **_beginthread** může být neplatný nebo ukazuje na jiný podproces. Nicméně popisovač, který je vrácen **_beginthreadex** musí být uzavřen volajícím funkce **_beginthreadex**, takže je zaručeno, že pokud se platný popisovač **_beginthreadex** nevrátila chybu.

Můžete volat [_endthread](endthread-endthreadex.md) nebo **_endthreadex** explicitně k ukončení podprocesu; nicméně **_endthread** nebo **_endthreadex** nazývá automaticky při podproces vrací z rutiny, která je předána jako parametr. Ukončení vlákna s voláním **_endthread** nebo **_endthreadex** pomáhá zajistit správné obnovení prostředků, které jsou k vláknu přiděleny.

**_endthread** automaticky uzavře popisovač vlákna, zatímco **_endthreadex** tak není. Proto při použití **_beginthread** a **_endthread**, explicitně nezavře popisovač vlákna voláním rozhraní Win32 [CloseHandle](/windows/desktop/api/handleapi/nf-handleapi-closehandle) rozhraní API. Toto chování se liší od rozhraní Win32 [ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread) rozhraní API.

> [!NOTE]
> Pro spustitelný soubor propojeného s Libcmt.lib Nevolejte rozhraní Win32 **ExitThread** rozhraní API, abyste nezabránili systému za běhu z recyklovat přidělené prostředky. **_endthread** a **_endthreadex** uvolní prostředky přidělené vláknu a následně zavolat **ExitThread**.

Operační systém zpracovává přidělení zásobníku při buď **_beginthread** nebo **_beginthreadex** nazývá; nemáte předat adresu zásobníku podprocesu některou z těchto funkcí. Kromě toho *stack_size* argument může být 0, ve kterém případ operační systém používá stejnou hodnotu jako zásobník, který je určen pro hlavní vlákno.

*seznam_argumentů* je parametr má být předán do nově vytvořeného vlákna. Obvykle je to adresa datové položky, jako je řetězec znaků. *seznam_argumentů* může být **NULL** Pokud není potřeba, ale **_beginthread** a **_beginthreadex** musí mít nějakou hodnotu pro předání do nového vlákna. Všechna vlákna jsou ukončena, pokud kterékoli vlákno použije [přerušit](abort.md), **ukončit**, **_exit**, nebo **exitprocess –** .

Národní prostředí nového vlákna je inicializována pomocí na úrovni jednotlivého procesu globální aktuální o národním prostředí. Pokud je povoleno národní prostředí pro vlákno voláním [_configthreadlocale](configthreadlocale.md) (buď globálně, nebo pro nová vlákna), vlákno lze změnit pouze své národní prostředí nezávisle z jiných vláken voláním **setlocale** nebo **_wsetlocale**. Vlákna, které nemají nastaven příznak národní prostředí vlákno může ovlivnit o národním prostředí v všechna vlákna, které nemají taky nastavit příznak národní prostředí vlákno, jakož i všech nově vytvořeného vlákna. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pro **/CLR** kódu, **_beginthread** a **_beginthreadex** mají dvě přetížení. Jeden má ukazatel na funkci nativní konvence volání a druhý bere **__clrcall** ukazatel na funkci. První přetížení není bezpečné z hlediska domény aplikace a nikdy ani nebude možné. Pokud píšete **/CLR** kód musíte zajistit, že nové vlákno zadá správnou doménu aplikace před přístupem ke spravované prostředky. To můžete provést například pomocí [call_in_appdomain – funkce](../../dotnet/call-in-appdomain-function.md). Druhé přetížení je aplikace bezpečné domény; nově vytvořené vlákno vždy skončí v doméně aplikace volajícího **_beginthread** nebo **_beginthreadex**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_beginthread**|\<process.h>|
|**_beginthreadex**|\<process.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Verze s více vlákny [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

Chcete-li použít **_beginthread** nebo **_beginthreadex**, aplikaci je třeba propojit s jednou z vícevláknových běhových knihoven C.

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

Stisknutím libovolné klávesy ukončete vzorovou aplikaci.

## <a name="example"></a>Příklad

Následující ukázkový kód ukazuje, jak můžete použít popisovač podprocesu, který je vrácen **_beginthreadex** spolu se synchronizací API [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject). Hlavní podproces čeká na ukončení před pokračováním druhého podprocesu. Když volá druhé vlákno **_endthreadex**, způsobí, že jeho objekt vlákna přejde do signalizovaného stavu. To umožňuje primárnímu vláknu pokračovat v běhu. Tuto akci nelze provést s **_beginthread** a **_endthread**, protože **_endthread** volání **CloseHandle**, které ničí vlákna objekt před jeho můžete nastaven do signalizovaného stavu.

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

## <a name="see-also"></a>Viz také:

- [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)
- [_endthread, _endthreadex](endthread-endthreadex.md)
- [abort](abort.md)
- [exit, _Exit, _exit](exit-exit-exit.md)
- [GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
