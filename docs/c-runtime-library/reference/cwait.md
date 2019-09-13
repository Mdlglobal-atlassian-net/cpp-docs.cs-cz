---
title: _cwait
ms.date: 11/04/2016
api_name:
- _cwait
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
ms.openlocfilehash: b4be342ef528959bae22917bc59eef5a953aa4ae
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937747"
---
# <a name="_cwait"></a>_cwait

Počká, dokud nebude ukončen jiný proces.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ukazatel na vyrovnávací paměť, kde bude uložen kód výsledku určeného procesu, nebo **hodnota null**.

*procHandle*<br/>
Popisovač procesu, na kterém se má čekat (to znamená, že proces, který musí skončit před **_cwait** může vracet).

*kroky*<br/>
HODNOTA NULL: Ignorují se v aplikacích operačního systému Windows. pro ostatní aplikace: kód akce, který se má provést na *procHandle*.

## <a name="return-value"></a>Návratová hodnota

Po úspěšném dokončení zadaného procesu vrátí popisovač zadaného procesu a nastaví *termstat* na kód výsledku vrácený zadaným procesem. V opačném případě vrátí hodnotu-1 a nastaví **errno** následujícím způsobem.

|Value|Popis|
|-----------|-----------------|
|**ECHILD**|Neexistuje žádný zadaný proces, *procHandle* je neplatný nebo volání rozhraní API [GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) nebo [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) selhalo.|
|**EINVAL**|*Akce* je neplatná.|

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_cwait** čeká na ukončení ID procesu zadaného procesu, který poskytuje *procHandle*. Hodnota *procHandle* , která je předána **_cwait** , by měla být hodnota, která je vrácena voláním funkce [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) , která vytvořila zadaný proces. Pokud ID procesu končí před voláním **_cwait** , **_cwait** se vrátí hned. **_cwait** může použít jakýkoli proces čekání na jiný známý proces, pro který existuje platný popisovač (*procHandle*).

*termstat* odkazuje na vyrovnávací paměť, kde bude uložen návratový kód zadaného procesu. Hodnota *termstat* označuje, zda byl zadaný proces normálním způsobem ukončen voláním rozhraní API systému Windows [ExitProcess –](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) . **ExitProcess –** se nazývá interně, pokud zadaný proces volá **Exit** nebo **_exit**, vrátí hodnotu z **Main**nebo dosáhne konce **Main**. Další informace o hodnotě, která se předává zpět prostřednictvím *termstat*, najdete v tématu [GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Pokud je **_cwait** volána pomocí hodnoty **null** pro *termstat*, návratový kód zadaného procesu není uložen.

Operační systém Windows ignoruje parametr *Action* , protože relace nadřazený-podřízený nejsou v těchto prostředích implementovány.

Pokud *procHandle* je-1 nebo-2 (zpracovává aktuální proces nebo vlákno), popisovač bude zavřen. Proto v takovém případě nepoužívejte vrácený popisovač.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_cwait**|\<Process. h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
