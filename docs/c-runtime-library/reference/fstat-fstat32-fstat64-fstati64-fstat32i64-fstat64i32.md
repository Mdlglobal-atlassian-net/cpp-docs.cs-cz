---
title: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
ms.date: 11/04/2016
api_name:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 1ab71071fdf5578295cfcd72f79930787e634d5f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956466"
---
# <a name="_fstat-_fstat32-_fstat64-_fstati64-_fstat32i64-_fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32

Načte informace o otevřeném souboru.

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

*fd*<br/>
Popisovač souboru otevřeného souboru

*vyrovnávací paměti*<br/>
Ukazatel na strukturu pro uložení výsledků.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud jsou získány informace o stavu souboru. Návratová hodnota-1 označuje chybu. Pokud je popisovač souboru neplatný nebo má *vyrovnávací paměť* **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EBADF**, v případě neplatného deskriptoru souboru nebo na **EINVAL**, pokud má *vyrovnávací paměť* **hodnotu null**.

## <a name="remarks"></a>Poznámky

Funkce **_fstat** získává informace o otevřeném souboru přidruženém ke *FD* a ukládá je do struktury, na kterou odkazovalo pomocí *vyrovnávací paměti*. Struktura **_stat** definovaná v SYS\Stat.h obsahuje následující pole.

|Pole|Význam|
|-|-|
| **st_atime** | Čas posledního přístupu k souboru |
| **st_ctime** | Čas vytvoření souboru |
| **st_dev** | Pokud zařízení, *FD*; v opačném případě 0. |
| **st_mode** | Bitová maska pro informace o režimu souboru. Bit **_S_IFCHR** je nastaven, pokud má *FD* odkaz na zařízení. Bit **_S_IFREG** je nastaven, pokud *FD* odkazuje na běžný soubor. Bity pro čtení a zápis jsou nastaveny v závislosti na režimu oprávnění souboru. **_S_IFCHR** a další konstanty jsou definovány v SYS\Stat.h. |
| **st_mtime** | Čas poslední změny souboru. |
| **st_nlink** | Vždy 1 v systémech souborů bez NTFS. |
| **st_rdev** | Pokud zařízení, *FD*; v opačném případě 0. |
| **st_size** | Velikost souboru v bajtech |

Pokud *FD* odkazuje na zařízení, pole **st_atime**, **st_ctime**, **st_mtime**a **st_size** nejsou smysluplná.

Vzhledem k tomu, že stat. h používá typ [_dev_t](../../c-runtime-library/standard-types.md) , který je definován v Types. h, musíte zahrnout Types. h před stat. h ve vašem kódu.

**_fstat64**, která používá strukturu **__stat64** , umožňuje, aby data vytváření souborů byla vyjádřena až 23:59:59, 31. prosince 3000, UTC; zatímco jiné funkce reprezentují jenom kalendářní data až 23:59:59. ledna 2038, UTC. Půlnoc, 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.

Variace těchto funkcí podporují 32 nebo 64 typů času a 32 bitů a délky ne64 bitové kopie souboru. První číselná přípona (**32** nebo **64**) označuje velikost použitého typu času; Druhá přípona je buď **i32** , nebo **I64**, která označuje, jestli je velikost souboru reprezentována jako 32 nebo 64 celočíselného bitu.

**_fstat** je ekvivalentem **_fstat64i32**a **Struktura** **_stat** obsahuje 64-bit času. To platí, pokud není definován **_USE_32BIT_TIME_T** , v takovém případě se stará chování projeví. **_fstat** používá 32 čas a **struktura** **_stat** obsahuje 32-bit času. Totéž platí pro **_fstati64**.

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Typ času a délka souboru – variace typu _stat

|Funkce|_USE_32BIT_TIME_T definovány?|Typ času|Typ délky souboru|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|Nedefinováno|64bitová|32bitová|
|**_fstat**|definované|32bitová|32bitová|
|**_fstat32**|Není ovlivněno definicí makra.|32bitová|32bitová|
|**_fstat64**|Není ovlivněno definicí makra.|64bitová|64bitová|
|**_fstati64**|Nedefinováno|64bitová|64bitová|
|**_fstati64**|definované|32bitová|64bitová|
|**_fstat32i64**|Není ovlivněno definicí makra.|32bitová|64bitová|
|**_fstat64i32**|Není ovlivněno definicí makra.|64bitová|32bitová|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fstat**|\<sys/stat. h > a \<sys/Types. h >|
|**_fstat32**|\<sys/stat. h > a \<sys/Types. h >|
|**_fstat64**|\<sys/stat. h > a \<sys/Types. h >|
|**_fstati64**|\<sys/stat. h > a \<sys/Types. h >|
|**_fstat32i64**|\<sys/stat. h > a \<sys/Types. h >|
|**_fstat64i32**|\<sys/stat. h > a \<sys/Types. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
[_stat, funkce _wstat](stat-functions.md)<br/>
