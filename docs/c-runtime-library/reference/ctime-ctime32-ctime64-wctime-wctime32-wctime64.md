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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 6056ad8bac6561c0ce2902928364996b2be9ae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348239"
---
# <a name="ctime-_ctime32-_ctime64-_wctime-_wctime32-_wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

Převeďte hodnotu času na řetězec a upravte nastavení místního časového pásma. K dispozici jsou bezpečnější verze těchto funkcí. viz [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).

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
Ukazatel na uložený čas převést.

## <a name="return-value"></a>Návratová hodnota

Ukazatel na výsledek řetězce znaku. **Null** bude vrácena, pokud:

- *sourceTime* představuje datum před půlnocí, 1 leden 1970, UTC.

- Pokud používáte **_ctime32** nebo **_wctime32** a *sourceTime* představuje datum po 23:59:59 Leden 18, 2038, UTC.

- Pokud používáte **_ctime64** nebo **_wctime64** a *sourceTime* představuje datum po 23:59:59, prosinec 31, 3000, UTC.

**ctime** je vřadná funkce, která je vyhodnocena jako **_ctime64** a **time_t** je ekvivalentní **__time64_t**. Pokud potřebujete vynutit, aby kompilátor interpretoval **time_t** jako starý 32bitový **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To **způsobí, že ctime** vyhodnotit **_ctime32**. To se nedoporučuje, protože vaše aplikace může selhat po 18 leden 2038 a není povoleno na 64bitové platformy.

## <a name="remarks"></a>Poznámky

Funkce **ctime** převede časovou hodnotu uloženou jako [hodnotu time_t](../../c-runtime-library/standard-types.md) na řetězec znaků. SourceTime hodnota je obvykle získána z volání [na čas](time-time32-time64.md), který vrátí počet sekund uplynulých od půlnoci (00:00:00), 1 leden 1970, koordinovaný univerzální čas (UTC). *sourceTime* Řetězec vrácené hodnoty obsahuje přesně 26 znaků a má formulář:

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Používá se 24hodinová hodina. Všechna pole mají konstantní šířku. Znak nového řádku (\n') a znak null (\0' zabírají poslední dvě pozice řetězce.

Řetězec převedených znaků je také upraven podle nastavení místního časového pásma. Informace o konfiguraci místního času a [funkce _tzset](tzset.md) naleznete v části [Time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)a [localtime,](localtime-localtime32-localtime64.md) kde najdete podrobnosti o definování prostředí časového pásma a globálních proměnných.

Volání **ctime** upravuje jednu staticky přidělenou vyrovnávací paměť používanou funkcemi **gmtime** a **localtime.** Každé volání jedné z těchto rutin zničí výsledek předchozího volání. **ctime** sdílí statickou vyrovnávací paměť s funkcí **asctime.** Volání **ctime** tedy zničí výsledky jakékoli předchozí výzvy **k asctime**, **localtime**nebo **gmtime**.

**_wctime** a **_wctime64** jsou širokoznaková verze **ctime** a **_ctime64**; vrací ukazatel na řetězec s širokým znakem. V opačném případě **se _ctime64**, **_wctime**a **_wctime64** chovají stejně jako **ctime**.

Tyto funkce ověřují jejich parametry. Pokud *sourceTime* je ukazatel null, nebo pokud *sourceTime* hodnota je záporná, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí **NULL** a nastavit **errno** **eINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**ctime**|**ctime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ctime**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<time.h> \<nebo wchar.h>|
|**_wctime32**|\<time.h> \<nebo wchar.h>|
|**_wctime64**|\<time.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
