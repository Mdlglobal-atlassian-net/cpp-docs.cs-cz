---
title: _pipe
ms.date: 4/2/2020
api_name:
- _pipe
- _o__pipe
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- pipe
- _pipe
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
ms.openlocfilehash: 5bac435bed26decee0069f5814d1f3d25a54470a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338500"
---
# <a name="_pipe"></a>_pipe

Vytvoří potrubí pro čtení a zápis.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _pipe(
   int *pfds,
   unsigned int psize,
   int textmode
);
```

### <a name="parameters"></a>Parametry

*pfds*<br/>
Ukazatel na pole dvou **int** pro uložení popisovačů souboru pro čtení a zápis.

*pvelikost*<br/>
Množství paměti k rezervaci.

*Textové*<br/>
Režim souboru.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je úspěšná. Vrátí hodnotu -1 označující chybu. Při chybě je **chybné číslo** nastaveno na jednu z těchto hodnot:

- **EMFILE**, což znamená, že nejsou k dispozici žádné další popisovače souborů.

- **ENFILE**, což znamená přetečení systémové tabulky.

- **EINVAL**, což znamená, že buď pole *pfds* je nulový ukazatel nebo že byla předána neplatná hodnota pro *textmode.*

Další informace o těchto a dalších návratových kódech naleznete [v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_pipe** vytvoří *kanál*, což je umělý vstupně-o kanál, který program používá k předání informací jiným programům. Kanál se podobá souboru, protože má ukazatel souboru, popisovač souboru nebo obojí a lze jej číst nebo zapisovat pomocí vstupních a výstupních funkcí standardní knihovny. Potrubí však nepředstavuje konkrétní soubor nebo zařízení. Místo toho představuje dočasné úložiště v paměti, která je nezávislá na vlastní paměti programu a je řízena výhradně operačním systémem.

**_pipe** se podobá **_open** ale otevře kanál pro čtení a zápis a vrátí dva popisovače souborů namísto jednoho. Program může použít obě strany potrubí nebo zavřít ten, který nepotřebuje. Například procesor příkazů v systému Windows vytvoří kanál při spuštění příkazu, například **PROGRAM1** | **PROGRAM2**.

Standardní výstupní popisovač **programu 1** je připojen k popisovači zápisu kanálu. Standardní vstupní popisovač **programu 2** je připojen k popisovači čtení kanálu. To eliminuje potřebu vytvářet dočasné soubory pro předání informací jiným programům.

Funkce **_pipe** vrátí dva popisovače souborů do kanálu v argumentu *pfds.* Element *pfds*[0] obsahuje popisovač čtení a prvek *pfds*[1] obsahuje popisovač zápisu. Popisovače souborů kanálu se používají stejným způsobem jako ostatní popisovače souborů. (Nízkoúrovňové vstupní a výstupní funkce **_read** a **_write** mohou číst z kanálu a zapisovat do něj.) Chcete-li zjistit podmínku konce kanálu, zkontrolujte **požadavek _read,** který vrátí 0 jako počet přečtených bajtů.

Argument *psize* určuje velikost paměti v bajtů, chcete-li rezervovat pro potrubí. Argument *mode text* určuje režim překladu pro kanál. Konstanta manifestu **_O_TEXT** určuje textový překlad a konstantní **_O_BINARY** určuje binární překlad. (Viz [fopen, _wfopen](fopen-wfopen.md) popis textu a binární režimy.) Pokud je argument *textmode* 0, **_pipe** použije výchozí režim překladu, který je určen proměnnou výchozího režimu [_fmode](../../c-runtime-library/fmode.md).

V programech s více vlákny se neprovádí žádné zamykání. Popisovače souborů, které jsou vráceny, jsou nově otevřeny a neměly by být odkazovány žádným vláknem, dokud nebude **dokončeno volání _pipe.**

Chcete-li použít **funkci _pipe** ke komunikaci mezi nadřazeným procesem a podřízeným procesem, musí mít každý proces v kanálu otevřený pouze jeden popisovač. Popisovače musí být protiklady: pokud má nadřazený popisovač čtení otevřený, potom podřízený musí mít otevřený popisovač zápisu. Nejjednodušší způsob, jak to udělat, je**|** bitové nebo ( ) **příznak _O_NOINHERIT** s *textmode*. Potom použijte **_dup** nebo **_dup2** k vytvoření dědičné kopie popisovače kanálu, který chcete předat podřízenému. Zavřete původní deskriptor a potom spusťte podřízený proces. Po návratu z pawwn volání zavřete duplicitní popisovač v nadřazeném procesu. Další informace naleznete v příkladu 2 dále v tomto článku.

V operačním systému Windows je kanál zničen, když byly uzavřeny všechny jeho popisovače. (Pokud byly uzavřeny všechny popisovače čtení na kanálu, pak zápis do kanálu způsobí chybu.) Všechny operace čtení a zápisu na kanálu počkejte, dokud nebude dostatek dat nebo dostatek místa ve vyrovnávací paměti k dokončení požadavku na vstupně-va.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_pipe**|\<io.h>|\<fcntl.h>,1 \<errno.h>2|

1 Pro **definice _O_BINARY** a **_O_TEXT.**

2 **errno** definice.

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="example-1"></a>Příklad 1

```C
// crt_pipe.c
/* This program uses the _pipe function to pass streams of
* text to spawned processes.
*/

#include <stdlib.h>
#include <stdio.h>
#include <io.h>
#include <fcntl.h>
#include <process.h>
#include <math.h>

enum PIPES { READ, WRITE }; /* Constants 0 and 1 for READ and WRITE */
#define NUMPROBLEM 8

int main( int argc, char *argv[] )
{

   int fdpipe[2];
   char hstr[20];
   int pid, problem, c;
   int termstat;

   /* If no arguments, this is the spawning process */
   if( argc == 1 )
   {

      setvbuf( stdout, NULL, _IONBF, 0 );

      /* Open a set of pipes */
      if( _pipe( fdpipe, 256, O_BINARY ) == -1 )
          exit( 1 );

      /* Convert pipe read descriptor to string and pass as argument
       * to spawned program. Program spawns itself (argv[0]).
       */
      _itoa_s( fdpipe[READ], hstr, sizeof(hstr), 10 );
      if( ( pid = _spawnl( P_NOWAIT, argv[0], argv[0],
            hstr, NULL ) ) == -1 )
          printf( "Spawn failed" );

      /* Put problem in write pipe. Since spawned program is
       * running simultaneously, first solutions may be done
       * before last problem is given.
       */
      for( problem = 1000; problem <= NUMPROBLEM * 1000; problem += 1000)
      {

         printf( "Son, what is the square root of %d?\n", problem );
         _write( fdpipe[WRITE], (char *)&problem, sizeof( int ) );

      }

      /* Wait until spawned program is done processing. */
      _cwait( &termstat, pid, WAIT_CHILD );
      if( termstat & 0x0 )
         printf( "Child failed\n" );

      _close( fdpipe[READ] );
      _close( fdpipe[WRITE] );

   }

   /* If there is an argument, this must be the spawned process. */
   else
   {

      /* Convert passed string descriptor to integer descriptor. */
      fdpipe[READ] = atoi( argv[1] );

      /* Read problem from pipe and calculate solution. */
      for( c = 0; c < NUMPROBLEM; c++ )
      {

        _read( fdpipe[READ], (char *)&problem, sizeof( int ) );
        printf( "Dad, the square root of %d is %3.2f.\n",
                 problem, sqrt( ( double )problem ) );

      }
   }
}
```

```Output
Son, what is the square root of 1000?
Son, what is the square root of 2000?
Son, what iDad, the square root of 1000 is 31.62.
Dad, the square root of 2000 is 44.72.
s the square root of 3000?
Dad, the square root of 3000 is 54.77.
Son, what is the square root of 4000?
Dad, the square root of 4000 is 63.25.
Son, what is the square root of 5000?
Dad, the square root of 5000 is 70.71.
Son, what is the square root of 6000?
SonDad, the square root of 6000 is 77.46.
, what is the square root of 7000?
Dad, the square root of 7000 is 83.67.
Son, what is the square root of 8000?
Dad, the square root of 8000 is 89.44.
```

## <a name="example-2"></a>Příklad 2

Toto je základní aplikace filtru. Vytvoří aplikace crt_pipe_beeper poté, co vytvoří potrubí, které směruje stdout zplodil aplikace na filtr. Filtr odstraní znaky ASCII 7 (pípnutí).

```C
// crt_pipe_beeper.c

#include <stdio.h>
#include <string.h>

int main()
{
   int   i;
   for(i=0;i<10;++i)
      {
         printf("This is speaker beep number %d...\n\7", i+1);
      }
   return 0;
}
```

Skutečná aplikace filtru:

```C
// crt_pipe_BeepFilter.C
// arguments: crt_pipe_beeper.exe

#include <windows.h>
#include <process.h>
#include <memory.h>
#include <string.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>

#define   OUT_BUFF_SIZE 512
#define   READ_FD 0
#define   WRITE_FD 1
#define   BEEP_CHAR 7

char szBuffer[OUT_BUFF_SIZE];

int Filter(char* szBuff, ULONG nSize, int nChar)
{
   char* szPos = szBuff + nSize -1;
   char* szEnd = szPos;
   int nRet = nSize;

   while (szPos > szBuff)
   {
      if (*szPos == nChar)
         {
            memmove(szPos, szPos+1, szEnd - szPos);
            --nRet;
         }
      --szPos;
   }
   return nRet;
}

int main(int argc, char** argv)
{
   int nExitCode = STILL_ACTIVE;
   if (argc >= 2)
   {
      HANDLE hProcess;
      int fdStdOut;
      int fdStdOutPipe[2];

      // Create the pipe
      if(_pipe(fdStdOutPipe, 512, O_NOINHERIT) == -1)
         return   1;

      // Duplicate stdout file descriptor (next line will close original)
      fdStdOut = _dup(_fileno(stdout));

      // Duplicate write end of pipe to stdout file descriptor
      if(_dup2(fdStdOutPipe[WRITE_FD], _fileno(stdout)) != 0)
         return   2;

      // Close original write end of pipe
      _close(fdStdOutPipe[WRITE_FD]);

      // Spawn process
      hProcess = (HANDLE)_spawnvp(P_NOWAIT, argv[1],
       (const char* const*)&argv[1]);

      // Duplicate copy of original stdout back into stdout
      if(_dup2(fdStdOut, _fileno(stdout)) != 0)
         return   3;

      // Close duplicate copy of original stdout
      _close(fdStdOut);

      if(hProcess)
      {
         int nOutRead;
         while   (nExitCode == STILL_ACTIVE)
         {
            nOutRead = _read(fdStdOutPipe[READ_FD],
             szBuffer, OUT_BUFF_SIZE);
            if(nOutRead)
            {
               nOutRead = Filter(szBuffer, nOutRead, BEEP_CHAR);
               fwrite(szBuffer, 1, nOutRead, stdout);
            }

            if(!GetExitCodeProcess(hProcess,(unsigned long*)&nExitCode))
               return 4;
         }
      }
   }
   return nExitCode;
}
```

```Output
This is speaker beep number 1...
This is speaker beep number 2...
This is speaker beep number 3...
This is speaker beep number 4...
This is speaker beep number 5...
This is speaker beep number 6...
This is speaker beep number 7...
This is speaker beep number 8...
This is speaker beep number 9...
This is speaker beep number 10...
```

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
