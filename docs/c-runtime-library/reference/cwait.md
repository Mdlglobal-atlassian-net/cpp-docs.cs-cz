---
title: _cwait – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a765a6a51a050b96dfd110c21810248b3bb58e16
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cwait"></a>_cwait

Čeká na jiný proces se ukončuje.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ukazatel na vyrovnávací paměť, kde bude uložena kód výsledku určený proces, nebo hodnota NULL.

*procHandle*<br/>
Proces pro čekání na popisovač (který je proces, který má ukončit před **_cwait –** může vrátit).

*Akce*<br/>
Hodnotu NULL: Ignorovat aplikací operačního systému Windows u ostatních aplikací: kód akce k provedení na *procHandle*.

## <a name="return-value"></a>Návratová hodnota

Po úspěšném dokončení procesu zadaný vrátí popisovač zadaný procesu a nastaví *termstat* na kód výsledku, který vrátí určený proces. Jinak vrátí hodnotu -1 a nastaví **errno** následujícím způsobem.

|Hodnota|Popis|
|-----------|-----------------|
|**ECHILD –**|Žádný zadaný proces existuje, *procHandle* je neplatný nebo volání [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx) nebo [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx) rozhraní API se nezdařilo.|
|**EINVAL –**|*Akce* je neplatný.|

Další informace o těchto a dalších návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Cwait –** funkce čeká na ukončení ID procesu zadaný procesu od *procHandle*. Hodnota *procHandle* předá do **_cwait –** by měla být hodnota, kterou vrátí volání [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) funkce, která vytvořila určený proces. Pokud ID procesu ukončí před **_cwait –** je volána, **_cwait –** vrátí okamžitě. **_cwait –** umožňuje žádné procesem čekat na jiný známé proces, pro který platný popisovač (*procHandle*) existuje.

*termstat* body k uložení návratový kód určený proces vyrovnávací paměti. Hodnota *termstat* označuje, zda zadaný proces ukončen normálně voláním Windows [exitprocess –](http://msdn.microsoft.com/library/windows/desktop/ms682658.aspx) rozhraní API. **Exitprocess –** je volána interně, pokud zadaný procesu volání **ukončete** nebo **_exit –**, vrátí z **hlavní**, nebo dosáhne konce **hlavní** . Další informace o hodnotě, který se předává zpátky pomocí *termstat*, najdete v části [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx). Pokud **_cwait –** nazývá pomocí hodnoty NULL pro *termstat*, není uložen návratový kód určený proces.

*Akce* parametr je ignorován v operačního systému Windows, protože vztahů nadřazenosti a podřízenosti nejsou implementované v těchto prostředích.

Pokud *procHandle* -1 nebo -2 (zpracovává aktuální proces nebo vlákno), budou uzavřeny popisovač. Proto v této situaci, nepoužívejte Vrácený popisovač.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_cwait**|\<Process.h >|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
