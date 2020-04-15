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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 5c530f46877bdb23fc51fb49beab8abfc0c16b2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361204"
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

*Název_souboru*<br/>
Ukazatel na řetězec, který obsahuje cestu nebo název souboru.

*Krát*<br/>
Ukazatel na uložené hodnoty času.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud byl změněn čas změny souboru. Vrácená hodnota -1 označuje chybu. Pokud je předán neplatný parametr, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí -1 a **errno** je nastavena na jednu z následujících hodnot:

|hodnota errno|Podmínka|
|-|-|
| **ACCACCES** | Cesta určuje adresář nebo soubor jen pro čtení. |
| **EINVAL** | Argument *Neplatných časů* |
| **SOUBOR EM** | Příliš mnoho otevřených souborů (soubor musí být otevřen, aby se změnil čas změny) |
| **ENOENT** | Cesta nebo název souboru nebyl nalezen. |

Další informace o těchto a dalších návratových kódech naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

Datum lze změnit pro soubor, pokud je datum změny po půlnoci, 1. **_utime** a **_wutime** použít 64bitovou časovou hodnotu, takže koncové datum je 23:59:59, 31. Pokud **_USE_32BIT_TIME_T** je definován a vynutit staré chování, koncové datum je 23:59:59 leden 18, 2038, UTC. **_utime32** nebo **_wutime32** používat 32bitový časový typ bez ohledu na to, zda je **definován_USE_32BIT_TIME_T** a vždy mají dřívější koncové datum. **_utime64** nebo **_wutime64** vždy používat 64bitový časový typ, takže tyto funkce vždy podporují pozdější koncové datum.

## <a name="remarks"></a>Poznámky

Funkce **_utime** nastaví čas změny souboru *určeného názvem souboru*. Proces musí mít přístup pro zápis do souboru, aby se změnil čas. V operačním systému Windows můžete změnit dobu přístupu a čas změny ve **struktuře _utimbuf.** Pokud *časy* je **ukazatel NULL,** čas změny je nastavena na aktuální místní čas. V opačném případě musí *časy* ukazovat na strukturu typu **_utimbuf**definované v sys\UTIME. H.

Struktura **_utimbuf** ukládá časy přístupu k souborům a úpravy používané **_utime** ke změně dat úprav souborů. Struktura má následující pole, která jsou typu **time_t**:

| Pole |   |
|-------|---|
| **actime** | Čas přístupu k souboru |
| **modtime** | Čas změny souboru |

Specifické verze **_utimbuf** struktury (**_utimebuf32** a **__utimbuf64**) jsou definovány pomocí 32bitových a 64bitových verzí časového typu. Ty se používají v 32bitové a 64bitové specifické verzi této funkce. **_utimbuf** sám ve výchozím nastavení používá 64bitový časový typ, pokud není definován **_USE_32BIT_TIME_T.**

**_utime** je shodný s **_futime** s tím rozdílem, že argument *názvu souboru* **_utime** je název souboru nebo cesta k souboru, nikoli popisovač souboru otevřeného souboru.

**_wutime** je širokoznaková verze **_utime**; argument *název souboru,* který **má _wutime,** je řetězec s širokým znakem. Tyto funkce se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>Požadavky

|Rutina|Povinná záhlaví|Volitelná záhlaví|
|-------------|----------------------|----------------------|
|**_utime** **_utime32** **_utime64**|\<sys/utime.h>|\<errno.h>|
|**_utime64**|\<sys/utime.h>|\<errno.h>|
|**_wutime**|\<utime.h> \<nebo wchar.h>|\<errno.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
