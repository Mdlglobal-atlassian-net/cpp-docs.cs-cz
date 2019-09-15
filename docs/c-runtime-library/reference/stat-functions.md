---
title: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32
ms.date: 11/04/2016
api_name:
- _wstat64
- _stati64
- _stat32
- _stat32i64
- _stat
- _wstati64
- _wstat32
- _wstat64i32
- _wstat
- _stat64
- _stat64i32
- _wstat32i64
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
- tstat32
- tstat
- _tstat64i32
- tstati64
- _wstat64
- _wstat32
- wstati64
- tstat64
- _stati64
- _wstat
- wstat64i32
- stat32i64
- tstat32i64
- _tstat
- _wstati64
- _tstati64
- _wstat32i64
- wstat32
- _wstat64i32
- _stat
- _tstat32
- stat64i32
- wstat64
- stat
- _stat32i64
- _stat32
- stati64
- wstat
- _stat64i32
- stat32
- _tstat32i64
- tstat64i32
- _tstat64
- _stat64
- stat/_stat
- stat/_stat32
- stat/_stat64
- stat/_stati64
- stat/_stat32i64
- stat/_stat64i32
- stat/_wstat
- stat/_wstat32
- stat/_wstat64
- stat/_wstati64
- stat/_wstat32i64
- stat/_wstat64i32
helpviewer_keywords:
- files [C++], status information
- _stat function
- _wstat function
- _stat64i32 function
- tstat function
- _tstat64i32 function
- _stati64 function
- _stat64 function
- tstati64 function
- wstati64 function
- wstat64 function
- _wstat64i32 function
- _tstat32i64 function
- _stat32i64 function
- stat function
- status of files
- _tstat32 function
- tstat64 function
- _wstat64 function
- _tstat function
- _stat32 function
- wstat function
- _wstat32i64 function
- _tstati64 function
- _wstat32 function
- stat64 function
- stati64 function
- _wstati64 function
- _tstat64 function
- files [C++], getting status information
ms.assetid: 99a75ae6-ff26-47ad-af70-5ea7e17226a5
ms.openlocfilehash: 5a6e78c0d98871e4becbb5e7411d9c819e9d0596
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957951"
---
# <a name="_stat-_stat32-_stat64-_stati64-_stat32i64-_stat64i32-_wstat-_wstat32-_wstat64-_wstati64-_wstat32i64-_wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

Získat informace o stavu souboru

## <a name="syntax"></a>Syntaxe

```C
int _stat(
   const char *path,
   struct _stat *buffer
);
int _stat32(
   const char *path,
   struct __stat32 *buffer
);
int _stat64(
   const char *path,
   struct __stat64 *buffer
);
int _stati64(
   const char *path,
   struct _stati64 *buffer
);
int _stat32i64(
   const char *path,
   struct _stat32i64 *buffer
);
int _stat64i32(
   const char *path,
   struct _stat64i32 *buffer
);
int _wstat(
   const wchar_t *path,
   struct _stat *buffer
);
int _wstat32(
   const wchar_t *path,
   struct __stat32 *buffer
);
int _wstat64(
   const wchar_t *path,
   struct __stat64 *buffer
);
int _wstati64(
   const wchar_t *path,
   struct _stati64 *buffer
);
int _wstat32i64(
   const wchar_t *path,
   struct _stat32i64 *buffer
);
int _wstat64i32(
   const wchar_t *path,
   struct _stat64i32 *buffer
);
```

### <a name="parameters"></a>Parametry

*Cesta*<br/>
Ukazatel na řetězec obsahující cestu k existujícímu souboru nebo adresáři.

*vyrovnávací paměti*<br/>
Ukazatel na strukturu, která ukládá výsledky.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud jsou získány informace o stavu souboru. Návratová hodnota-1 označuje chybu. v takovém případě je **errno** nastavena na **ENOENT**, což značí, že se nepovedlo najít název souboru nebo cestu. Návratová hodnota **EINVAL** označuje neplatný parametr. **errno** je také v tomto případě nastaveno na **EINVAL** .

Další informace o tomto a dalších návratových kódech naleznete v tématech [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

Časové razítko v souboru může být reprezentované, pokud je pozdější než půlnoc, od 1. ledna 1970 a do 23:59:59, 31. prosince 3000, UTC, pokud nepoužíváte **_stat32** nebo **_wstat32**nebo jste definovali **_USE_32BIT_TIME_T**. v takovém případě může být datum zastoupeno pouze 23:59:59 do 18. ledna 2038, UTC.

## <a name="remarks"></a>Poznámky

Funkce **_stat** získává informace o souboru nebo adresáři určeném *cestou* a ukládá je do struktury, na kterou se odkazuje pomocí *vyrovnávací paměti*. **_stat** automaticky zpracovává argumenty vícebajtového řetězce znaků podle potřeby a rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která se právě používá.

**_wstat** je **_stat**verze s velkým znakem; Argument *cesty* pro **_wstat** je řetězec s velkým znakem. **_wstat** a **_stat** se chovají stejně, s výjimkou toho, že **_wstat** zpracovává řetězce vícebajtových znaků.

Variace těchto funkcí podporují typy s délkou 32 nebo 64 a délky souborů 32 a 64. První číselná přípona (**32** nebo **64**) označuje velikost použitého typu času; Druhá přípona je buď **i32** , nebo **I64**, která označuje, jestli je velikost souboru reprezentována jako 32 nebo 64 celočíselného bitu.

**_stat** je ekvivalentem **_stat64i32**a **Struktura** **_stat** obsahuje 64-bit času. To platí, pokud není definován **_USE_32BIT_TIME_T** , v takovém případě se stará chování projeví. **_stat** používá 32 čas a **struktura** **_stat** obsahuje 32-bit času. Totéž platí pro **_stati64**.

> [!NOTE]
> **_wstat** nefunguje s symbolické odkazy systému Windows Vista. V těchto případech bude **_wstat** vždy hlásit velikost souboru 0. **_stat** funguje správně se symbolických odkazů.

Tato funkce ověří své parametry. Pokud má kterákoli z *cest* nebo *vyrovnávací paměti* **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Typ času a délka souboru – variace typu _stat

|Funkce|_USE_32BIT_TIME_T definovány?|Typ času|Typ délky souboru|
|---------------|------------------------------------|---------------|----------------------|
|**_stat**, **_wstat**|Nedefinováno|64bitová|32bitová|
|**_stat**, **_wstat**|definované|32bitová|32bitová|
|**_stat32**, **_wstat32**|Není ovlivněno definicí makra.|32bitová|32bitová|
|**_stat64**, **_wstat64**|Není ovlivněno definicí makra.|64bitová|64bitová|
|**_stati64**, **_wstati64**|Nedefinováno|64bitová|64bitová|
|**_stati64**, **_wstati64**|definované|32bitová|64bitová|
|**_stat32i64**, **_wstat32i64**|Není ovlivněno definicí makra.|32bitová|64bitová|
|**_stat64i32**, **_wstat64i32**|Není ovlivněno definicí makra.|64bitová|32bitová|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat**|**_stat**|**_stat**|**_wstat**|
|**_tstat64**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

Struktura **_stat** definovaná v SYS\STAT. H obsahuje následující pole.

|Pole||
|-|-|
| **st_gid** | Číselný identifikátor skupiny, který vlastní soubor (specifický pro systém UNIX), bude v systémech Windows vždycky nula. Přesměrovaný soubor je klasifikován jako soubor systému Windows. |
| **st_atime** | Čas posledního přístupu k souboru Platí pro systém souborů NTFS, ale ne pro diskové jednotky ve formátu FAT. |
| **st_ctime** | Čas vytvoření souboru Platí pro systém souborů NTFS, ale ne pro diskové jednotky ve formátu FAT. |
| **st_dev** | Číslo jednotky disku obsahujícího soubor (totéž jako **st_rdev**). |
| **st_ino** | Číslo informačního uzlu ( **inode**) pro soubor (specifický pro systém UNIX). V systémech souborů UNIX **inode** popisuje datum a časová razítka, oprávnění a obsah souboru. Když jsou soubory vzájemně propojeny, sdílejí stejný **inode**. **Inode**, a proto **st_ino**, nemá žádný význam v systémech souborů FAT, HPFS nebo NTFS. |
| **st_mode** | Bitová maska pro informace o režimu souboru. Bit **_S_IFDIR** je nastaven, pokud *cesta* Určuje adresář. bit **_S_IFREG** je nastaven, pokud *cesta* určuje běžný soubor nebo zařízení. Bity čtení a zápisu uživatelů jsou nastaveny v závislosti na režimu oprávnění souboru; bity spouštění uživatele jsou nastaveny podle přípony názvu souboru. |
| **st_mtime** | Čas poslední úpravy souboru |
| **st_nlink** | Vždy 1 v systémech souborů bez NTFS. |
| **st_rdev** | Číslo jednotky disku obsahujícího soubor (totéž jako **st_dev**). |
| **st_size** | Velikost souboru v bajtech; 64 celé číslo pro variace s příponou **I64** . |
| **st_uid** | Číselný identifikátor uživatele, který vlastní soubor (specifický pro systém UNIX). Toto pole bude v systémech Windows vždycky nula. Přesměrovaný soubor je klasifikován jako soubor systému Windows. |

Pokud *cesta* odkazuje na zařízení, pole **st_size**, různá časová pole, **st_dev**a **st_rdev** ve struktuře **_stat** nemají význam. Protože STAT. H používá typ [_dev_t](../../c-runtime-library/standard-types.md) , který je definován v typech. H, je nutné zahrnout typy. H před STATou H ve vašem kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**_stat**, **_stat32**, **_stat64**, **_stati64**, **_stat32i64**, **_stat64i32**|\<sys/Types. h > následovaný \<sys/stat. h >|\<errno.h>|
|**_wstat**, **_wstat32**, **_wstat64**, **_wstati64**, **_wstat32i64**, **_wstat64i32**|\<sys/Types. h > následovaný \<sys/stat. h > nebo \<WCHAR. h >|\<errno.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_stat.c
// This program uses the _stat function to
// report information about the file named crt_stat.c.

#include <time.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   struct _stat buf;
   int result;
   char timebuf[26];
   char* filename = "crt_stat.c";
   errno_t err;

   // Get data associated with "crt_stat.c":
   result = _stat( filename, &buf );

   // Check if statistics are valid:
   if( result != 0 )
   {
      perror( "Problem getting information" );
      switch (errno)
      {
         case ENOENT:
           printf("File %s not found.\n", filename);
           break;
         case EINVAL:
           printf("Invalid parameter to _stat.\n");
           break;
         default:
           /* Should never be reached. */
           printf("Unexpected error in _stat.\n");
      }
   }
   else
   {
      // Output some of the statistics:
      printf( "File size     : %ld\n", buf.st_size );
      printf( "Drive         : %c:\n", buf.st_dev + 'A' );
      err = ctime_s(timebuf, 26, &buf.st_mtime);
      if (err)
      {
         printf("Invalid arguments to ctime_s.");
         exit(1);
      }
      printf( "Time modified : %s", timebuf );
   }
}
```

```Output
File size     : 732
Drive         : C:
Time modified : Thu Feb 07 14:39:36 2002
```

## <a name="see-also"></a>Viz také:

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_setmbcp](setmbcp.md)<br/>
