---
title: "_pipe – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 95169aa5070493be76db6306f4d5863d6a2e654f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="pipe"></a>_pipe
Vytvoří kanálu pro čtení a zápis.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _pipe(  
   int *pfds,  
   unsigned int psize,  
   int textmode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfds`[2]  
 Pole pro uložení pro čtení a zápis popisovače souborů.  
  
 `psize`  
 Množství paměti rezervovat.  
  
 `textmode`  
 Režim souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu 0. Vrátí hodnotu -1 indikující chybu. V případě chyby `errno` nastaven na jednu z těchto hodnot:  
  
-   `EMFILE`, což naznačuje, že jsou k dispozici žádné další popisovače souborů.  
  
-   `ENFILE`, což naznačuje přetečení tabulce systému souborů.  
  
-   `EINVAL`, což znamená, že buď pole `pfds` je ukazatel s hodnotou null nebo neplatnou hodnotu pro `textmode` byla předána.  
  
 Další informace o těchto a dalších návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_pipe` Funkce vytvoří *kanálu*, což je umělé vstupně-výstupního kanálu, který program používá k předávání informací do jiných programů. Protože jsou popisovače souborů, ukazatele souboru nebo obojí, a může číst nebo zapisovat do pomocí standardní knihovna vstup a výstup funkce se podobá svislicí soubor. Svislicí však nepředstavuje konkrétní soubor nebo zařízení. Místo toho představuje dočasné úložiště v paměti, která je nezávislá vlastní paměti programu a řídí zcela operačního systému.  
  
 `_pipe` podobá `_open` ale otevře kanál pro čtení a zápis a vrátí dva popisovače místo jeden soubor. Program můžete použít obě strany kanálu nebo zavřete ten, který nepotřebuje. Například procesor příkazů ve Windows vytváří kanál, jakmile je spuštěn příkaz například `PROGRAM1 | PROGRAM2`.  
  
 Standardní výstupní popisovač `PROGRAM1` je připojen k popisovač zápisu do kanálu. Standardní vstupní popisovač `PROGRAM2` je připojen k popisovač pro čtení kanálu. Tím se eliminuje potřebu vytvářet dočasné soubory předávat informace do jiných programů.  
  
 `_pipe` Funkce vrátí do kanálu v dva popisovače souborů `pfds` argument. Element `pfds`[0] obsahuje popisovač pro čtení a element `pfds`[1] obsahuje popisovač zápisu. Popisovače souborů kanálu se používají stejným způsobem jako ostatní popisovače souborů. (Nízké úrovně vstupní a výstupní funkce `_read` a `_write` může číst a zapisovat do kanálu.) Ke zjištění podmínky end kanálu, vyhledávat `_read` požadavek, který vrátí hodnotu 0, jako je počet přečtených bajtů.  
  
 `psize` Argument určuje množství paměti, v bajtech, můžete vyhradit pro kanál. `textmode` Argument určuje režim překladu pro kanál. Manifestu konstanta `_O_TEXT` Určuje text překlad a konstantu `_O_BINARY` Určuje binární překlad. (Viz [fopen –, _wfopen –](../../c-runtime-library/reference/fopen-wfopen.md) popis textové a binární režimy.) Pokud `textmode` argument je 0, `_pipe` používá výchozí režim překladu, která je zadána proměnná výchozí režim [_fmode –](../../c-runtime-library/fmode.md).  
  
 Žádné uzamčení se provádí v programy s více vlákny. Popisovače souborů, které jsou vráceny jsou nově otevřené a jakékoli vlákno až po nesmí odkazovat `_pipe` volání je dokončena.  
  
 Použít `_pipe` funkce pro komunikaci mezi procesem nadřazeného a podřízeného procesu, jednotlivých procesů musí mít jenom jeden popisovač otevřít v kanálu. Popisovače musí být opposites: Pokud má nadřazená otevřít popisovač pro čtení, pak podřízený objekt musí mít otevřete popisovač zápisu. Nejjednodušším způsobem je `OR` (`|`) `_O_NOINHERIT` příznak s `textmode`. Poté použijte `_dup` nebo `_dup2` vytvořit zděditelné kopii popisovač kanálu, který chcete předat podřízená. Zavřete původní popisovač a pak vytvořit podřízeného procesu. Na vrácení z volání spawn, zavřete duplicitní popisovač v nadřazené procesu. Další informace najdete v tématu příklad 2 později v tomto článku.  
  
 V operačním systému Windows znakem | zničena při všechny jeho popisovače bylo ukončeno. (Pokud jste uzavřeli všechny čtení popisovače na kanálu, pak zápisu do kanálu způsobí, že k chybě.) Všechny čtení a zápisu operací na kanálu Počkejte, dokud není k dispozici dostatek dat nebo dostatek místa vyrovnávací paměti pro dokončení požadavku vstupně-výstupních operací.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_pipe`|\<io.h>|\<fcntl.h>,1 \<errno.h>2|  
  
 1 pro `_O_BINARY` a `_O_TEXT` definice.  
  
 2 `errno` definice.  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
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
 Toto je základní filtru aplikací. Crt_pipe_beeper aplikace se vytvoří po vytvoření kanálu, který přesměruje vytvořená aplikace stdout filtru. Filtr odebere znaky ASCII 7 (zvukového signálu).  
  
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
  
 Skutečné filtru aplikací:  
  
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
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)