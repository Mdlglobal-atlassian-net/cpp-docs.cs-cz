---
title: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
ms.date: 11/04/2016
api_name:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
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
ms.openlocfilehash: a6329319be5d002c8f0a35ceb0258cb9081923f7
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624414"
---
# <a name="ctime_s-_ctime32_s-_ctime64_s-_wctime_s-_wctime32_s-_wctime64_s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

Převést časovou hodnotu na řetězec a upravit pro nastavení místního časového pásma. Jedná se o verze [CTime –, _ctime64, _wctime, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*vyrovnávací paměti*<br/>
Musí být dostatečně velký, aby obsahovalo 26 znaků. Ukazatel na výsledek řetězce znaků, nebo **hodnota null** , pokud:

- *sourceTime* představuje datum před půlnocí, 1. ledna 1970, UTC.

- Pokud používáte **_ctime32_s** nebo **_wctime32_s** a *sourceTime* představuje datum 23:59:59 od 18. ledna 2038, UTC.

- Pokud použijete **_ctime64_s** nebo **_wctime64_s** a *sourceTime* představuje datum po 23:59:59. prosince 3000, standard UTC.

- Pokud používáte **_ctime_s** nebo **_wctime_s**, jsou tyto funkce obálky pro předchozí funkce. Viz část poznámky.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

*sourceTime*<br/>
Ukazatel na uložený čas.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud dojde k chybě z důvodu neplatného parametru, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí se kód chyby. Kódy chyb jsou definovány v ERRNO. Y Seznam těchto chyb naleznete v tématu [errno](../../c-runtime-library/errno-constants.md). Skutečné chybové kódy vyvolané pro jednotlivé chybové podmínky jsou uvedeny v následující tabulce.

## <a name="error-conditions"></a>Chybové stavy

|*vyrovnávací paměti*|*numberOfElements*|*sourceTime*|Vrátit|Hodnota v *bufferu*|
|--------------|------------------------|------------|------------|-----------------------|
|**PLATNOST**|Jakýmikoli|Jakýmikoli|**EINVAL**|Neupraveno|
|Není **null** (ukazuje na platnou paměť)|0,8|Jakýmikoli|**EINVAL**|Neupraveno|
|není **null**|0 < velikosti < 26|Jakýmikoli|**EINVAL**|Prázdný řetězec|
|není **null**|> = 26|NULL|**EINVAL**|Prázdný řetězec|
|není **null**|> = 26|< 0|**EINVAL**|Prázdný řetězec|

## <a name="remarks"></a>Poznámky

Funkce **ctime_s** převede hodnotu času uloženou jako strukturu [time_t](../../c-runtime-library/standard-types.md) na řetězec znaků. Hodnota *sourceTime* se obvykle získává z volání do [doby](time-time32-time64.md), která vrací počet sekund uplynulý od půlnoci (00:00:00), 1. ledna 1970, KOORDINOVANÝ světový čas (UTC). Řetězec návratové hodnoty obsahuje přesně 26 znaků a má formu:

`Wed Jan 02 02:03:55 1980\n\0`

Použije se 24hodinový čas. Všechna pole mají konstantní šířku. Znak nového řádku (' \n ') a znak null (' \ 0 ') zabírají poslední dvě pozice řetězce.

Převedený řetězec znaků je také upraven podle nastavení místního časového pásma. Informace o tom, jak definovat prostředí časového pásma a globální proměnné, najdete v tématu funkce [Time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)a [localtime32_s](localtime-s-localtime32-s-localtime64-s.md) pro informace o konfiguraci místního času a funkci [_tzset](tzset.md) .

**_wctime32_s** a **_wctime64_s** jsou verze s velkým znakem **_ctime32_s** a **_ctime64_s**; vrací se ukazatel na řetězec s velkým znakem. Jinak se **_ctime64_s**, **_wctime32_s**a **_wctime64_s** chovají stejně jako **_ctime32_s**.

**ctime_s** je vložená funkce, která se vyhodnotí jako **_ctime64_s** a **time_t** je ekvivalentem **__time64_t**. Pokud potřebujete vynutit, aby kompilátor interpretoval **time_t** jako starou 32 **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To způsobí, že se **ctime_s** vyhodnotí jako **_ctime32_s**. To se nedoporučuje, protože vaše aplikace může selhat i po 18. lednu 2038 a není povolená na 64 platformách.

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky a eliminují nutnost zadat argument Size. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Verze knihovny ladění těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFE. Pokud chcete toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ctime_s**, **_ctime32_s**, **_ctime64_s**|\<time. h >|
|**_wctime_s**, **_wctime32_s**, **_wctime64_s**|\<Time. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
