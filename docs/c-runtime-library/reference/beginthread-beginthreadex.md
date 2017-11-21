---
title: "_beginthread –, _beginthreadex | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- _beginthread function
- threading [C++], creating threads
- beginthreadex function
- _beginthreadex function
- beginthread function
ms.assetid: 0df64740-a978-4358-a88f-fb0702720091
caps.latest.revision: "36"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 88da6a8a34670da588c0fef25b3060c79b3145f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="beginthread-beginthreadex"></a>_beginthread, _beginthreadex
Vytvoří vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `start_address`  
 Počáteční adresa rutiny, která zahájí provádění nové vlákno. Pro `_beginthread`, konvence volání je buď [__cdecl](../../cpp/cdecl.md) (pro nativní kód) nebo [__clrcall](../../cpp/clrcall.md) (pro spravovaný kód); pro `_beginthreadex`, je buď [__stdcall](../../cpp/stdcall.md)(pro nativní kód) nebo [__clrcall](../../cpp/clrcall.md) (pro spravovaný kód).  
  
 `stack_size`  
 Velikost zásobníku pro nové vlákno, nebo 0.  
  
 `arglist`  
 Seznam argumentů mají být předány nové vlákno, nebo hodnota NULL.  
  
 `Security`  
 Ukazatel na [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje, zda může být vrácená popisovač zděděn podřízené procesy. Pokud `Security` má hodnotu NULL, nemůže být zděděna popisovač. Musí být NULL pro systém Windows 95 aplikace.  
  
 `initflag`  
 Příznaky, které řídí počáteční stav nové vlákno. Nastavit `initflag` k `0` spustit okamžitě, nebo `CREATE_SUSPENDED` vytvořit vlákno v pozastaveném stavu; použít [ResumeThread](http://msdn.microsoft.com/library/windows/desktop/ms685086.aspx) provést vlákno. Nastavit `initflag` k `STACK_SIZE_PARAM_IS_A_RESERVATION` příznak pro použití `stack_size` jako počáteční rezervy velikost zásobníku v bajtů; Pokud tento příznak není zadán, `stack_size` Určuje velikost potvrzení.  
  
 `thrdaddr`  
 Odkazuje na 32-bit proměnné, která přijímá identifikátor přístup z více vláken. Pokud je hodnota NULL, se nepoužije.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud bylo úspěšné, každá z těchto funkcí vrátí popisovač nově vytvořený vlákno; ale pokud nově vytvořený vlákno ukončí příliš rychle `_beginthread` nemusí vracet platný popisovač. (Viz popis v oddílu Poznámky.) Při chybě `_beginthread` vrátí hodnotu-1 L a `errno` je nastaven na `EAGAIN` Pokud jsou moc velký počet vláken, na `EINVAL` Pokud argument je neplatný nebo velikost zásobníku je nesprávný, nebo k `EACCES` Pokud není dostatek prostředků (např. paměti) . Při chybě `_beginthreadex` vrátí hodnotu 0, a `errno` a `_doserrno` jsou nastavené.  
  
 Pokud `startaddress` má hodnotu NULL, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí hodnotu -1.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Další informace o `uintptr_t`, najdete v části [standardní typy](../../c-runtime-library/standard-types.md).  
  
## <a name="remarks"></a>Poznámky  
 `_beginthread` Funkce vytvoří vlákno, které zahájí provádění rutiny v `start_address`. Rutiny v `start_address` musí používat `__cdecl` (pro nativní kód) nebo `__clrcall` (pro spravovaný kód) konvence volání a měl by obsahovat žádnou návratovou hodnotu. Po návratu vlákno z této rutiny je ukončen automaticky. Další informace o vláken najdete v tématu [podpora více vláken ve starším kódu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 `_beginthreadex`vypadá takto: Win32 [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453.aspx) další rozhraní API úzce než `_beginthread` nepodporuje. `_beginthreadex`se liší od `_beginthread` následujícími způsoby:  
  
-   `_beginthreadex`má tři další parametry: `initflag`, `security`, a `threadaddr`. Nové vlákno lze vytvořit v pozastaveném stavu, zadaný zabezpečení a je přístupný pomocí `thrdaddr`, což je identifikátor přístup z více vláken.  
  
-   Rutiny v `start_address` předá do `_beginthreadex` musí používat `__stdcall` (pro nativní kód) nebo `__clrcall` (pro spravovaný kód) konvence volání a musí vracet ukončovací kód přístup z více vláken.  
  
-   `_beginthreadex`selhání, nikoli L-1, vrátí hodnotu 0.  
  
-   Vlákno, která je vytvořená pomocí `_beginthreadex` je ukončen voláním [_endthreadex](../../c-runtime-library/reference/endthread-endthreadex.md).  
  
 `_beginthreadex` Funkce vám dává větší kontrolu nad vytváření vlákno než `_beginthread` nepodporuje. `_endthreadex` Funkce je také flexibilnější. Například s `_beginthreadex`, můžete pomocí informací o zabezpečení, nastavit počáteční stav vláken (spuštěna nebo pozastavena) a získat přístup z více vláken identifikátor nově vytvořený vlákno. Můžete také použít popisovač podprocesu, který je vrácen `_beginthreadex` se synchronizací rozhraní API, což nelze provést s `_beginthread`.  
  
 Je bezpečnější používat `_beginthreadex` než `_beginthread`. Pokud podproces, který je generován `_beginthread` ukončí rychle obslužná rutina, která je vrácena volajícímu `_beginthread` může být neplatná nebo přejděte na jiné vlákno. Ale popisovač, který je vrácen `_beginthreadex` musí být uzavřené volající `_beginthreadex`, takže ho záruku, že pokud se platný popisovač `_beginthreadex` nevrátil k chybě.  
  
 Můžete volat [_endthread](../../c-runtime-library/reference/endthread-endthreadex.md) nebo `_endthreadex` explicitně k ukončení vlákna; však `_endthread` nebo `_endthreadex` je volána automaticky, když vlákno vrátí z rutiny, která se předá jako parametr. Ukončení vlákna pomocí volání `_endthread` nebo `_endthreadex` pomáhá zajistit, aby správné obnovení prostředků, které jsou přiděleny pro vlákno.  
  
 `_endthread`Zatímco se automaticky zavře popisovač podprocesu `_endthreadex` neexistuje. Proto při použití `_beginthread` a `_endthread`, popisovač podprocesu explicitně nezavírejte voláním Win32 [funkce CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) rozhraní API. Toto chování se liší od Win32 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) rozhraní API.  
  
> [!NOTE]
>  Pro spustitelný soubor, propojený s Libcmt.lib, nevolejte Win32 `ExitThread` rozhraní API, takže nemusíte běhu systému zabránit opětovného získání přidělené prostředky. `_endthread`a `_endthreadex` uvolnit prostředky přidělené vláken a pak zavolají `ExitThread`.  
  
 Operační systém zpracovává přidělení zásobníku při buď `_beginthread` nebo `_beginthreadex` nazývá; nemáte adresu zásobníku vlákno předat některé z těchto funkcí. Kromě toho `stack_size` argument může mít hodnotu 0, ve kterém případ operačního systému používá stejnou hodnotu jako zásobníku, která je zadána pro hlavní vlákno.  
  
 `arglist`je parametr mají být předány nově vytvořený vlákno. Obvykle je to adresa položky dat, jako je řetězec znaků. `arglist`může mít hodnotu NULL, pokud není nutné ji, ale `_beginthread` a `_beginthreadex` musí být uvedeny některé hodnoty, které mají být předána do nové vlákno. Všechna vlákna budou ukončena, pokud žádný přístup z více vláken volání `abort`, `exit`, `_exit`, nebo `ExitProcess`.  
  
 Národní prostředí nové vlákno je zděděno od její nadřazené přístup z více vláken. Pokud je ve volání povoleno národní prostředí podle vláken [_configthreadlocale –](../../c-runtime-library/reference/configthreadlocale.md) (globálně nebo pro nové vlákna), vlákno lze změnit pouze jeho národního prostředí nezávisle z nadřazené voláním `setlocale` nebo `_wsetlocale`. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Pro smíšený a čistý kód `_beginthread` a `_beginthreadex` mají dvě přetížení – má ukazatel na nativní funkci konvence volání, jiné trvá `__clrcall` – ukazatel na funkci. První přetížení není aplikace bezpečných domény a nikdy bude možné. Pokud vytváříte smíšený nebo čistý kód je nutné zajistit, že nové vlákno zadá domény správné aplikace před přistupuje k spravované prostředky. To provedete, například pomocí [call_in_appdomain – funkce](../../dotnet/call-in-appdomain-function.md). Druhý přetížení je aplikace domény bezpečných; nově vytvořený vlákno vždycky skončí v doméně aplikace volající `_beginthread` nebo `_beginthreadex`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_beginthread`|\<Process.h >|  
|`_beginthreadex`|\<Process.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Vícevláknové verzích [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
 Chcete-li použít `_beginthread` nebo `_beginthreadex`, aplikace se musí propojit s jedním z více vláken běhové knihovny jazyka C.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `_beginthread` a `_endthread`.  
  
```  
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
  
// Bounce - Thread to create and and control a colored letter that moves  
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
  
 Stisknutím libovolné klávesy ukázkové aplikace se ukončí.  
  
## <a name="example"></a>Příklad  
 Následující vzorový kód ukazuje, jak můžete použít popisovač podprocesu, který je vrácen `_beginthreadex` se synchronizací rozhraní API [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx). Hlavní vlákno čeká na ukončení před dalším postupem druhý podprocesu. Když druhý vlákno volá `_endthreadex`, způsobí, že jeho vlákno objekt přejít na signalizovaného stavu. To umožňuje primární vlákno dál běžet. Tento krok nelze provést s `_beginthread` a `_endthread`, protože `_endthread` volání `CloseHandle`, který zničí objekt vlákna předtím, než je můžete nastavit signalizovaného stavu.  
  
```  
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
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [_endthread –, _endthreadex](../../c-runtime-library/reference/endthread-endthreadex.md)   
 [přerušení](../../c-runtime-library/reference/abort.md)   
 [ukončení, _exit –, _exit –](../../c-runtime-library/reference/exit-exit-exit.md)   
 [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)