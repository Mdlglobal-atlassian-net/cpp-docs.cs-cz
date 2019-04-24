---
title: _pipe
ms.date: 11/04/2016
apiname:
- _pipe
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- pipe
- _pipe
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
ms.openlocfilehash: c5db59fecd84ae291e5651b1cec1be31c815e53a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155959"
---
# <a name="pipe"></a>_pipe

Vytvoří kanál pro čtení a zápis.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ukazatel na pole dvou **int** podržte čtení a zápis popisovače souborů.

*psize*<br/>
Množství paměti pro rezervaci.

*textmode*<br/>
Režim souboru.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0. Vrátí hodnotu -1 označuje chybu. Při chybě **errno** nastavena na jednu z těchto hodnot:

- **EMFILE**, což znamená, že nejsou k dispozici žádné další popisovače souboru.

- **ENFILE**, který označuje přetečení tabulce systému souborů.

- **EINVAL**, což znamená, že buď pole *tyto diagramy* je ukazatel s hodnotou null nebo neplatná hodnota pro *v textovém režimu* byla předána.

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**_Pipe –** vytvoří funkci *kanálu*, což je umělý vstupně-výstupní kanál, který program používá k předávání informací do jiných programů. Kanál se podobá souboru, protože má ukazatel souboru, popisovač souboru nebo obojí, a může číst nebo zapisovat do pomocí standardní knihovny vstupu a výstupu funkcí. Kanál však nepředstavuje konkrétní soubor nebo zařízení. Místo toho představuje dočasné úložiště v paměti, která je nezávislá vlastní paměti programu a je řízeno výhradně operačním systémem.

**_pipe –** se podobá **_Otevřít** ale otevře kanál pro čtení a zápis a vrátí dva popisovače souboru místo jednoho. Program můžete používat obě strany kanálu nebo zavřít ten, který nepotřebuje. Například procesor příkazu v Windows vytváří kanál, když je spuštěn příkaz jako **PROGRAM1** | **PROGRAM2**.

Standardní výstupní popisovač **PROGRAM1** se připojuje k popisovači zápisu kanálu. Standardní vstupní popisovač **PROGRAM2** se připojuje k popisovači čtení kanálu. To eliminuje potřebu vytvářet dočasné soubory k předávání informací do jiných programů.

**_Pipe –** funkce vrátí dva popisovače souborů kanálu v *tyto diagramy* argument. Element *tyto diagramy*[0] obsahuje popisovače čtení a prvek *tyto diagramy*[1] obsahuje popisovač zápisu. Popisovače souborů kanálu se používají stejným způsobem jako ostatní popisovače souborů. (Nižší vstupní a výstupní funkce **_read** a **_write** může číst z a zapisovat do kanálu.) Ke zjištění stavu ukončení kanálu, vyhledávat **_read** žádosti, která vrátí hodnotu 0 jako počet přečtených bajtů.

*Psize* argument určuje množství paměti v bajtech, která chcete vyhradit pro kanál. *v textovém režimu* argument určuje režim překladu pro kanál. Konstanta manifestu **_O_TEXT** určuje překlad textu a konstanta **_O_BINARY** Určuje binární překlad. (Viz [fopen _wfopen –](fopen-wfopen.md) popis textu a binárních režimů.) Pokud *v textovém režimu* argument je 0, **_pipe –** používá výchozí režim překladu určený proměnnou výchozího režimu [_fmode](../../c-runtime-library/fmode.md).

Žádné uzamčení se neprovádí v programech s více vlákny. Popisovače souborů, které jsou vráceny, jsou nově otevřeny a neměly by být odkazovány z žádného vlákna do po **_pipe –** dokončení volání.

Použít **_pipe –** funkce ke komunikaci mezi nadřazeným a podřízený proces, musí mít každý proces na kanálu otevřený pouze jeden popisovač. Popisovače musí být opaky: Pokud má nadřazená otevřený popisovač pro čtení, pak musí mít podřízený prvek otevřený popisovač zápisu. Nejjednodušší způsob je do bitového nebo (**|**) **_O_NOINHERIT** s příznakem *v textovém režimu*. Potom použijte **_dup –** nebo **_dup2 –** vytvořte dědičnou kopii popisovače kanálu, které chcete předat do podřízeného. Zavřete původní popisovač a pak spusťte podřízený proces. Při návratu z volání vzniku zavřete duplicitní popisovač v nadřazeném procesu. Další informace naleznete v příkladu 2 dále v tomto článku.

V operačním systému Windows je kanál zničen, když všechny jeho popisovače uzavřeny. (Pokud jsou uzavřené, všechny popisovače čtení na kanálu, pak zápis do kanálu způsobí chybu.) Všechny operace čtení a zápisu na kanálu čekají dokud není k dispozici dostatek dat nebo dostatek vyrovnávací paměti k dokončení požadavku vstupně-výstupních operací.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_pipe**|\<io.h>|\<fcntl.h>,1 \<errno.h>2|

1 pro **_O_BINARY** a **_O_TEXT** definice.

2 **errno** definice.

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

Toto je základní aplikace filtru. To vzniknout aplikaci crt_pipe_beeper po vytvoření kanálu, který přesměruje stdout vytvořené aplikace do filtru. Filtr odstraní znaky ASCII 7 (zvukový signál).

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

Aktuální aplikace filtru:

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

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
