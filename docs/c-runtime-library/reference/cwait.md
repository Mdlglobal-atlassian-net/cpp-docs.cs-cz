---
title: _cwait
ms.date: 11/04/2016
apiname:
- _cwait
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: f7a49497ac71ec15261e1215bd2bbed2e49f42ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288781"
---
# <a name="cwait"></a>_cwait

Počká, až do doby ukončení jiným procesem.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
intptr_t _cwait(
   int *termstat,
   intptr_t procHandle,
   int action
);
```

### <a name="parameters"></a>Parametry

*termstat*<br/>
Ukazatel do vyrovnávací paměti, kam se má uložit výsledek kód určený proces, nebo **NULL**.

*procHandle*<br/>
Popisovač čekání na proces (to znamená, že proces, který má ukončit před **_cwait** může vrátit).

*Akce*<br/>
HODNOTA NULL: Ignorovat podle aplikací operačního systému Windows. u ostatních aplikací: kód akce k provedení na *procHandle*.

## <a name="return-value"></a>Návratová hodnota

Pokud zadaný proces úspěšně dokončil, vrátí popisovač určený proces a nastaví *termstat* kódu výsledek vrácený rutinou určeného procesu. V opačném případě vrátí hodnotu -1 a nastaví **errno** následujícím způsobem.

|Hodnota|Popis|
|-----------|-----------------|
|**ECHILD**|Neexistuje žádný zadaný proces *procHandle* je neplatný nebo volání [metody GetExitCodeProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) nebo [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) rozhraní API se nezdařilo.|
|**EINVAL**|*Akce* je neplatný.|

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Cwait** funkce čeká na ukončení ID procesu určeného procesu, která je poskytována *procHandle*. Hodnota *procHandle* , který je předán **_cwait** by měla být hodnota, který je vrácen voláním [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) funkci, kterou vytvořili určeného procesu. Pokud ID procesu ukončí před **_cwait** se nazývá **_cwait** vrátí hodnotu okamžitě. **_cwait** můžete využívat čekání na další známé proces pro který nějaký proces platný popisovač (*procHandle*) existuje.

*termstat* bodů do vyrovnávací paměti, kam se budou ukládat návratový kód určeného procesu. Hodnota *termstat* označuje, zda určený proces byl korektně ukončen voláním Windows [exitprocess –](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitprocess) rozhraní API. **Exitprocess –** je voláno interně volá zadaný proces **ukončit** nebo **_exit**, vrátí z **hlavní**, nebo dosáhne konce **hlavní** . Další informace o hodnotu, která je předává zpátky pomocí *termstat*, naleznete v tématu [metody GetExitCodeProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Pokud **_cwait** je volána za použití **NULL** hodnota *termstat*, návratový kód určený proces není uložený.

*Akce* parametr je ignorován operačním systémem Windows, protože nejsou implementované vztahů nadřazenosti a podřízenosti v těchto prostředích.

Není-li *procHandle* -1 nebo -2 (zpracuje aktuální proces nebo vlákno), popisovač se zavře. Proto se v takovém případě nepoužívejte Vrácený popisovač.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_cwait.c
// compile with: /c
// This program launches several processes and waits
// for a specified process to finish.

#define _CRT_RAND_S

#include <windows.h>
#include <process.h>
#include <stdlib.h>
#include <stdio.h>
#include <time.h>

// Macro to get a random integer within a specified range
#define getrandom( min, max ) (( (rand_s (&number), number) % (int)((( max ) + 1 ) - ( min ))) + ( min ))

struct PROCESS
{
   int     nPid;
   char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main( int argc, char *argv[] )
{
   int termstat, c;
   unsigned int number;

   srand( (unsigned)time( NULL ) );    // Seed randomizer

   // If no arguments, this is the calling process
   if ( argc == 1 )
   {
      // Spawn processes in numeric order
      for ( c = 0; c < 4; c++ ) {
         _flushall();
         process[c].nPid = _spawnl( _P_NOWAIT, argv[0], argv[0],
                                    process[c].name, NULL );
      }

      // Wait for randomly specified process, and respond when done
      c = getrandom( 0, 3 );
      printf( "Come here, %s.\n", process[c].name );
      _cwait( &termstat, process[c].nPid, _WAIT_CHILD );
      printf( "Thank you, %s.\n", process[c].name );

   }
   // If there are arguments, this must be a spawned process
   else
   {
      // Delay for a period that's determined by process number
      Sleep( (argv[1][0] - 'A' + 1) * 1000L );
      printf( "Hi, Dad. It's %s.\n", argv[1] );
   }
}
```

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
