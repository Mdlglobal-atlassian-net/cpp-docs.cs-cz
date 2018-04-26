---
title: mktime – _mktime32 –, _mktime64 – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _mktime32
- mktime
- _mktime64
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
- mktime
- _mktime64
dev_langs:
- C++
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d7ead8ea50a617a5b0c67f4528b2138e9cd9e31e
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="mktime-mktime32-mktime64"></a>mktime, _mktime32, _mktime64

Převeďte místního času na hodnotu kalendáře.

## <a name="syntax"></a>Syntaxe

```C
time_t mktime(
   struct tm *timeptr
);
__time32_t _mktime32(
   struct tm *timeptr
);
__time64_t _mktime64(
   struct tm *timeptr
);
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Ukazatel na strukturu čas; v tématu [asctime –](asctime-wasctime.md).

## <a name="return-value"></a>Návratová hodnota

**_mktime32 –** vrátí čas zadaný kalendář kódovaná jako hodnota typu [time_t](../../c-runtime-library/standard-types.md). Pokud *timeptr* odkazuje na data před půlnoc, 1. ledna 1970, nebo pokud není možné vyjádřit čas kalendáře, **_mktime32 –** vrátí hodnotu -1 přetypovat na typ **time_t**. Při použití **_mktime32 –** a pokud *timeptr* odkazy a data po 23:59:59 18 leden 2038 koordinovaný světový čas (UTC), vrátí hodnotu -1 přetypovat na typ **time_t**.

**_mktime64 –** vrátí hodnotu -1 přetypovat na typ **__time64_t –** Pokud *timeptr* odkazuje na datum po 23:59:59, 31. prosince 3000, UTC.

## <a name="remarks"></a>Poznámky

**Mktime –**, **_mktime32 –** a **_mktime64 –** funkce převést (pravděpodobně neúplný) zadaný čas struktura na kterou odkazuje *timeptr*do plně definované struktury s normalized hodnoty a převede ji na **time_t** kalendář hodnota času. Převedený čas je stejné kódování jako hodnoty vrácené [čas](time-time32-time64.md) funkce. Původní hodnoty **tm_wday** a **tm_yday** součásti *timeptr* struktura jsou ignorovány a původní hodnoty ostatní součásti nejsou s omezeným přístupem na jejich normální oblasti.

**mktime –** je vložená funkce, která je ekvivalentní **_mktime64 –**, pokud **_USE_32BIT_TIME_T** je definována v takovém případě je ekvivalentní **_mktime32 –** .

Po úpravě na čas UTC **_mktime32 –** zpracovává data z půlnoc, 1. ledna 1970 na 23:59:59 18 leden 2038 UTC. **_mktime64 –** zpracovává data z půlnoc, 1. ledna 1970 do 23:59:59, 31. prosince 3000. Tato úprava může způsobit, že tyto funkce vrátí hodnotu -1 (přetypovat **time_t**, **__time32_t** nebo **__time64_t –**) i když zadáte datum v rozsahu. Například pokud jste Káhiře, země, která je dvě hodiny před časem UTC, dvě hodiny se nejprve bude odečítat od data, zadejte v *timeptr*; to může vložte data mimo rozsah.

Tyto funkce lze použít k ověření a vyplňte tm struktura. Pokud úspěšné, tyto funkce nastavit hodnoty **tm_wday** a **tm_yday** jako vhodné a nastavte další součásti, které představují čas zadaný kalendář, ale s jejich hodnoty vynutit na normální rozsahy. Konečná hodnota **tm_mday** není nastaven dokud **tm_mon** a **tm_year** určuje. Při zadávání **tm** struktury čas, nastavte **tm_isdst** pole na:

- Nula (0) k označení, že (běžný čas) je v platnosti.

- Hodnota, která je větší než 0 k označení, že letní čas je v platnosti.

- Hodnotu menší než nula tak, aby měl kód běhové knihovny jazyka C výpočetní, zda (běžný čas) nebo letní čas je v platnosti.

Běhové knihovny jazyka C určí chování letní čas úspory z [TZ](tzset.md) proměnné prostředí. Pokud **TZ** není nastavena, volání Win32 API [funkce GetTimeZoneInformation](http://msdn.microsoft.com/library/windows/desktop/ms724421.aspx) se použije k získání letní čas informace z operačního systému. Pokud se to nezdaří, knihovny předpokládá, že se používají pravidla Spojené státy k výpočtu letní čas. **tm_isdst** je povinné pole. Není-li nastavit, jeho hodnota není definován a návratovou hodnotou z těchto funkcí nepředvídatelné. Pokud *timeptr* odkazuje na **tm** struktura vrácené z předchozího volání [asctime –](asctime-wasctime.md), [gmtime –](gmtime-gmtime32-gmtime64.md), nebo [místní čas](localtime-localtime32-localtime64.md) (nebo variant tyto funkce), **tm_isdst** pole obsahuje správnou hodnotu.

Všimněte si, že **gmtime –** a **místní čas** (a **_gmtime32 –**, **_gmtime64 –**, **_localtime32 –**, a **_localtime64 –**) ke konverzi použijte jednu vyrovnávací paměť na vlákno. Pokud zadáte tento vyrovnávací paměť pro **mktime –**, **_mktime32 –** nebo **_mktime64 –**, jsou zničen předchozí obsah.

Tyto funkce ověřit jejich parametrů. Pokud *timeptr* je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, funkce vrátí hodnotu -1 a nastavte **errno** k **einval –**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mktime –**|\<Time.h >|
|**_mktime32**|\<Time.h >|
|**_mktime64**|\<Time.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_mktime.c
/* The example takes a number of days
* as input and returns the time, the current
* date, and the specified number of days.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm  when;
   __time64_t now, result;
   int        days;
   char       buff[80];

   time( &now );
   _localtime64_s( &when, &now );
   asctime_s( buff, sizeof(buff), &when );
   printf( "Current time is %s\n", buff );
   days = 20;
   when.tm_mday = when.tm_mday + days;
   if( (result = mktime( &when )) != (time_t)-1 ) {
      asctime_s( buff, sizeof(buff), &when );
      printf( "In %d days the time will be %s\n", days, buff );
   } else
      perror( "mktime failed" );
}
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Current time is Fri Apr 25 13:34:07 2003

In 20 days the time will be Thu May 15 13:34:07 2003
```

## <a name="see-also"></a>Viz také

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
