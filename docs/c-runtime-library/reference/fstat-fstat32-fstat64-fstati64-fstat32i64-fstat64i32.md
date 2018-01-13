---
title: "_fstat –, _fstat32 –, _fstat64 –, _fstati64 –, _fstat32i64 –, _fstat64i32 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fstat32i64
- fstat
- fstat64i32
- _fstat64
- _fstati64
- fstat64
- _fstat32
- fstat32i64
- fstati64
- _fstat
- fstat32
- _fstat64i32
dev_langs: C++
helpviewer_keywords:
- _fstat64 function
- fstati64 function
- _fstat64i32 function
- _fstat32i64 function
- _fstat32 function
- file information
- fstat64i32 function
- fstat32 function
- fstat function
- fstat64 function
- _fstat function
- _fstati64 function
- fstat32i64 function
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d2993016e9c6b3a4ea7d47ba8071fab1267e483f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
Získá informace o otevření souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _fstat(   
   int fd,  
   struct _stat *buffer   
);  
int _fstat32(   
   int fd,  
   struct __stat32 *buffer   
);  
int _fstat64(   
   int fd,  
   struct __stat64 *buffer   
);  
int _fstati64(   
   int fd,  
   struct _stati64 *buffer   
);  
int _fstat32i64(   
   int fd,  
   struct _stat32i64 *buffer   
);  
int _fstat64i32(   
   int fd,  
   struct _stat64i32 *buffer   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Soubor popisovače otevření souboru.  
  
 `buffer`  
 Ukazatel na strukturu pro ukládání výsledků.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu 0, pokud je získat informace o stavu souboru. Vrácená hodnota -1 označuje chybu. Pokud popisovače souborů je neplatný nebo `buffer` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EBADF`, v případě popisovač souboru je neplatný, nebo na `EINVAL`, pokud `buffer` je `NULL`.  
  
## <a name="remarks"></a>Poznámky  
 `_fstat` Funkce získává informace o otevření souboru přidružené `fd` a uloží je ve struktuře, na kterou odkazuje `buffer`. `_stat` Struktuře, které jsou definované v SYS\Stat.h, obsahuje následující pole.  
  
 `st_atime`  
 Čas posledního přístupu k souboru.  
  
 `st_ctime`  
 Čas vytvoření souboru.  
  
 `st_dev`  
 Pokud zařízení, `fd`; jinak hodnota 0.  
  
 `st_mode`  
 Bitová maska režim souboru informace. `_S_IFCHR` Pokud je nastaven bit `fd` odkazuje na zařízení. `_S_IFREG` Pokud je nastaven bit `fd` odkazuje na soubor obyčejnou. Službu bits pro čtení a zápis jsou nastavena podle režimu oprávnění souboru. `_S_IFCHR`a ostatní konstanty jsou definovány v SYS\Stat.h.  
  
 `st_mtime`  
 Čas poslední změny souboru.  
  
 `st_nlink`  
 Vždy 1 v systémech souborů s jiným systémem souborů NTFS.  
  
 `st_rdev`  
 Pokud zařízení, `fd`; jinak hodnota 0.  
  
 `st_size`  
 Velikost souboru v bajtech.  
  
 Pokud `fd` odkazuje na zařízení, `st_atime`, `st_ctime`, `st_mtime`, a `st_size` pole nejsou důležité.  
  
 Protože Stat.h používá [_dev_t –](../../c-runtime-library/standard-types.md) typem, který je definován v Types.h, musí obsahovat Types.h před Stat.h ve vašem kódu.  
  
 `_fstat64`, které používá `__stat64` struktury, umožňuje vytvoření souboru data, která se vyjádřit až do 23:59:59, 31. prosince 3000, UTC; zatímco jiné funkce pouze představují datům až 23:59:59 18 leden 2038 UTC. Půlnoc, 1. ledna 1970, je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.  
  
 Variace tyto funkce podporují typy času 32bitové nebo 64bitové a 32bitové nebo 64bitové verze souboru délky. První číselná přípona (`32` nebo `64`) označuje velikost času typu používaného; druhý přípona buď `i32` nebo `i64`, což značí zda velikost souboru je reprezentována jako 32bitové nebo 64bitové celé číslo.  
  
 `_fstat`je ekvivalentní `_fstat64i32`, a `struct _stat` obsahuje 64-bit čas. Toto je hodnota true, pokud `_USE_32BIT_TIME_T` je definována v takovém případě staré chování je v platnosti; `_fstat` používá 32bitové čas a `struct _stat` obsahuje 32-bit čas. Totéž platí pro `_fstati64`.  
  
### <a name="time-type-and-file-length-type-variations-of-stat"></a>Typ času a soubor délka typu Variant _stat –  
  
|Funkce|_USE_32BIT_TIME_T definované?|Typ času|Typ délku souboru|  
|---------------|------------------------------------|---------------|----------------------|  
|`_fstat`|Nejsou definována.|64bitových|32bitová|  
|`_fstat`|Definované|32bitová|32bitová|  
|`_fstat32`|Není vliv na definici – makro|32bitová|32bitová|  
|`_fstat64`|Není vliv na definici – makro|64bitových|64bitových|  
|`_fstati64`|Nejsou definována.|64bitových|64bitových|  
|`_fstati64`|Definované|32bitová|64bitových|  
|`_fstat32i64`|Není vliv na definici – makro|32bitová|64bitových|  
|`_fstat64i32`|Není vliv na definici – makro|64bitových|32bitová|  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fstat`|\<SYS/stat.h > a \<sys/types.h >|  
|`_fstat32`|\<SYS/stat.h > a \<sys/types.h >|  
|`_fstat64`|\<SYS/stat.h > a \<sys/types.h >|  
|`_fstati64`|\<SYS/stat.h > a \<sys/types.h >|  
|`_fstat32i64`|\<SYS/stat.h > a \<sys/types.h >|  
|`_fstat64i32`|\<SYS/stat.h > a \<sys/types.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fstat.c  
// This program uses _fstat to report  
// the size of a file named F_STAT.OUT.  
  
#include <io.h>  
#include <fcntl.h>  
#include <time.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <errno.h>  
#include <share.h>  
  
int main( void )  
{  
   struct _stat buf;  
   int fd, result;  
   char buffer[] = "A line to output";  
   char timebuf[26];  
   errno_t err;  
  
   _sopen_s( &fd,  
             "f_stat.out",  
             _O_CREAT | _O_WRONLY | _O_TRUNC,  
             _SH_DENYNO,  
             _S_IREAD | _S_IWRITE );  
   if( fd != -1 )  
      _write( fd, buffer, strlen( buffer ) );  
  
   // Get data associated with "fd":   
   result = _fstat( fd, &buf );  
  
   // Check if statistics are valid:   
   if( result != 0 )  
   {  
      if (errno == EBADF)  
        printf( "Bad file descriptor.\n" );  
      else if (errno == EINVAL)  
        printf( "Invalid argument to _fstat.\n" );  
   }  
   else  
   {  
      printf( "File size     : %ld\n", buf.st_size );  
      err = ctime_s(timebuf, 26, &buf.st_mtime);  
      if (err)  
      {  
         printf("Invalid argument to ctime_s.");  
         exit(1);  
      }  
      printf( "Time modified : %s", timebuf );  
   }  
   _close( fd );  
}  
```  
  
```Output  
File size     : 16  
Time modified : Wed May 07 15:25:11 2003  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [_access –, _waccess –](../../c-runtime-library/reference/access-waccess.md)   
 [_chmod –, _wchmod –](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_filelength –, _filelengthi64 –](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [_stat, _wstat – funkce](../../c-runtime-library/reference/stat-functions.md)