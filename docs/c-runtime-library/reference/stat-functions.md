---
title: _stat, _stat32 –, _stat64 –, _stati64 –, _stat32i64 –, _stat64i32 –, _wstat –, _wstat32 –, _wstat64 –, _wstati64 –, _wstat32i64 –, _wstat64i32 – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ce367bdee78be1610a36c887a04f2130375114
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="stat-stat32-stat64-stati64-stat32i64-stat64i32-wstat-wstat32-wstat64-wstati64-wstat32i64-wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

Získáte informace o stavu pro určitý soubor.

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

Každá z těchto funkcí vrátí 0, pokud je získat informace o stavu souboru. Návratovou hodnotu-1 označuje chybu, v takovém případě **errno** je nastaven na **enoent –**, která určuje, zda název souboru nebo cesta nebyla nalezena. Vrácená hodnota **einval –** označuje neplatný parametr; **errno** je také nastavena na **einval –** v tomto případě.

V tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o tomto a dalších návratové kódy.

Razítka data na soubor může být reprezentován, pokud je novější než půlnoc, 1. ledna 1970 a před 23:59:59, 31. prosince 3000, UTC, pokud nechcete použít **_stat32 –** nebo **_wstat32 –**, nebo definovali **_ USE_32BIT_TIME_T**, v takovém případě může být reprezentován datum pouze do 23:59:59 18 leden 2038 UTC.

## <a name="remarks"></a>Poznámky

**_Stat –** funkce získává informace o soubor nebo adresář zadaný *cesta* a uloží je ve struktuře, na kterou odkazuje *vyrovnávací paměti*. **_stat –** automaticky zpracovává argumenty řetězce vícebajtových znaků podle potřeby, rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky aktuálně používán.

**_wstat –** je verze široká charakterová **_stat –**; *cesta* argument **_wstat –** je široká charakterová řetězec. **_wstat –** a **_stat –** vyjma toho, že se chovají stejně jako **_wstat –** nezpracovává řetězců vícebajtových znaků.

Variace tyto funkce podporují typy čas 32 nebo 64bitová verze a 32 nebo 64bitový soubor délky. První číselná přípona (**32** nebo **64**) označuje velikost času typu používaného; druhý přípona buď **i32** nebo **i64**, označující, zda velikost souboru je reprezentována jako 32bitové nebo 64bitové celé číslo.

**_stat –** je ekvivalentní **_stat64i32 –**, a **struktura** **_stat –** obsahuje 64-bit čas. Toto je hodnota true, pokud **_USE_32BIT_TIME_T** je definována v takovém případě staré chování je v platnosti; **_stat –** používá 32bitové čas a **struktura** **_stat –** obsahuje 32-bit čas. Totéž platí pro **_stati64 –**.

> [!NOTE]
> **_wstat –** nefunguje s Windows Vista symbolické odkazy. V těchto případech **_wstat –** bude vždy sestavy soubor o velikosti 0. **_stat –** fungovat správně s symbolické odkazy.

Tato funkce ověří jeho parametry. Pokud má jedna *cesta* nebo *vyrovnávací paměti* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

### <a name="time-type-and-file-length-type-variations-of-stat"></a>Typ času a soubor délka typu Variant _stat –

|Funkce|_USE_32BIT_TIME_T definované?|Typ času|Typ délku souboru|
|---------------|------------------------------------|---------------|----------------------|
|**_stat –**, **_wstat –**|Nejsou definována.|64bitových|32bitová|
|**_stat –**, **_wstat –**|Definované|32bitová|32bitová|
|**_stat32 –**, **_wstat32 –**|Není vliv na definici – makro|32bitová|32bitová|
|**_stat64 –**, **_wstat64 –**|Není vliv na definici – makro|64bitových|64bitových|
|**_stati64 –**, **_wstati64 –**|Nejsou definována.|64bitových|64bitových|
|**_stati64 –**, **_wstati64 –**|Definované|32bitová|64bitových|
|**_stat32i64 –**, **_wstat32i64 –**|Není vliv na definici – makro|32bitová|64bitových|
|**_stat64i32 –**, **_wstat64i32 –**|Není vliv na definici – makro|64bitových|32bitová|

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat –**|**_stat**|**_stat**|**_wstat**|
|**_tstat64 –**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64 –**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64 –**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32 –**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

**_Stat –** struktuře, které jsou definované v SYS\STAT. H, zahrnuje následující pole.

|Pole||
|-|-|
**st_gid**|Identifikační číslo skupiny, který vlastní soubor (specifických pro systém UNIX) Toto pole bude vždy nula v systémech Windows. Přesměrovaného soubor je klasifikován jako soubor systému Windows.
**st_atime**|Čas posledního přístupu k souboru. Diskové jednotky naformátované platné v systému souborů NTFS, ale ne v systému souborů FAT.
**st_ctime**|Čas vytvoření souboru. Diskové jednotky naformátované platné v systému souborů NTFS, ale ne v systému souborů FAT.
**st_dev**|Číslo disku obsahující soubor jednotky (stejné jako **st_rdev**).
**st_ino**|Počet uzlu informace ( **uzlů inode**) pro soubor (specifických pro systém UNIX). V systémech UNIX souborů **uzlů inode** popisuje datum souboru a časová razítka, oprávnění a obsahu. Pokud jsou soubory pevný odkaz na sebe navzájem, sdílejí stejné **uzlů inode**. **Uzlů inode**a proto **st_ino**, nemá žádný význam v systému souborů FAT, HPFS nebo systému souborů NTFS.
**st_mode –**|Bitová maska režim souboru informace. **_S_ifdir –** Pokud je nastaven bit *cesta* Určuje adresář; **_s_ifreg –** Pokud je nastaven bit *cesta* určuje obyčejnou soubor nebo zařízení. Služba bits pro čtení a zápis uživatele jsou nastavena podle režimu oprávnění souboru; uživatel provést bits jsou nastaveny podle příponu názvu souboru.
**st_mtime**|Čas poslední změny souboru.
**st_nlink**|Vždy 1 v systémech souborů s jiným systémem souborů NTFS.
**st_rdev**|Číslo disku obsahující soubor jednotky (stejné jako **st_dev**).
**st_size**|Velikost souboru v bajtech; 64bitové celé číslo pro změny s **i64** příponu.
**st_uid**|Identifikační číslo uživatele, který vlastní soubor (specifických pro systém UNIX). Toto pole bude vždy nula v systémech Windows. Přesměrovaného soubor je klasifikován jako soubor systému Windows.

Pokud *cesta* odkazuje na zařízení, **st_size**, různá pole čas **st_dev**, a **st_rdev** polí v **_stat –**  struktura nemají smysl. Protože STAT. H používá [_dev_t –](../../c-runtime-library/standard-types.md) typ, který je definován typy. H, musí obsahovat typy. H před STAT. H ve vašem kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné hlavičky|
|-------------|---------------------|----------------------|
|**_stat –**, **_stat32 –**, **_stat64 –**, **_stati64 –**, **_stat32i64 –**, **_stat64i32 –**|\<SYS/Types.h > následuje \<sys/stat.h >|\<errno.h>|
|**_wstat –**, **_wstat32 –**, **_wstat64 –**, **_wstati64 –**, **_wstat32i64 –**, **_wstat64i32 –**|\<SYS/Types.h > následuje \<sys/stat.h > nebo \<wchar.h >|\<errno.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
