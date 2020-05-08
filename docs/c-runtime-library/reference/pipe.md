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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d3805de6a591169f94926c09a4542ec01f221d1d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916830"
---
# <a name="_pipe"></a>_pipe

Vytvoří kanál pro čtení a zápis.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ukazatel na pole dvou **int** pro ukládání popisovačů souborů pro čtení a zápis.

*psize*<br/>
Velikost paměti, která se má rezervovat

*textmode*<br/>
Režim souboru.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0. Vrátí hodnotu-1 pro indikaci chyby. Při chybě je **errno** nastaveno na jednu z těchto hodnot:

- **EMFILE**, což znamená, že nejsou k dispozici žádné další popisovače souboru.

- **ENFILE**, která indikuje přetečení tabulky systému souborů.

- **EINVAL**, což znamená, že pole *pfds* je ukazatel s hodnotou null nebo že byla předána neplatná hodnota pro *TextMode* .

Další informace o těchto a dalších návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_pipe** vytvoří *kanál*, což je umělá vstupně-výstupní kanál, který program používá k předávání informací do jiných programů. Kanál se podobá souboru, protože má ukazatel na soubor, popisovač souboru nebo obojí a lze jej číst nebo do něj zapisovat pomocí funkcí vstupní a výstupní knihovny Standard. Kanál však nepředstavuje konkrétní soubor nebo zařízení. Místo toho představuje dočasné úložiště v paměti, které je nezávislé na vlastní paměti programu a řídí se výhradně operačním systémem.

**_pipe** se podobá **_open** , ale otevře kanál pro čtení a zápis a vrátí dva popisovače souborů místo jednoho. Program může použít obě strany kanálu nebo zavřít ten, který nepotřebuje. Například příkazový procesor v systému Windows vytvoří při spuštění příkazu, jako je například **Program1** | **PROGRAM2**, kanál.

Standardní výstupní popisovač **Program1** je připojen k popisovači zápisu kanálu. Standardní vstupní popisovač **PROGRAM2** je připojen k popisovači čtení kanálu. Tím se eliminuje nutnost vytvářet dočasné soubory pro předávání informací do jiných programů.

Funkce **_pipe** vrátí dva popisovače souboru do kanálu v argumentu *pfds* . Element *pfds*[0] obsahuje popisovač čtení a element *pfds*[1] obsahuje popisovač zápisu. Popisovače souborů kanálu jsou používány stejným způsobem jako jiné popisovače souborů. (Vstupní a výstupní funkce nízké úrovně **_read** a **_Write** mohou číst a zapisovat do kanálu.) Chcete-li zjistit podmínku konce kanálu, vyhledejte **_read** požadavek, který vrátí hodnotu 0 jako Počet přečtených bajtů.

Argument *psize* určuje množství paměti (v bajtech), které se má pro kanál vyhradit. Argument *TextMode* určuje režim překladu kanálu. Konstanta manifestu **_O_TEXT** určuje překlad textu a konstanta **_O_BINARY** Určuje binární překlad. (Viz [fopen, _wfopen](fopen-wfopen.md) pro popis textového a binárního režimu.) Pokud je argument *TextMode* 0, **_pipe** používá výchozí režim překladu, který je určený proměnnou výchozího režimu [_fmode](../../c-runtime-library/fmode.md).

V programech s více vlákny není provedeno zamykání. Popisovače souborů, které jsou vraceny, jsou nově otevřeny a neměly by být odkazovány žádným vláknem, dokud se **_pipe** volání nedokončí.

Chcete-li použít funkci **_pipe** ke komunikaci mezi nadřazeným a podřízeným procesem, každý proces musí mít v kanálu otevřený pouze jeden popisovač. Popisovače musí být Opaky: Pokud má nadřazený objekt otevřený popisovač pro čtení, musí mít podřízený objekt otevřený popisovač zápisu. Nejjednodušší způsob, jak to provést, je bitový operátor OR**|**() **_O_NOINHERIT** příznakem *TextMode*. Pak použijte **_dup** nebo **_dup2** k vytvoření dědičné kopie popisovače kanálu, který chcete předat podřízenému. Zavřete původní popisovač a potom vytvořte podřízený proces. Při návratu z volání metody, zavřete duplicitní popisovač v nadřazeném procesu. Další informace najdete v části Příklad 2 dále v tomto článku.

V operačním systému Windows je kanál zničen, když jsou všechny jeho popisovače uzavřeny. (Pokud se všechny popisovače čtení v kanálu zavřely, pak zápis do kanálu způsobí chybu.) Všechny operace čtení a zápisu na kanálu čekají, dokud nebude k dispozici dostatek dat nebo dostatek vyrovnávací paměti pro dokončení vstupně-výstupních požadavků.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_pipe**|\<IO. h>|\<fcntl. h>, 1 \<errno. h>2|

1 pro **_O_BINARY** a definice **_O_TEXT**

2 definice **errno** .

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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

Toto je základní aplikace filtru. Spustí aplikaci crt_pipe_beeper poté, co vytvoří kanál, který přesměruje objekt stdout vytvořené aplikace na filtr. Filtr odstraní znaky ASCII 7 (ZvukovýSignál).

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
