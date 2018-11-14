---
title: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
ms.date: 11/04/2016
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
ms.openlocfilehash: 36d8b0d6480266f86136119a470fb7af5859a5b8
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331240"
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
Popisovač souboru otevřený souboru.

*Vyrovnávací paměti*<br/>
Ukazatel na strukturu pro ukládání výsledků.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je získat informace o stavu souboru. Návratová hodnota-1 označuje chybu. Pokud popisovač souboru je neplatný nebo *vyrovnávací paměti* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EBADF**, v případě neplatného popisovače souboru, nebo do adresáře **EINVAL**, pokud *vyrovnávací paměti* je **NULL**.

## <a name="remarks"></a>Poznámky

**_Fstat** funkce získává informace o otevřený soubor přidružený k *fd* a uloží jej do struktury, na které odkazuje *vyrovnávací paměti*. **_Stat** struktury definované v SYS\Stat.h, obsahuje následující pole.

|Pole|Význam|
|-|-|
| **st_atime** | Čas posledního přístupu k souboru. |
| **st_ctime** | Čas vytvoření souboru. |
| **st_dev** | Pokud zařízení, *fd*; jinak 0. |
| **st_mode –** | Bitová maska informace režim souboru. **_S_IFCHR** bit nastaven, pokud *fd* odkazuje na zařízení. **_S_IFREG** bit nastaven, pokud *fd* odkazuje na soubor běžné. Bits pro čtení a zápis nastaveny podle režimu oprávnění k souboru. **_S_IFCHR** a ostatní konstanty jsou definovány v SYS\Stat.h. |
| **st_mtime** | Čas poslední změny souboru. |
| **st_nlink** | Vždy 1 v systémech souborů než NTFS. |
| **st_rdev** | Pokud zařízení, *fd*; jinak 0. |
| **st_size** | Velikost souboru v bajtech. |

Pokud *fd* odkazuje na zařízení, **st_atime**, **st_ctime**, **st_mtime**, a **st_size** pole jsou nemá význam.

Vzhledem k tomu používá Stat.h [_dev_t](../../c-runtime-library/standard-types.md) typ, který je definován v Types.h, je nutné zahrnout Types.h před Stat.h ve vašem kódu.

**_fstat64**, který používá **__stat64 –** struktury, umožňuje vytvoření souboru data vyjadřují až do 23:59:59, 31 prosince 3000 UTC, zatímco jiné funkce pouze představuje data do 23:59:59 18. ledna 2038 UTC. Půlnoc 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.

Variace z těchto funkcí podporovaly typy času 32bitové nebo 64bitové a 32bitové nebo 64bitové souboru. První číselná přípona (**32** nebo **64**) označuje velikost času používá typ; druhý přípony je buď **i32** nebo **i64**, označující, zda velikost souboru je reprezentován jako 32bitový nebo 64bitové celé číslo.

**_fstat** je ekvivalentní **_fstat64i32 –**, a **struktura** **_stat** obsahuje 64-bit čas. To platí Pokud **_USE_32BIT_TIME_T** je definován v takovém případě je v platnosti; staré chování **_fstat** používá čas 32-bit, a **struktura** **_stat** obsahuje čas 32-bit. Totéž platí pro **_fstati64**.

### <a name="time-type-and-file-length-type-variations-of-stat"></a>Typ času a soubor délka typ Variant _stat –

|Funkce|_USE_32BIT_TIME_T definované?|Typ času|Délka typu souboru|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|Nedefinovaná.|64bitových|32bitová|
|**_fstat**|Definice|32bitová|32bitová|
|**_fstat32**|Není ovlivněna definici makra|32bitová|32bitová|
|**_fstat64**|Není ovlivněna definici makra|64bitových|64bitových|
|**_fstati64**|Nedefinovaná.|64bitových|64bitových|
|**_fstati64**|Definice|32bitová|64bitových|
|**_fstat32i64**|Není ovlivněna definici makra|32bitová|64bitových|
|**_fstat64i32**|Není ovlivněna definici makra|64bitových|32bitová|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fstat**|\<SYS/stat.h > a \<sys/types.h >|
|**_fstat32**|\<SYS/stat.h > a \<sys/types.h >|
|**_fstat64**|\<SYS/stat.h > a \<sys/types.h >|
|**_fstati64**|\<SYS/stat.h > a \<sys/types.h >|
|**_fstat32i64**|\<SYS/stat.h > a \<sys/types.h >|
|**_fstat64i32**|\<SYS/stat.h > a \<sys/types.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[_stat, _wstat – funkce](stat-functions.md)<br/>
