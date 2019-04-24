---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 11/04/2016
apiname:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
ms.openlocfilehash: d1858a36c68a2ca5cedf70a1d74d5f250cbac8df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288600"
---
# <a name="ctime-ctime32-ctime64-wctime-wctime32-wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

Převeďte hodnotu času na řetězec a proveďte úpravu pro nastavení místního časového pásma. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).

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
Ukazatel na uložený čas k převedení.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na výsledek řetězce znaků. **NULL** bude vrácen, pokud:

- *sourceTime* představuje datum před půlnocí, 1. ledna 1970, UTC.

- Pokud používáte **_ctime32 –** nebo **_wctime32 –** a *sourceTime* představuje datum po 23:59:59 18. ledna 2038 UTC.

- Pokud používáte **_ctime64** nebo **_wctime64** a *sourceTime* představuje datum po 23:59:59, 31 prosince 3000 UTC.

**CTime –** je vložená funkce, která je vyhodnocena na **_ctime64** a **time_t** je ekvivalentní **__time64_t –**. Pokud je nutné donutit kompilátor k interpretaci **time_t** jako staré 32bitové **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To způsobí, že to **ctime** vyhodnotilo **_ctime32 –**. Toto nastavení nedoporučujeme, protože může vaše aplikace selhat po 18. ledna 2038, a to není povoleno na 64bitových platformách.

## <a name="remarks"></a>Poznámky

**Ctime** funkce převede hodnotu času, který je uložen jako [time_t](../../c-runtime-library/standard-types.md) hodnotu na řetězec znaků. *SourceTime* hodnota se obvykle získá z volání [čas](time-time32-time64.md), který vrátí dobu v sekundách uplynulých od půlnoci (00: 00:00), 1. ledna 1970, koordinovaného univerzálního času (UTC). Řetězec návratová hodnota obsahuje přesně 26 znaků a má formát:

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Se používá 24hodinový formát. Všechna pole mají konstantní šířce. Znak nového řádku ('\n') a znak null ('\0') zabírají posledních dvou pozic řetězce.

Řetězec převedený znak je také upravena podle nastavení místní časové pásmo. Najdete v článku [čas](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md), a [localtime](localtime-localtime32-localtime64.md) funkce informace o konfiguraci místního času a [_tzset –](tzset.md) funkce pro Podrobnosti o definování prostředí časové pásmo a globální proměnné.

Volání **ctime** upraví jedné staticky přidělenou vyrovnávací paměti používané **gmtime** a **localtime** funkce. Každé volání některé z těchto rutin ničí výsledek předchozího volání. **CTime –** sdílí statické vyrovnávací paměť hodnotou **asctime –** funkce. Proto volání **ctime** zničí výsledky jakéhokoli předchozího volání **asctime –**, **localtime**, nebo **gmtime**.

**_wctime** a **_wctime64** jsou širokoznaké verze **ctime** a **_ctime64**; vrací ukazatel na řetězec širokých znaků. V opačném případě **_ctime64**, **_wctime**, a **_wctime64** chovají stejně jako **ctime**.

Tyto funkce ověřují své parametry. Pokud *sourceTime* je ukazatel s hodnotou null, nebo pokud *sourceTime* hodnota je negativní, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce **NULL** a nastavte **errno** k **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**CTime –**|**CTime –**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**CTime –**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<Time.h > nebo \<wchar.h >|
|**_wctime32**|\<Time.h > nebo \<wchar.h >|
|**_wctime64**|\<Time.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
