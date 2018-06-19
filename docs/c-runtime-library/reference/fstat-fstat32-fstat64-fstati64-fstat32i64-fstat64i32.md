---
title: _fstat –, _fstat32 –, _fstat64 –, _fstati64 –, _fstat32i64 –, _fstat64i32 – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65d77bfdd7922387568ca8257e66f6e19dde1a35
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404965"
---
# <a name="fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32

Získá informace o otevření souboru.

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*FD*<br/>
Soubor popisovače otevření souboru.

*Vyrovnávací paměti*<br/>
Ukazatel na strukturu pro ukládání výsledků.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je získat informace o stavu souboru. Vrácená hodnota -1 označuje chybu. Pokud popisovače souborů je neplatný nebo *vyrovnávací paměti* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **ebadf –**, v případě popisovač souboru je neplatný, nebo na **einval –**, pokud *vyrovnávací paměti* je **NULL**.

## <a name="remarks"></a>Poznámky

**_Fstat –** funkce získává informace o otevření souboru přidružené *fd* a uloží je ve struktuře, na kterou odkazuje *vyrovnávací paměti*. **_Stat –** struktuře, které jsou definované v SYS\Stat.h, obsahuje následující pole.

|Pole|Význam|
|-|-|
**st_atime**|Čas posledního přístupu k souboru.
**st_ctime**|Čas vytvoření souboru.
**st_dev**|Pokud zařízení, *fd*; jinak hodnota 0.
**st_mode –**|Bitová maska režim souboru informace. **_S_ifchr –** Pokud je nastaven bit *fd* odkazuje na zařízení. **_S_ifreg –** Pokud je nastaven bit *fd* odkazuje na soubor obyčejnou. Službu bits pro čtení a zápis jsou nastavena podle režimu oprávnění souboru. **_S_ifchr –** a ostatní konstanty jsou definovány v SYS\Stat.h.
**st_mtime**|Čas poslední změny souboru.
**st_nlink**|Vždy 1 v systémech souborů s jiným systémem souborů NTFS.
**st_rdev**|Pokud zařízení, *fd*; jinak hodnota 0.
**st_size**|Velikost souboru v bajtech.

Pokud *fd* odkazuje na zařízení, **st_atime**, **st_ctime**, **st_mtime**, a **st_size** jsou pole nemá význam.

Protože Stat.h používá [_dev_t –](../../c-runtime-library/standard-types.md) typem, který je definován v Types.h, musí obsahovat Types.h před Stat.h ve vašem kódu.

**_fstat64 –**, které používá **__stat64 –** struktury, zatímco jiné funkce pouze představují datům až 23:59:59 leden 18 umožňuje vytvoření souboru data, která se vyjádřit až do 23:59:59, 31. prosince 3000, UTC. 2038, UTC. Půlnoc, 1. ledna 1970, je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.

Variace tyto funkce podporují typy času 32bitové nebo 64bitové a 32bitové nebo 64bitové verze souboru délky. První číselná přípona (**32** nebo **64**) označuje velikost času typu používaného; druhý přípona buď **i32** nebo **i64**, označující, zda velikost souboru je reprezentována jako 32bitové nebo 64bitové celé číslo.

**_fstat –** je ekvivalentní **_fstat64i32 –**, a **struktura** **_stat –** obsahuje 64-bit čas. Toto je hodnota true, pokud **_USE_32BIT_TIME_T** je definována v takovém případě staré chování je v platnosti; **_fstat –** používá 32bitové čas a **struktura** **_stat –** obsahuje 32-bit čas. Totéž platí pro **_fstati64 –**.

### <a name="time-type-and-file-length-type-variations-of-stat"></a>Typ času a soubor délka typu Variant _stat –

|Funkce|_USE_32BIT_TIME_T definované?|Typ času|Typ délku souboru|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat –**|Nejsou definována.|64bitových|32bitová|
|**_fstat –**|Definované|32bitová|32bitová|
|**_fstat32**|Není vliv na definici – makro|32bitová|32bitová|
|**_fstat64**|Není vliv na definici – makro|64bitových|64bitových|
|**_fstati64**|Nejsou definována.|64bitových|64bitových|
|**_fstati64**|Definované|32bitová|64bitových|
|**_fstat32i64**|Není vliv na definici – makro|32bitová|64bitových|
|**_fstat64i32**|Není vliv na definici – makro|64bitových|32bitová|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fstat –**|\<SYS/stat.h > a \<sys/types.h >|
|**_fstat32**|\<SYS/stat.h > a \<sys/types.h >|
|**_fstat64**|\<SYS/stat.h > a \<sys/types.h >|
|**_fstati64**|\<SYS/stat.h > a \<sys/types.h >|
|**_fstat32i64**|\<SYS/stat.h > a \<sys/types.h >|
|**_fstat64i32**|\<SYS/stat.h > a \<sys/types.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
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

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[_stat, _wstat – funkce](stat-functions.md)<br/>
