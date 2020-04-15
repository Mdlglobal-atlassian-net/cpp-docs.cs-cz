---
title: asctime_s, _wasctime_s
ms.date: 4/2/2020
api_name:
- _wasctime_s
- asctime_s
- _o__wasctime_s
- _o_asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: 52391eb1237e4c1d7ef320dacd211b603a21ab8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334214"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s, _wasctime_s

Převeďte strukturu času **tm** na řetězec znaků. Tyto funkce jsou verze [asctime, _wasctime](asctime-wasctime.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t asctime_s(
   char* buffer,
   size_t numberOfElements,
   const struct tm *tmSource
);
errno_t _wasctime_s(
   wchar_t* buffer,
   size_t numberOfElements
   const struct tm *tmSource
);
template <size_t size>
errno_t asctime_s(
   char (&buffer)[size],
   const struct tm *tmSource
); // C++ only
template <size_t size>
errno_t _wasctime_s(
   wchar_t (&buffer)[size],
   const struct tm *tmSource
); // C++ only
```

### <a name="parameters"></a>Parametry

*Vyrovnávací paměti*<br/>
Ukazatel na vyrovnávací paměť pro uložení výsledku řetězce znaku. Tato funkce předpokládá ukazatel na platné umístění paměti s velikostí určenou *numberOfElements*.

*numberOfElements*<br/>
Velikost vyrovnávací paměti použité k uložení výsledku.

*tmZdroj*<br/>
Struktura času a data. Tato funkce předpokládá ukazatel na platný **objekt struct** **tm.**

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud dojde k chybě, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrácená hodnota je kód chyby. Kódy chyb jsou definovány v ERRNO. H. Další informace naleznete [v tématu errno Constants](../../c-runtime-library/errno-constants.md). Skutečné chybové kódy vrácené pro každý chybový stav jsou uvedeny v následující tabulce.

### <a name="error-conditions"></a>Chybové stavy

|*Vyrovnávací paměti*|*numberOfElements*|*tmZdroj*|Vrátit|Hodnota ve *vyrovnávací paměti*|
|--------------|------------------------|----------|------------|-----------------------|
|**Null**|Všechny|Všechny|**EINVAL**|Nezměněno|
|Není **null** (odkazuje na platnou paměť)|0|Všechny|**EINVAL**|Nezměněno|
|Není **null**|0< velikost <i 26|Všechny|**EINVAL**|Prázdný řetězec|
|Není **null**|>= 26|**Null**|**EINVAL**|Prázdný řetězec|
|Není **null**|>= 26|Neplatná časová struktura nebo hodnoty mimo rozsah pro součásti času|**EINVAL**|Prázdný řetězec|

> [!NOTE]
> Chybové podmínky pro **wasctime_s** jsou podobné **asctime_s** s výjimkou, že limit velikosti se měří slovy.

## <a name="remarks"></a>Poznámky

Funkce **asctime** převede čas uložený jako struktura na řetězec znaků. Hodnota *tmSource* je obvykle získána z volání **gmtime** nebo **localtime**. Obě funkce lze použít k vyplnění struktury **tm,** jak je definováno v TIME. H.

|člen timeptr|Hodnota|
|--------------------|-----------|
|**tm_hour**|Počet hodin od půlnoci (0-23)|
|**tm_isdst**|Pozitivní, pokud je v platnosti letní čas; 0, pokud letní čas není v platnosti; negativní, pokud není znám stav letního času. C run-time knihovna předpokládá pravidla Spojených států pro implementaci výpočtu letního času (DST).|
|**tm_mday**|Den v měsíci (1-31)|
|**tm_min**|Minuty po hodině (0-59)|
|**tm_mon**|Měsíc (0-11; Leden = 0)|
|**tm_sec**|Sekundpo minutě (0-59)|
|**tm_wday**|Den v týdnu (0-6; Neděle = 0)|
|**tm_yday**|Den v roce (0-365; 1. ledna = 0)|
|**tm_year**|Rok (aktuální rok minus 1900)|

Řetězec převedených znaků je také upraven podle nastavení místního časového pásma. Informace o [_tzset](tzset.md) definování prostředí časového pásma a globálních proměnných naleznete v _localtime32_s _localtime32_s a funkcích [čas, _time32, _time64](time-time32-time64.md) [, _ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)a [localtime_s](localtime-s-localtime32-s-localtime64-s.md) _localtime64_s.

Výsledek řetězce vytvořený **asctime_s** obsahuje přesně 26 `Wed Jan 02 02:03:55 1980\n\0`znaků a má tvar . Používá se 24hodinová hodina. Všechna pole mají konstantní šířku. Nový znak řádku a znak null zabírají poslední dvě pozice řetězce. Hodnota předaná jako druhý parametr by měla být alespoň tak velká. Pokud je menší, bude vrácen kód chyby **EINVAL**.

**_wasctime_s** je širokoznaková verze **asctime_s**. **_wasctime_s** a **asctime_s** se chovají stejně jinak.

Ladicí verze knihovny těchto funkcí nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapování rutiny obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky, což eliminuje potřebu zadat argument velikosti. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**asctime_s**|\<time.h>|
|**_wasctime_s**|\<time.h> \<nebo wchar.h>|

## <a name="security"></a>Zabezpečení

Pokud ukazatel vyrovnávací paměti není **NULL** a ukazatel neodkazuje na platnou vyrovnávací paměť, funkce přepíše vše, co je v umístění. To může také vést k narušení přístupu.

K [přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns) může dojít, pokud je předaný argument velikosti větší než skutečná velikost vyrovnávací paměti.

## <a name="example"></a>Příklad

Tento program umístí systémový čas do dlouhého **celého čísla aclock**, převede jej do struktury **newtime** a pak převede na řetězec formulář pro výstup, pomocí **asctime_s** funkce.

```C
// crt_asctime_s.c
#include <time.h>
#include <stdio.h>

struct tm newtime;
__time32_t aclock;

int main( void )
{
   char buffer[32];
   errno_t errNum;
   _time32( &aclock );   // Get time in seconds.
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.

   // Print local time as a string.

   errNum = asctime_s(buffer, 32, &newtime);
   if (errNum)
   {
       printf("Error code: %d", (int)errNum);
       return 1;
   }
   printf( "Current date and time: %s", buffer );
   return 0;
}
```

```Output
Current date and time: Wed May 14 15:30:17 2003
```

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
