---
title: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
ms.date: 11/04/2016
apiname:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 8e52845a828e272ff3b8458b299c3757b8def748
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524628"
---
# <a name="utime-utime32-utime64-wutime-wutime32-wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64

Nastavte čas modifikace souboru.

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

*Název souboru*<br/>
Ukazatel na řetězec, který obsahuje cestu nebo název souboru.

*časy*<br/>
Ukazatel na uložený čas hodnoty.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí 0, pokud čas modifikace souboru byl změněn. Návratová hodnota-1 označuje chybu. Pokud je předán neplatný parametr, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a **errno** nastavena na jednu z následujících hodnot:

|Hodnota errno|Podmínka|
|-|-|
| **EACCES** | Cesta Určuje adresář nebo soubor určený jen pro čtení |
| **EINVAL** | Neplatný *časy* argument |
| **EMFILE** | Příliš mnoho otevřených souborů (Chcete-li změnit její čas změny musíte otevřít soubor.) |
| **ENOENT** | Cesta nebo název souboru nebyl nalezen |

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratových kódů.

Data lze změnit pro soubor, pokud je datum změny po půlnoci 1. ledna 1970 a před datem ukončení funkce používá. **_utime** a **_wutime** použít 64-bit časové hodnoty, takže koncové datum 23:59:59, 31 prosince 3000 UTC. Pokud **_USE_32BIT_TIME_T** je definována pro vynucení staré chování, je koncové datum 23:59:59 18. ledna 2038 UTC. **_utime32** nebo **_wutime32** použít typ 32-bit čas bez ohledu na to, zda **_USE_32BIT_TIME_T** je definována, a mít vždy starší koncové datum. **_utime64** nebo **_wutime64** vždy použít typ času 64-bit, tak tyto funkce vždy podporují novější datum ukončení.

## <a name="remarks"></a>Poznámky

**_Utime** funkce nastaví čas změny pro soubor určený parametrem *filename*. Proces musí mít oprávnění k zápisu do souboru, chcete-li změnit čas. V operačním systému Windows, můžete změnit čas přístupu a čas změny v **_utimbuf –** struktury. Pokud *časy* je **NULL** ukazatele, čas změny nastavena na aktuální místní čas. V opačném případě *časy* musí ukazovat na strukturu typu **_utimbuf –**, definované v SYS\UTIME. H.

**_Utimbuf –** struktura ukládá časy přístupu a úpravy souborů používá **_utime** ke změně datumů úpravy souboru. Struktura obsahuje následující pole, které jsou typu **time_t**:

| Pole |   |
|-------|---|
| **actime** | Čas přístup k souborům |
| **modtime** | Čas modifikace souboru |

Konkrétní verze **_utimbuf –** strukturu (**_utimebuf32** a **__utimbuf64 –**) jsou definovány pomocí 32bitové a 64bitové verze typu time. Ty se používají v 32bitové a 64bitové určité verze této funkce. **_utimbuf –** sama ve výchozím nastavení používá typu time 64-bit, není-li **_USE_32BIT_TIME_T** je definována.

**_utime** je stejný jako **_futime** s tím rozdílem, že *filename* argument **_utime** je název souboru nebo cesta k souboru, nikoli popisovač souboru z Otevřete soubor.

**_wutime** je verze širokého znaku **_utime**; *filename* argument **_wutime** je širokoznaký řetězec. Tyto funkce chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime –**|**_utime**|**_utime**|**_wutime**|
|**_tutime32 –**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64 –**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadované záhlaví|Volitelná záhlaví|
|-------------|----------------------|----------------------|
|**_utime**, **_utime32**, **_utime64**|\<SYS/utime.h >|\<errno.h>|
|**_utime64**|\<SYS/utime.h >|\<errno.h>|
|**_wutime**|\<utime.h > nebo \<wchar.h >|\<errno.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program využívá **_utime** nastavit čas modifikace souboru na aktuální čas.

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

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime, _futime32, _futime64](futime-futime32-futime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat, _wstat – funkce](stat-functions.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
