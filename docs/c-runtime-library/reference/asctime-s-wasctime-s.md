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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 282f4666734a4a8fd9c6825ee18265bd03fff65b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909411"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s, _wasctime_s

Převést časovou strukturu **správce** na řetězec znaků. Tyto funkce jsou verze [asctime, _wasctime](asctime-wasctime.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*vyrovnávací paměti*<br/>
Ukazatel na vyrovnávací paměť pro uložení výsledku řetězce znaků. Tato funkce předpokládá ukazatel na platné umístění v paměti, které má velikost určenou parametrem *numberOfElements*.

*numberOfElements*<br/>
Velikost vyrovnávací paměti použité k uložení výsledku.

*tmSource*<br/>
Struktura data a času. Tato funkce předpokládá ukazatel na platný objekt **struct** **TM** .

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud dojde k selhání, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, návratová hodnota je kód chyby. Kódy chyb jsou definovány v ERRNO. Y. Další informace naleznete v tématu [konstanty errno](../../c-runtime-library/errno-constants.md). V následující tabulce jsou uvedeny skutečné kódy chyb vracené pro jednotlivé chybové podmínky.

### <a name="error-conditions"></a>Chybové stavy

|*vyrovnávací paměti*|*numberOfElements*|*tmSource*|Vrátit|Hodnota v *bufferu*|
|--------------|------------------------|----------|------------|-----------------------|
|**PLATNOST**|Všechny|Všechny|**EINVAL**|Neupraveno|
|Není **null** (ukazuje na platnou paměť)|0|Všechny|**EINVAL**|Neupraveno|
|Není **null**|0< velikosti < 26|Všechny|**EINVAL**|Prázdný řetězec|
|Není **null**|>= 26|**PLATNOST**|**EINVAL**|Prázdný řetězec|
|Není **null**|>= 26|Neplatná časová struktura nebo hodnoty mimo rozsah pro součásti času|**EINVAL**|Prázdný řetězec|

> [!NOTE]
> Chybové stavy pro **wasctime_s** jsou podobné **asctime_s** s výjimkou, že omezení velikosti se měří v slovech.

## <a name="remarks"></a>Poznámky

Funkce **asctime** převede čas uložený jako strukturu na řetězec znaků. Hodnota *tmSource* je obvykle získána ze volání **gmtime** nebo **localtime**. Obě funkce lze použít k vyplnění struktury **TM** , jak je definováno v čase. Y.

|člen timeptr|Hodnota|
|--------------------|-----------|
|**tm_hour**|Hodiny od půlnoci (0-23)|
|**tm_isdst**|Kladné, pokud je v platnosti letní čas; 0, pokud letní čas neplatí; záporné, pokud stav letního času není známý. Knihovna run-time jazyka C předpokládá pravidla USA pro implementaci výpočtu letního času (DST).|
|**tm_mday**|Den v měsíci (1-31)|
|**tm_min**|Minuty po hodině (0-59)|
|**tm_mon**|Měsíc (0-11; Leden = 0)|
|**tm_sec**|Sekundy po minutě (0-59)|
|**tm_wday**|Den v týdnu (0-6; Neděle = 0)|
|**tm_yday**|Den v roce (0-365; 1. ledna = 0)|
|**tm_year**|Year (aktuální rok minus 1900)|

Převedený řetězec znaků je také upraven podle nastavení místního časového pásma. Informace o konfiguraci místního času a _ftime64 funkce najdete v tématu [_time32, _time64](time-time32-time64.md), [_ftime, _ftime32, localtime_s](ftime-ftime32-ftime64.md)a [_localtime32_s](localtime-s-localtime32-s-localtime64-s.md) _localtime64_s _tzsetch funkcí, které vám pomají informace o tom, jak nakonfigurovat místní čas a funkci [_tzset](tzset.md) pro informace o definování prostředí časového pásma a globálních proměnných.

Výsledek řetězce vytvořený **asctime_s** obsahuje přesně 26 znaků a má formu `Wed Jan 02 02:03:55 1980\n\0`. Použije se 24hodinový čas. Všechna pole mají konstantní šířku. Znak nového řádku a znak null zabírají poslední dvě pozice řetězce. Hodnota předaná jako druhý parametr by měla být nejméně ta velká. Pokud je menší, vrátí se chybový kód **EINVAL**.

**_wasctime_s** je verze **asctime_s**s velkým znakem. **_wasctime_s** a **asctime_s** se chovají identicky jinak.

Verze knihovny ladění těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFE. K zakázání tohoto chování použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapování rutiny obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky a eliminují nutnost zadat argument Size. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**asctime_s**|\<Time. h>|
|**_wasctime_s**|\<Time. h> nebo \<WCHAR. h>|

## <a name="security"></a>Zabezpečení

Pokud ukazatel vyrovnávací paměti není **null** a ukazatel neukazuje na platnou vyrovnávací paměť, funkce přepíše vše, co je v umístění. Následkem toho může dojít k narušení přístupu.

[Přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns) může nastat, pokud je předaný argument Size větší než skutečná velikost vyrovnávací paměti.

## <a name="example"></a>Příklad

Tento program umístí systémový čas do dlouhého celého čísla **ACLOCK**, převede ho do struktury **newtime** a pak ji převede na formát řetězce pro výstup pomocí funkce **asctime_s** .

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
