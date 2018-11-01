---
title: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32
ms.date: 11/04/2016
apiname:
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
ms.openlocfilehash: 316012479ec374cc5f40061384475008fe04e331
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637278"
---
# <a name="stat-stat32-stat64-stati64-stat32i64-stat64i32-wstat-wstat32-wstat64-wstati64-wstat32i64-wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

Umožňuje získáte informace o stavu souboru.

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
Ukazatel na řetězec obsahující cestu k existující soubor nebo adresář.

*Vyrovnávací paměti*<br/>
Ukazatel na strukturu, která ukládá výsledky.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud je získat informace o stavu souboru. Návratová hodnota-1 označuje chybu, v takovém případě **errno** je nastavena na **ENOENT**, která udává, že název souboru nebo cesta nebyla nalezena. Vrácená hodnota **EINVAL** určuje neplatný parametr; **errno** je také nastavena na **EINVAL** v tomto případě.

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o tomto a dalších návratových kódů.

Časové razítko souboru lze znázornit, pokud je novější než půlnoci 1. ledna 1970 a před 23:59:59, 31 prosince 3000 UTC, pokud nechcete použít **_stat32 –** nebo **_wstat32 –**, nebo jste definovali **_ USE_32BIT_TIME_T**, v takovém případě může být reprezentován datum pouze až do 23:59:59 18. ledna 2038 UTC.

## <a name="remarks"></a>Poznámky

**_Stat** funkce získává informace o souboru nebo adresáři určeném *cesta* a uloží jej do struktury, na které odkazuje *vyrovnávací paměti*. **_stat –** automaticky zpracovává argumenty vícebajtových řetězců znaků podle potřeby, rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky, která aktuálně používán.

**_wstat –** je verze širokého znaku **_stat**; *cesta* argument **_wstat –** je širokoznaký řetězec. **_wstat –** a **_stat** chovají stejně, s výjimkou, že **_wstat –** nezpracovává vícebajtové znakové řetězce.

Variace tyto funkce podporují typy času 32bitové nebo 64bitové a 32bitové nebo 64bitové souboru délky. První číselná přípona (**32** nebo **64**) označuje velikost času používá typ; druhý přípony je buď **i32** nebo **i64**, označující, zda velikost souboru je reprezentován jako 32bitový nebo 64bitové celé číslo.

**_stat –** je ekvivalentní **_stat64i32 –**, a **struktura** **_stat** obsahuje 64-bit čas. To platí Pokud **_USE_32BIT_TIME_T** je definován v takovém případě je v platnosti; staré chování **_stat** používá čas 32-bit, a **struktura** **_stat** obsahuje čas 32-bit. Totéž platí pro **_stati64**.

> [!NOTE]
> **_wstat –** nefunguje s Windows Vista symbolické odkazy. V těchto případech **_wstat –** bude vždy sestavy soubor o velikosti 0. **_stat –** správně funguje s symbolické odkazy.

Tato funkce ověřuje své parametry. Pokud *cesta* nebo *vyrovnávací paměti* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

### <a name="time-type-and-file-length-type-variations-of-stat"></a>Typ času a soubor délka typ Variant _stat –

|Funkce|_USE_32BIT_TIME_T definované?|Typ času|Délka typu souboru|
|---------------|------------------------------------|---------------|----------------------|
|**_stat –**, **_wstat –**|Nedefinovaná.|64bitových|32bitová|
|**_stat –**, **_wstat –**|Definice|32bitová|32bitová|
|**_stat32 –**, **_wstat32 –**|Není ovlivněna definici makra|32bitová|32bitová|
|**_stat64**, **_wstat64**|Není ovlivněna definici makra|64bitových|64bitových|
|**_stati64**, **_wstati64**|Nedefinovaná.|64bitových|64bitových|
|**_stati64**, **_wstati64**|Definice|32bitová|64bitových|
|**_stat32i64 –**, **_wstat32i64 –**|Není ovlivněna definici makra|32bitová|64bitových|
|**_stat64i32 –**, **_wstat64i32 –**|Není ovlivněna definici makra|64bitových|32bitová|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat –**|**_stat**|**_stat**|**_wstat**|
|**_tstat64 –**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64 –**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64 –**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32 –**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

**_Stat** struktury definované v SYS\STAT. H, obsahuje následující pole.

|Pole||
|-|-|
**st_gid**|Číselný identifikátor skupiny, která je vlastníkem souboru (specifické pro systém UNIX) Toto pole bude vždy nula v systémech Windows. Přesměrované soubor je klasifikován jako soubor Windows.
**st_atime**|Čas posledního přístupu k souboru. Diskové jednotky naformátované platné v systému souborů NTFS, ale ne v systému souborů FAT.
**st_ctime**|Čas vytvoření souboru. Diskové jednotky naformátované platné v systému souborů NTFS, ale ne v systému souborů FAT.
**st_dev**|Číslo disku obsahující soubor jednotky (stejné jako **st_rdev**).
**st_ino**|Počet uzlu informace ( **uzlů**) pro soubor (specifické pro systém UNIX). V systémech souborů UNIX **uzlů** popisuje data souborů a časová razítka, oprávnění a obsah. Pokud jsou soubory pevných – vzájemně propojený, sdílejí stejné **uzlů**. **Uzlů**a proto **st_ino**, nemá žádný význam v systémech souborů FAT, HPFS nebo systému souborů NTFS.
**st_mode –**|Bitová maska informace režim souboru. **_S_IFDIR** bit nastaven, pokud *cesta* Určuje adresář; **_S_IFREG** bit nastaven, pokud *cesta* Určuje běžný soubor nebo zařízení. Podle režimu oprávnění k souboru; jsou nastaveny bity pro čtení a zápis uživatele uživatel spustit bity jsou nastaveny podle příponu názvu souboru.
**st_mtime**|Čas poslední změny souboru.
**st_nlink**|Vždy 1 v systémech souborů než NTFS.
**st_rdev**|Číslo disku obsahující soubor jednotky (stejné jako **st_dev**).
**st_size**|Velikost souboru v bajtech; 64bitové celé číslo pro změny s **i64** příponu.
**st_uid**|Číselný identifikátor uživatele, který je vlastníkem souboru (specifické pro systém UNIX). Toto pole bude vždy nula v systémech Windows. Přesměrované soubor je klasifikován jako soubor Windows.

Pokud *cesta* odkazuje na zařízení, **st_size**, různá pole čas **st_dev**, a **st_rdev** pole **_stat –**  struktura nemají smysl. Protože STAT. H používá [_dev_t](../../c-runtime-library/standard-types.md) typ, který je definovaný v typy. H, musí obsahovat typy. H před STAT. H ve vašem kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná záhlaví|
|-------------|---------------------|----------------------|
|**_stat –**, **_stat32 –**, **_stat64**, **_stati64**, **_stat32i64 –**, **_stat64i32 –**|\<SYS/Types.h > za nímž následuje \<sys/stat.h >|\<errno.h>|
|**_wstat –**, **_wstat32 –**, **_wstat64**, **_wstati64**, **_wstat32i64 –**, **_wstat64i32 –**|\<SYS/Types.h > za nímž následuje \<sys/stat.h > nebo \<wchar.h >|\<errno.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
