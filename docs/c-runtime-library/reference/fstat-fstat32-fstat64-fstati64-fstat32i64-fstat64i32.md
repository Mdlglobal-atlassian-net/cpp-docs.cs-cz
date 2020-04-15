---
title: _fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32
ms.date: 4/2/2020
api_name:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
- _o__fstat32
- _o__fstat32i64
- _o__fstat64
- _o__fstat64i32
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 02d297fec2ada545a8b693abacfecc7981149dae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345674"
---
# <a name="_fstat-_fstat32-_fstat64-_fstati64-_fstat32i64-_fstat64i32"></a>_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32

Získá informace o otevřeném souboru.

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

*Fd*<br/>
Popisovač souboru otevřeného souboru.

*Vyrovnávací paměti*<br/>
Ukazatel na strukturu pro uložení výsledků.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud jsou získány informace o stavu souboru. Vrácená hodnota -1 označuje chybu. Pokud je popisovač souboru neplatný nebo *je vyrovnávací paměť* **null**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **je chybné číslo** nastaveno na **EBADF**, v případě neplatného popisovače souboru nebo na **EINVAL**, pokud je *vyrovnávací paměť* **NULL**.

## <a name="remarks"></a>Poznámky

Funkce **_fstat** získá informace o otevřeném souboru přidruženém k *fd* a uloží jej do struktury, na kterou se vztahuje *vyrovnávací paměť*. Struktura **_stat** definovaná v souboru SYS\Stat.h obsahuje následující pole.

|Pole|Význam|
|-|-|
| **st_atime** | Čas posledního přístupu k souboru. |
| **st_ctime** | Čas vytvoření souboru. |
| **st_dev** | Je-li zařízení, *fd*; jinak 0. |
| **st_mode** | Bitová maska pro informace o režimu souboru. **Bit _S_IFCHR** je *nastaven,* pokud fd odkazuje na zařízení. Bit **_S_IFREG** je *nastaven,* pokud fd odkazuje na běžný soubor. Bity pro čtení a zápis jsou nastaveny podle režimu oprávnění souboru. **_S_IFCHR** a další konstanty jsou definovány v SYS\Stat.h. |
| **st_mtime** | Čas poslední změny souboru. |
| **st_nlink** | Vždy 1 na souborových systémech, které nejsou ntfs. |
| **st_rdev** | Je-li zařízení, *fd*; jinak 0. |
| **st_size** | Velikost souboru v bajtů. |

Pokud *fd* odkazuje na zařízení, pole **st_atime**, **st_ctime**, **st_mtime**a **st_size** nejsou smysluplné.

Vzhledem k tomu, že Stat.h používá typ [_dev_t,](../../c-runtime-library/standard-types.md) který je definován v Types.h, musíte do kódu zahrnout Text.h před Stat.h.

**_fstat64**, který používá **__stat64** strukturu, umožňuje vyjádřit data vytváření souborů až do 23:59:59, prosinec 31, 3000, UTC; vzhledem k tomu, že ostatní funkce představují pouze data do 23:59:59 Leden 18, 2038, UTC. Půlnoc 1. ledna 1970 je dolní mez časového období pro všechny tyto funkce.

Varianty těchto funkcí podporují 32bitové nebo 64bitové časové typy a 32bitové nebo 64bitové délky souborů. První číselná přípona (**32** nebo **64**) označuje velikost použitého časového typu; Druhá přípona je **buď i32** nebo **i64**, označující, zda je velikost souboru reprezentována jako 32bitové nebo 64bitové celé číslo.

**_fstat** je ekvivalentní **_fstat64i32**a **_stat struktury** **obsahuje** 64bitový čas. To platí, pokud **není definována _USE_32BIT_TIME_T,** v takovém případě je staré chování v platnosti; **_fstat** používá 32bitový čas a **_stat struktury** **obsahuje** 32bitový čas. Totéž platí pro **_fstati64**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Změny typu a délky souboru _stat

|Functions|_USE_32BIT_TIME_T definován?|Typ času|Typ délky souboru|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|Nedefinováno|64bitová|32bitová|
|**_fstat**|Definovány|32bitová|32bitová|
|**_fstat32**|Definice makra nemá vliv na|32bitová|32bitová|
|**_fstat64**|Definice makra nemá vliv na|64bitová|64bitová|
|**_fstati64**|Nedefinováno|64bitová|64bitová|
|**_fstati64**|Definovány|32bitová|64bitová|
|**_fstat32i64**|Definice makra nemá vliv na|32bitová|64bitová|
|**_fstat64i32**|Definice makra nemá vliv na|64bitová|32bitová|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fstat**|\<sys/stat.h> \<a sys/types.h>|
|**_fstat32**|\<sys/stat.h> \<a sys/types.h>|
|**_fstat64**|\<sys/stat.h> \<a sys/types.h>|
|**_fstati64**|\<sys/stat.h> \<a sys/types.h>|
|**_fstat32i64**|\<sys/stat.h> \<a sys/types.h>|
|**_fstat64i32**|\<sys/stat.h> \<a sys/types.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
[_stat, _wstat funkce](stat-functions.md)<br/>
