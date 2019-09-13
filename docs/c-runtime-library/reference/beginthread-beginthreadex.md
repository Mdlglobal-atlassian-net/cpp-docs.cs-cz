---
title: _beginthread, _beginthreadex
ms.date: 02/27/2018
api_name:
- _beginthread
- _beginthreadex
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
ms.openlocfilehash: 8714e945464dd98483f9347c4226321a96cda61c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943635"
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
Počáteční adresa rutiny, která zahájí provádění nového vlákna. Pro **_beginthread**je konvence volání buď [__cdecl](../../cpp/cdecl.md) (pro nativní kód), nebo [__clrcall](../../cpp/clrcall.md) (pro spravovaný kód); pro **_beginthreadex**je buď [__stdcall](../../cpp/stdcall.md) (pro nativní kód) nebo [__clrcall](../../cpp/clrcall.md) (pro spravovaný kód).

*stack_size*<br/>
Velikost zásobníku pro nové vlákno nebo 0.

*arglist*<br/>
Seznam argumentů, které mají být předány novému vláknu, nebo **hodnota null**.

*Zabezpečení*<br/>
Ukazatel na strukturu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , která určuje, zda vrácený popisovač mohou být děděny podřízenými procesy. Pokud je zabezpečení **null**, nelze popisovač dědit. Pro aplikace systému Windows 95 musí být **hodnota null** .

*initflag*<br/>
Příznaky, které řídí počáteční stav nového vlákna. Nastavte *initflag* na hodnotu 0 pro okamžité spuštění, nebo **CREATE_SUSPENDED** pro vytvoření vlákna v pozastaveném stavu. použijte [ResumeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-resumethread) pro spuštění vlákna. Nastavte příznak *initflag* na **STACK_SIZE_PARAM_IS_A_RESERVATION** , aby se použil *STACK_SIZE* jako počáteční rezervní velikost zásobníku v bajtech. Pokud tento příznak není zadán, *stack_size* určuje velikost potvrzení.

*thrdaddr*<br/>
Odkazuje na 32 proměnnou, která přijímá identifikátor vlákna. Pokud je **hodnota null**, není použita.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, každá z těchto funkcí vrátí popisovač nově vytvořenému vláknu; Pokud se ale nově vytvořené vlákno ukončí příliš rychle, **_beginthread** nemusí vracet platný popisovač. (Podívejte se na diskuzi v části poznámky.) V případě chyby **_beginthread** vrací hodnotu-1l a **errno** je nastavená na **EAGAIN** , pokud existuje příliš mnoho vláken, **EINVAL** , pokud je argument neplatný nebo pokud je velikost zásobníku nesprávná, nebo na **EACCES** , pokud není dostatek prostředků ( například paměť). V případě chyby **_beginthreadex** vrátí hodnotu 0 a nastaví **errno** a **_doserrno** .

Pokud má Start_address **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí-1.

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Další informace o **uintptr_t**naleznete v tématu [Standard Types](../../c-runtime-library/standard-types.md).

## <a name="remarks"></a>Poznámky

Funkce **_beginthread** vytvoří vlákno, které zahájí provádění rutiny na *start_address*. Rutina na *start_address* musí používat **__cdecl** (pro nativní kód) nebo **__clrcall** (pro spravovaný kód) konvence volání a nesmí mít žádnou návratovou hodnotu. Když se vlákno z této rutiny vrátí, automaticky se ukončí. Další informace o vláknech naleznete v tématu [Podpora multithreadingu pro starší kód (vizuál C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

**_beginthreadex** připomíná rozhraní Win32 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) API těsněji než **_beginthread** . **_beginthreadex** se liší od **_beginthread** , a to následujícími způsoby:

- **_beginthreadex** má tři další parametry: *initflag*, *Security*a **threadaddr**. Nové vlákno lze vytvořit v pozastaveném stavu se zadaným zabezpečením a lze k němu přistupovat pomocí *thrdaddr*, což je identifikátor vlákna.

- Rutina na *start_address* , která je předána **_beginthreadex** , musí používat konvenci **__stdcall** (pro nativní kód) nebo **__clrcall** (pro spravovaný kód) a musí vracet ukončovací kód vlákna.

- **_beginthreadex** vrací 0 při selhání, nikoli-1l.

- Vlákno, které je vytvořeno pomocí **_beginthreadex** , je ukončeno voláním [_endthreadex](endthread-endthreadex.md).

Funkce **_beginthreadex** poskytuje větší kontrolu nad tím, jak je vlákno vytvořeno, než **_beginthread** . Funkce **_endthreadex** je také pružnější. Například pomocí **_beginthreadex**můžete použít informace o zabezpečení, nastavit počáteční stav vlákna (spuštěno nebo pozastaveno) a získat identifikátor vlákna nově vytvořeného vlákna. Můžete také použít popisovač vlákna, který vrací **_beginthreadex** , s rozhraními API synchronizace, která nelze s **_beginthread**provádět.

Použití **_beginthreadex** než **_beginthread**je bezpečnější. Pokud je vlákno, které generuje **_beginthread** , rychle ukončeno, obslužná rutina, která je vrácena volajícímu **_beginthread** , může být neplatná nebo ukazovat na jiné vlákno. Nicméně popisovač vrácený funkcí **_beginthreadex** musí být uzavřen volajícím **_beginthreadex**, takže je zaručeno, že musí být platným popisovačem, pokud **_beginthreadex** nevrátil chybu.

Můžete volat [_endthread](endthread-endthreadex.md) nebo **_endthreadex** explicitně pro ukončení vlákna; **_endthread** nebo **_endthreadex** se však zavolá automaticky při návratu vlákna z rutiny, která je předána jako parametr. Ukončení vlákna s voláním **_endthread** nebo **_endthreadex** pomáhá zajistit správné obnovení prostředků, které jsou přiděleny pro vlákno.

**_endthread** automaticky zavře popisovač vlákna, zatímco **_endthreadex** ne. Proto při použití **_beginthread** a **_endthread**explicitně uzavřete popisovač vlákna voláním rozhraní Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API. Toto chování se liší od rozhraní Win32 [ExitThread –](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API.

> [!NOTE]
> Pro spustitelný soubor propojený s Libcmt. lib Nevolejte rozhraní Win32 **ExitThread –** API, aby nedocházelo k tomu, aby systém za běhu vyvolal nároky přidělené prostředky. **_endthread** a **_endthreadex** uvolní prostředky přiděleného vlákna a pak zavolají **ExitThread –** .

Operační systém zpracovává přidělení zásobníku, pokud je volán buď **_beginthread** nebo **_beginthreadex** ; není nutné předávat adresu zásobníku vláken do některé z těchto funkcí. Kromě toho může být argument *stack_size* 0, v takovém případě operační systém používá stejnou hodnotu jako zásobník, který je určen pro hlavní vlákno.

*Arglist* je parametr, který se má předat nově vytvořenému vláknu. Obvykle je to adresa datové položky, jako je například řetězec znaků. *Arglist* může mít **hodnotu null** , pokud není potřeba, ale **_beginthread** a **_beginthreadex** musí předat nějaké hodnotě, která má být předána novému vláknu. Všechna vlákna jsou ukončena, pokud jakékoli vlákno volá funkci [Abort](abort.md), **Exit**, **_exit**nebo **ExitProcess –** .

Národní prostředí nového vlákna je inicializováno pomocí informací o globálním aktuálním národním prostředí pro proces. Pokud je národní prostředí pro vlákno povoleno voláním [_configthreadlocale](configthreadlocale.md) (buď globálně, nebo pouze pro nové vlákna), vlákno může změnit své národní prostředí nezávisle na jiných vláknech voláním **setlocale** nebo **_wsetlocale**. Vlákna, která nemají nastaven příznak národního prostředí pro vlákno, mohou ovlivnit informace o národním prostředí ve všech ostatních vláknech, které nemají nastaven příznak národního prostředí pro vlákno a také všechna nově vytvořená vlákna. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pro kód **/CLR** , **_beginthread** a **_beginthreadex** mají dvě přetížení. Jedna má ukazatel na funkci nativní konvence volání a druhý přebírá ukazatel na funkci **__clrcall** . První přetížení není bezpečné pro doménu aplikace a nikdy nebude. Pokud píšete kód **/CLR** , musíte zajistit, aby nové vlákno zadalo správnou doménu aplikace před tím, než přistupuje ke spravovaným prostředkům. To lze provést například pomocí [funkce call_in_appdomain](../../dotnet/call-in-appdomain-function.md). Druhé přetížení je aplikace zabezpečená pro doménu; nově vytvořené vlákno bude vždy ukončeno v doméně aplikace volajícího **_beginthread** nebo **_beginthreadex**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_beginthread**|\<Process. h >|
|**_beginthreadex**|\<Process. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Pouze vícevláknové verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

Chcete-li použít **_beginthread** nebo **_beginthreadex**, musí aplikace propojit jednu z vícevláknových knihoven run-time jazyka C.

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

Stisknutím libovolné klávesy ukončete ukázkovou aplikaci.

## <a name="example"></a>Příklad

Následující vzorový kód ukazuje, jak lze použít popisovač vlákna, který je vrácen pomocí **_beginthreadex** s rozhraním API pro synchronizaci [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject). Hlavní vlákno čeká na ukončení druhého vlákna, než pokračuje. Když druhé vlákno volá **_endthreadex**, způsobí, že objekt vlákna přejde do stavu signalizace. To umožňuje, aby primární vlákno pokračovalo v běhu. Tento postup nelze provést s **_beginthread** a **_endthread**, protože **_endthread** volá **CloseHandle**, což zničí objekt vlákna předtím, než může být nastaven na signálový stav.

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
- [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)
