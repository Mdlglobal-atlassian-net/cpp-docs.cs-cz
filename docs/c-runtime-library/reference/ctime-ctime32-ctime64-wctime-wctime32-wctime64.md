---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 4/2/2020
api_name:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
- _o__wctime32
- _o__wctime64
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
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
ms.openlocfilehash: 7dc87f417db93f8ad0d90de1270c19997669fb7c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914828"
---
# <a name="ctime-_ctime32-_ctime64-_wctime-_wctime32-_wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

Převést časovou hodnotu na řetězec a upravit pro nastavení místního časového pásma. K dispozici jsou bezpečnější verze těchto funkcí; viz [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *ctime( const time_t *sourceTime );
char *_ctime32( const __time32_t *sourceTime );
char *_ctime64( const __time64_t *sourceTime );
wchar_t *_wctime( const time_t *sourceTime );
wchar_t *_wctime32( const __time32_t *sourceTime );
wchar_t *_wctime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Ukazatel na uložený čas, který chcete převést.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na výsledek řetězce znaků. **Hodnota null** se vrátí, pokud:

- *sourceTime* představuje datum před půlnocí, 1. ledna 1970, UTC.

- Pokud používáte **_ctime32** nebo **_wctime32** a *sourceTime* představuje datum po 23:59:59. ledna 2038, UTC.

- Pokud použijete **_ctime64** nebo **_wctime64** a *sourceTime* představuje datum po 23:59:59. prosince 3000, standard UTC.

**CTime –** je vložená funkce, která je vyhodnocena jako **_ctime64** a **time_t** je ekvivalentní **__time64_t**. Pokud potřebujete vynutit, aby kompilátor interpretoval **time_t** jako starou **time_t**32, můžete definovat **_USE_32BIT_TIME_T**. To způsobí, že se **CTime –** vyhodnotí jako **_ctime32**. To se nedoporučuje, protože vaše aplikace může selhat i po 18. lednu 2038 a není povolená na 64 platformách.

## <a name="remarks"></a>Poznámky

Funkce **CTime –** převede hodnotu času uloženou jako hodnotu [time_t](../../c-runtime-library/standard-types.md) do řetězce znaků. Hodnota *sourceTime* se obvykle získává z volání do [doby](time-time32-time64.md), která vrací počet sekund uplynulý od půlnoci (00:00:00), 1. ledna 1970, KOORDINOVANÝ světový čas (UTC). Řetězec návratové hodnoty obsahuje přesně 26 znaků a má formu:

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Použije se 24hodinový čas. Všechna pole mají konstantní šířku. Znak nového řádku (' \n ') a znak null (' \ 0 ') zabírají poslední dvě pozice řetězce.

Převedený řetězec znaků je také upraven podle nastavení místního časového pásma. Podrobnosti o definování prostředí časového pásma a globálních proměnných najdete v tématu funkce [Time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)a [localtime](localtime-localtime32-localtime64.md) pro informace o konfiguraci místního času a funkci [_tzset](tzset.md) .

Volání **CTime –** upravuje jednu staticky přidělenou vyrovnávací paměť, kterou používají funkce **gmtime** a **localtime** . Každé volání jedné z těchto rutin zničí výsledek předchozího volání. **CTime –** sdílí statickou vyrovnávací paměť s funkcí **asctime** . Proto volání **CTime –** zničí výsledky jakéhokoliv předchozího volání **asctime**, **localtime**nebo **gmtime**.

**_wctime** a **_wctime64** jsou verze **CTime –** a **_ctime64**. vrací se ukazatel na řetězec s velkým znakem. V opačném případě **_ctime64**, **_wctime**a **_wctime64** se chovají stejně jako **CTime –**.

Tyto funkce ověřují své parametry. Pokud je *sourceTime* ukazatel s hodnotou null, nebo pokud je hodnota *sourceTime* záporná, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **hodnotu null** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**CTime –**|**CTime –**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**CTime –**|\<Time. h>|
|**_ctime32**|\<Time. h>|
|**_ctime64**|\<Time. h>|
|**_wctime**|\<Time. h> nebo \<WCHAR. h>|
|**_wctime32**|\<Time. h> nebo \<WCHAR. h>|
|**_wctime64**|\<Time. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_ctime64.c
// compile with: /W3
/* This program gets the current
* time in _time64_t form, then uses ctime to
* display the time in string form.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   __time64_t ltime;

   _time64( &ltime );
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996
   // Note: _ctime64 is deprecated; consider using _ctime64_s
}
```

```Output
The time is Wed Feb 13 16:04:43 2002
```

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
