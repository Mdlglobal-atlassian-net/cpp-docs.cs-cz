---
title: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
ms.date: 4/2/2020
api_name:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
- _o__ctime32_s
- _o__ctime64_s
- _o__wctime32_s
- _o__wctime64_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
ms.openlocfilehash: d5121c795ed27c22d20087868f798a4b7f5f5b02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348170"
---
# <a name="ctime_s-_ctime32_s-_ctime64_s-_wctime_s-_wctime32_s-_wctime64_s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

Převeďte hodnotu času na řetězec a upravte nastavení místního časového pásma. Jedná se o verze [ctime, _ctime64, _wctime, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) s vylepšeními zabezpečení, jak je popsáno v [části Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t ctime_s(
   char* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _ctime32_s(
   char* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _ctime64_s(
   char* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime )
;
errno_t _wctime_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _wctime32_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _wctime64_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime
);
```

```cpp
template <size_t size>
errno_t _ctime32_s(
   char (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _ctime64_s(
   char (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime32_s(
   wchar_t (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime64_s(
   wchar_t (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Musí být dostatečně velký, aby pojmout 26 znaků. Ukazatel na výsledek řetězce znaku nebo **NULL,** pokud:

- *sourceTime* představuje datum před půlnocí, 1 leden 1970, UTC.

- Pokud používáte **_ctime32_s** nebo **_wctime32_s** a *sourceTime* představuje datum po 23:59:59 Leden 18, 2038, UTC.

- Pokud používáte **_ctime64_s** nebo **_wctime64_s** a *sourceTime* představuje datum po 23:59:59, Prosinec 31, 3000, UTC.

- Pokud používáte **_ctime_s** nebo **_wctime_s**, jsou tyto funkce obálkami předchozích funkcí. Viz část Poznámky.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

*sourceTime*<br/>
Ukazatel na uložený čas.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud došlo k chybě z důvodu neplatného parametru, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, je vrácen kód chyby. Kódy chyb jsou definovány v ERRNO. H; Seznam těchto chyb naleznete v [tématu errno](../../c-runtime-library/errno-constants.md). Skutečné chybové kódy vyháněné pro každý chybový stav jsou uvedeny v následující tabulce.

## <a name="error-conditions"></a>Chybové stavy

|*Vyrovnávací paměti*|*numberOfElements*|*sourceTime*|Vrátit|Hodnota ve *vyrovnávací paměti*|
|--------------|------------------------|------------|------------|-----------------------|
|**Null**|jakékoli|jakékoli|**EINVAL**|Nezměněno|
|Není **null** (odkazuje na platnou paměť)|0|jakékoli|**EINVAL**|Nezměněno|
|Není **null**|0< velikost <i 26|jakékoli|**EINVAL**|Prázdný řetězec|
|Není **null**|>= 26|NULL|**EINVAL**|Prázdný řetězec|
|Není **null**|>= 26|< 0|**EINVAL**|Prázdný řetězec|

## <a name="remarks"></a>Poznámky

Funkce **ctime_s** převede časovou hodnotu uloženou jako [time_t](../../c-runtime-library/standard-types.md) strukturu na řetězec znaků. SourceTime hodnota je obvykle získána z volání [na čas](time-time32-time64.md), který vrátí počet sekund uplynulých od půlnoci (00:00:00), 1 leden 1970, koordinovaný univerzální čas (UTC). *sourceTime* Řetězec vrácené hodnoty obsahuje přesně 26 znaků a má formulář:

`Wed Jan 02 02:03:55 1980\n\0`

Používá se 24hodinová hodina. Všechna pole mají konstantní šířku. Nový znak řádku (\n') a znak null (\0' zabírají poslední dvě pozice řetězce.

Řetězec převedených znaků je také upraven podle nastavení místního časového pásma. Informace [_tzset](tzset.md) o definování prostředí časového pásma a globálních proměnných naleznete v funkcích [time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)a [localtime32_s.](localtime-s-localtime32-s-localtime64-s.md)

**_wctime32_s** a **_wctime64_s** jsou širokoúhlá verze **_ctime32_s** a **_ctime64_s**; vrací ukazatel na řetězec s širokým znakem. V opačném případě **se _ctime64_s**, **_wctime32_s**a **_wctime64_s** chovají stejně jako **_ctime32_s**.

**ctime_s** je vsazená funkce, která je vyhodnocena jako **_ctime64_s** a **time_t** je ekvivalentní **__time64_t**. Pokud potřebujete vynutit, aby kompilátor interpretoval **time_t** jako starý 32bitový **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To **způsobí,** že ctime_s vyhodnotit na **_ctime32_s**. To se nedoporučuje, protože vaše aplikace může selhat po 18 leden 2038 a není povoleno na 64bitové platformy.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky, což eliminuje potřebu zadat argument velikosti. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze knihovny těchto funkcí nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ctime_s**, **_ctime32_s**, **_ctime64_s**|\<time.h>|
|**_wctime_s** **_wctime32_s** **_wctime64_s**|\<time.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_wctime_s.c
// This program gets the current
// time in time_t form and then uses _wctime_s to
// display the time in string form.

#include <time.h>
#include <stdio.h>

#define SIZE 26

int main( void )
{
   time_t ltime;
   wchar_t buf[SIZE];
   errno_t err;

   time( &ltime );

   err = _wctime_s( buf, SIZE, &ltime );
   if (err != 0)
   {
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);
   }
   wprintf_s( L"The time is %s\n", buf );
}
```

```Output
The time is Fri Apr 25 13:03:39 2003
```

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
