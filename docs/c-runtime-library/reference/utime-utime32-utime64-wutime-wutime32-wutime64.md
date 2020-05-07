---
title: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
ms.date: 4/2/2020
api_name:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
- _o__utime32
- _o__utime64
- _o__wutime32
- _o__wutime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
ms.openlocfilehash: dbff557cd116eb1df44f015b17716408c8dc54c2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912132"
---
# <a name="_utime-_utime32-_utime64-_wutime-_wutime32-_wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64

Nastavte čas změny souboru.

## <a name="syntax"></a>Syntaxe

```C
int _utime(
   const char *filename,
   struct _utimbuf *times
);
int _utime32(
   const char *filename,
   struct __utimbuf32 *times
);
int _utime64(
   const char *filename,
   struct __utimbuf64 *times
);
int _wutime(
   const wchar_t *filename,
   struct _utimbuf *times
);
int _wutime32(
   const wchar_t *filename,
   struct __utimbuf32 *times
);
int _wutime64(
   const wchar_t *filename,
   struct __utimbuf64 *times
);
```

### <a name="parameters"></a>Parametry

*Bitmap*<br/>
Ukazatel na řetězec, který obsahuje cestu nebo název souboru.

*časový*<br/>
Ukazatel na hodnoty uložených časových časů.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí hodnotu 0, pokud byl změněn čas úpravy souboru. Návratová hodnota-1 označuje chybu. Pokud je předán neplatný parametr, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce hodnotu-1 a **errno** se nastaví na jednu z následujících hodnot:

|hodnota errno|Podmínka|
|-|-|
| **EACCES** | Cesta Určuje soubor s adresářem nebo jen pro čtení. |
| **EINVAL** | Neplatný argument *časy* |
| **EMFILE** | Je otevřeno příliš mnoho souborů (soubor je třeba otevřít, aby se změnil čas změny). |
| **ENOENT** | Cesta nebo název souboru se nenašly. |

Další informace o těchto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

Datum může být změněno pro soubor, pokud je datum změny po půlnoci, 1. lednu 1970 a před koncovým datem používané funkce. **_utime** a **_wutime** používají hodnotu 64 času, takže koncové datum je 23:59:59, prosince 31, 3000, UTC. Pokud je definována **_USE_32BIT_TIME_T** pro vynucení starého chování, je koncové datum 23:59:59. ledna 2038, UTC. **_utime32** nebo **_wutime32** používá typ času 32 bez ohledu na to, zda je **_USE_32BIT_TIME_T** definován, a vždy má předchozí koncové datum. **_utime64** nebo **_wutime64** vždy používá typ času 64, takže tyto funkce vždy podporují pozdější koncové datum.

## <a name="remarks"></a>Poznámky

Funkce **_utime** nastavuje čas změny souboru určeného parametrem *filename*. Aby bylo možné změnit čas, proces musí mít k souboru přístup pro zápis. V operačním systému Windows můžete změnit dobu přístupu a dobu změny ve struktuře **_utimbuf** . Pokud *je časový ukazatel* s **hodnotou null** , je čas změny nastaven na aktuální místní čas. V opačném případě musí *časy* ukazovat na strukturu typu **_utimbuf**definovaná v SYS\UTIME.. Y.

Struktura **_utimbuf** ukládá přístup k souborům a časy úprav používané **_utime** ke změně dat úprav souborů. Struktura má následující pole, která jsou obě typu **time_t**:

| Pole |   |
|-------|---|
| **actime** | Čas přístupu k souboru |
| **modtime** | Čas úpravy souboru |

Konkrétní verze **_utimbuf** struktury (**_utimebuf32** a **__utimbuf64**) jsou definovány pomocí 32 a 64 verzí typu času. Ty se používají ve verzích této funkce 32 a 64, které se týkají bitů. **_utimbuf** sám ve výchozím nastavení používá typ času 64, pokud není definován **_USE_32BIT_TIME_T** .

**_utime** je stejný jako **_futime** s tím rozdílem, že argument *filename* **_utime** je název souboru nebo cesta k souboru, nikoli popisovač souboru otevřeného souboru.

**_wutime** je verze **_utime**s velkým znakem; Argument *filename* pro **_wutime** je řetězec s velkým znakem. Tyto funkce se chovají identicky jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadované hlavičky|Volitelné hlavičky|
|-------------|----------------------|----------------------|
|**_utime**, **_utime32** **_utime64**|\<sys/UTIME. h>|\<errno. h>|
|**_utime64**|\<sys/UTIME. h>|\<errno. h>|
|**_wutime**|\<UTIME. h> nebo \<WCHAR. h>|\<errno. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program používá **_utime** k nastavení času změny souboru na aktuální čas.

```C
// crt_utime.c
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/utime.h>
#include <time.h>

int main( void )
{
   struct tm tma = {0}, tmm = {0};
   struct _utimbuf ut;

   // Fill out the accessed time structure
   tma.tm_hour = 12;
   tma.tm_isdst = 0;
   tma.tm_mday = 15;
   tma.tm_min = 0;
   tma.tm_mon = 0;
   tma.tm_sec = 0;
   tma.tm_year = 103;

   // Fill out the modified time structure
   tmm.tm_hour = 12;
   tmm.tm_isdst = 0;
   tmm.tm_mday = 15;
   tmm.tm_min = 0;
   tmm.tm_mon = 0;
   tmm.tm_sec = 0;
   tmm.tm_year = 102;

   // Convert tm to time_t
   ut.actime = mktime(&tma);
   ut.modtime = mktime(&tmm);

   // Show file time before and after
   system( "dir crt_utime.c" );
   if( _utime( "crt_utime.c", &ut ) == -1 )
      perror( "_utime failed\n" );
   else
      printf( "File time modified\n" );
   system( "dir crt_utime.c" );
}
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/09/2003  05:38 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
File time modified
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/15/2002  12:00 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
```

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime, _futime32, _futime64](futime-futime32-futime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat, _wstat funkce](stat-functions.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
