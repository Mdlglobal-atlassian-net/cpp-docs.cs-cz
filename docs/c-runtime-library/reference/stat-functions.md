---
title: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32
ms.date: 4/2/2020
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
- _o__stat32
- _o__stat32i64
- _o__stat64
- _o__stat64i32
- _o__wstat32
- _o__wstat32i64
- _o__wstat64
- _o__wstat64i32
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
ms.openlocfilehash: 32a96a93eb8a18e366ac7a075b414dbca732fb61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355420"
---
# <a name="_stat-_stat32-_stat64-_stati64-_stat32i64-_stat64i32-_wstat-_wstat32-_wstat64-_wstati64-_wstat32i64-_wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

Získejte informace o stavu souboru.

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

*Cestu*<br/>
Ukazatel na řetězec obsahující cestu existujícího souboru nebo adresáře.

*Vyrovnávací paměti*<br/>
Ukazatel na strukturu, která ukládá výsledky.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí hodnotu 0, pokud jsou získány informace o stavu souboru. Vrácená hodnota -1 označuje chybu, v takovém případě je **chybová** hodnota nastavena na **Hodnotu ENOENT**, což znamená, že název souboru nebo cesta nebyla nalezena. Vrácená hodnota **EINVAL** označuje neplatný parametr; **errno** je v tomto případě také nastavenna na **EINVAL.**

Další informace o tomto a dalších návratových kódech naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

Razítko data v souboru může být reprezentováno **_USE_32BIT_TIME_T** **_wstat32** **_stat32,** pokud je pozdější než o půlnoci, 1.

## <a name="remarks"></a>Poznámky

Funkce **_stat** získá informace o souboru nebo adresáři určeném *cestou* a uloží je do struktury, na kterou se vztahuje *vyrovnávací paměť*. **_stat** podle potřeby automaticky zpracovává argumenty vícebajtových řetězců a rozpozná se sekvence vícebajtových znaků podle aktuálně používáné vícebajtové znakové stránky.

**_wstat** je širokoznaková verze **_stat**; argument *cesty* k **_wstat** je řetězec s širokým znakem. **_wstat** a **_stat** se chovají stejně s tím rozdílem, že **_wstat** nezpracovává vícebajtové řetězce znaků.

Varianty těchto funkcí podporují 32bitové nebo 64bitové časové typy a 32bitové nebo 64bitové délky souborů. První číselná přípona (**32** nebo **64**) označuje velikost použitého časového typu; Druhá přípona je **buď i32** nebo **i64**, označující, zda je velikost souboru reprezentována jako 32bitové nebo 64bitové celé číslo.

**_stat** je ekvivalentní **_stat64i32**a **_stat struktury** **obsahuje** 64bitový čas. To platí, pokud **není definována _USE_32BIT_TIME_T,** v takovém případě je staré chování v platnosti; **_stat** používá 32bitový čas a **_stat struktury** **obsahuje** 32bitový čas. Totéž platí pro **_stati64**.

> [!NOTE]
> **_wstat** nefunguje se symbolickými odkazy systému Windows Vista. V těchto případech **_wstat** vždy nahlásí velikost souboru 0. **_stat** funguje správně se symbolickými odkazy.

Tato funkce ověřuje její parametry. Pokud je *buď cesta* nebo *vyrovnávací paměť* **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Změny typu a délky souboru _stat

|Functions|_USE_32BIT_TIME_T definován?|Typ času|Typ délky souboru|
|---------------|------------------------------------|---------------|----------------------|
|**_stat**, **_wstat**|Nedefinováno|64bitová|32bitová|
|**_stat**, **_wstat**|Definovány|32bitová|32bitová|
|**_stat32** **_wstat32**|Definice makra nemá vliv na|32bitová|32bitová|
|**_stat64**, **_wstat64**|Definice makra nemá vliv na|64bitová|64bitová|
|**_stati64**, **_wstati64**|Nedefinováno|64bitová|64bitová|
|**_stati64**, **_wstati64**|Definovány|32bitová|64bitová|
|**_stat32i64** **_wstat32i64**|Definice makra nemá vliv na|32bitová|64bitová|
|**_stat64i32**, **_wstat64i32**|Definice makra nemá vliv na|64bitová|32bitová|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat**|**_stat**|**_stat**|**_wstat**|
|**_tstat64**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

Struktura **_stat** definovaná v sys\stat. H, obsahuje následující pole.

|Pole||
|-|-|
| **st_gid** | Číselný identifikátor skupiny, která soubor vlastní (specifické pro systém UNIX), toto pole bude v systémech Windows vždy nulové. Přesměrovaný soubor je klasifikován jako soubor systému Windows. |
| **st_atime** | Čas posledního přístupu k souboru. Platí pro systém souborů NTFS, ale nikoli na diskových jednotkách ve formátu FAT. |
| **st_ctime** | Čas vytvoření souboru. Platí pro systém souborů NTFS, ale nikoli na diskových jednotkách ve formátu FAT. |
| **st_dev** | Číslo jednotky disku obsahujícího soubor (stejné jako **st_rdev**). |
| **st_ino** | Číslo informačního uzlu **(inode)** pro soubor (specifický pro UNIX). V systémech souborů UNIX **inode** popisuje datum souboru a časová razítka, oprávnění a obsah. Pokud jsou soubory vzájemně pevně propojeny, sdílejí stejnou **inodu**. **Inode**, a proto **st_ino**, nemá žádný význam v systémech souborů FAT, HPFS nebo NTFS. |
| **st_mode** | Bitová maska pro informace o režimu souboru. **Bit _S_IFDIR** je nastaven, pokud *cesta* určuje adresář; **_S_IFREG** bit je nastaven, pokud *cesta* určuje běžný soubor nebo zařízení. Bity pro čtení a zápis uživatele jsou nastaveny podle režimu oprávnění souboru. bity spouštění uživatele jsou nastaveny podle přípony názvu souboru. |
| **st_mtime** | Čas poslední změny souboru. |
| **st_nlink** | Vždy 1 na souborových systémech, které nejsou ntfs. |
| **st_rdev** | Číslo jednotky disku obsahujícího soubor (stejné jako **st_dev**). |
| **st_size** | Velikost souboru v bajtů; 64bitové celé číslo pro varianty s příponou **i64.** |
| **st_uid** | Číselný identifikátor uživatele, který vlastní soubor (specifický pro unix). Toto pole bude v systémech Windows vždy nulové. Přesměrovaný soubor je klasifikován jako soubor systému Windows. |

Pokud *cesta* odkazuje na zařízení, **st_size**, různá časová pole, **st_dev**a **st_rdev** pole ve struktuře **_stat** jsou bezvýznamná. Protože STAT. H používá [typ _dev_t,](../../c-runtime-library/standard-types.md) který je definován v TYPES. H, musíte zahrnout TYPY. H před STAT. H ve vašem kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**_stat**, **_stat32 _stat64**, **_stati64** **_stat32i64**_stati64 **_stat64i32** **_stati64**|\<sys/types.h> \<následovaný sys/stat.h>|\<errno.h>|
|**_wstat**, **_wstat32**, **_wstat64**, **_wstati64 _wstat32i64**, **_wstat64i32** **_wstat64i32**|\<> sys/types.h \<následovaný sys/stat.h \<> nebo wchar.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_setmbcp](setmbcp.md)<br/>
