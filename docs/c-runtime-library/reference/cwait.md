---
title: _cwait
ms.date: 4/2/2020
api_name:
- _cwait
- _o__cwait
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
- api-ms-win-crt-process-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: d54f62c8ce391b2c8ead92a0a73ac48e6f2b3cb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348153"
---
# <a name="_cwait"></a>_cwait

Čeká, dokud neskončí jiný proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ukazatel na vyrovnávací paměť, kde bude uložen kód výsledku zadaného procesu nebo **NULL**.

*procHandle*<br/>
Popisovač procesu čekat na (to znamená, že proces, který má ukončit před **_cwait** může vrátit).

*Akce*<br/>
NULL: Ignorováno aplikacemi operačního systému Windows; pro ostatní aplikace: kód akce, který se má provádět na *procHandle*.

## <a name="return-value"></a>Návratová hodnota

Po úspěšném dokončení zadaného procesu vrátí popisovač zadaného procesu a nastaví *termstat* na kód výsledku, který je vrácen zadaným procesem. V opačném případě vrátí -1 a nastaví **errno** následujícím způsobem.

|Hodnota|Popis|
|-----------|-----------------|
|**ECHILD**|Neexistuje žádný zadaný proces, *procHandle* je neplatný nebo volání [rozhraní GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) nebo [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) API se nezdařilo.|
|**EINVAL**|*akce* je neplatná.|

Další informace o těchto a dalších návratových kódech naleznete [v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_cwait** čeká na ukončení ID procesu zadaného procesu, který je poskytován *procHandle*. Hodnota *procHandle,* která je předána **_cwait** by měla být hodnota, která je vrácena volání [m _spawnj.](../../c-runtime-library/spawn-wspawn-functions.md) Pokud ID procesu ukončí před **_cwait** je volána, **_cwait** vrátí okamžitě. **_cwait** může být použit libovolný proces čekat na jakýkoli jiný známý proces, pro který existuje platný popisovač (*procHandle).*

*termstat* odkazuje na vyrovnávací paměť, kde bude uložen návratový kód zadaného procesu. Hodnota *termstat označuje,* zda zadaný proces ukončen normálně voláním rozhraní API [ExitProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) systému Windows. **ExitProcess** je volána interně, pokud zadaný proces volá **exit** nebo **_exit**, vrátí z **hlavní**nebo dosáhne konce **hlavní**. Další informace o hodnotě, která je předána zpět prostřednictvím *termstat*, naleznete v [tématu GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Pokud **_cwait** je volána pomocí hodnoty **NULL** pro *termstat*, návratový kód zadaného procesu není uložen.

Parametr *akce* je ignorován operačním systémem Windows, protože vztahy nadřazený podřízený nejsou implementovány v těchto prostředích.

Pokud *procHandle* je -1 nebo -2 (zpracovává aktuální proces nebo vlákno), popisovač bude uzavřen. Proto v této situaci nepoužívejte vrácený popisovač.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
