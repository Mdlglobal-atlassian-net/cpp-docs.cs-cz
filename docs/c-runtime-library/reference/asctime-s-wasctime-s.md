---
title: asctime_s –, _wasctime_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wasctime_s
- asctime_s
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
- asctime_s
- _wasctime_s
- _tasctime_s
dev_langs:
- C++
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4300d5fdab43cf4d22cf4e1fdee790f9d06d00d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403245"
---
# <a name="asctimes-wasctimes"></a>asctime_s, _wasctime_s

Převést **tm** čas struktura na řetězec znaků. Tyto funkce jsou verze [asctime –, _wasctime –](asctime-wasctime.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel na vyrovnávací paměť pro uložení výsledném řetězci znaků. Tato funkce se předpokládá ukazatel umístění platný paměti s velikostí určeného *numberOfElements*.

*numberOfElements*<br/>
Velikost vyrovnávací paměti používané k ukládání výsledků.

*tmSource*<br/>
Struktura času a data. Tato funkce se předpokládá ukazatel na platnou **struktura** **tm** objektu.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud dojde k selhání, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, je vrácenou hodnotu chybový kód. Kódy chyb jsou definovány v kód chyby. H. Další informace najdete v tématu [errno – konstanty](../../c-runtime-library/errno-constants.md). V následující tabulce jsou uvedeny skutečné chybové kódy, vrátí všechny chybové stavy.

### <a name="error-conditions"></a>Chybové stavy

|*Vyrovnávací paměti*|*numberOfElements*|*tmSource*|Vrátí|Hodnota v *vyrovnávací paměti*|
|--------------|------------------------|----------|------------|-----------------------|
|**HODNOTU NULL**|všechny|všechny|**EINVAL –**|nedojde ke změně|
|Není **NULL** (odkazuje na platný paměti)|0|všechny|**EINVAL –**|nedojde ke změně|
|není **hodnotu NULL.**|0 < velikost < 26|všechny|**EINVAL –**|prázdný řetězec.|
|není **hodnotu NULL.**|>= 26|**HODNOTU NULL**|**EINVAL –**|prázdný řetězec.|
|není **hodnotu NULL.**|>= 26|Neplatná doba struktura nebo mimo rozsah hodnoty pro součásti času|**EINVAL –**|prázdný řetězec.|

> [!NOTE]
> Chyba podmínky pro **wasctime_s –** jsou podobné **asctime_s –** s tím rozdílem, že omezení velikosti se měří v slova.

## <a name="remarks"></a>Poznámky

**Asctime –** funkce převede čas uložené jako struktura na řetězec znaků. *TmSource* hodnota se obvykle získávají z volání **gmtime –** nebo **místní čas**. Obě funkce lze použít k vyplnění **tm** struktury, jak jsou definovány v čase. H.

|člen timeptr|Hodnota|
|--------------------|-----------|
|**tm_hour**|Hodiny od půlnoci (0-23)|
|**tm_isdst**|Kladné, pokud letní čas je v platnosti; 0, pokud letní čas není platný; záporná, pokud má neznámý stav letní čas. Běhové knihovny jazyka C předpokládá Spojené státy pravidla pro implementaci výpočtu letní čas (DST).|
|**tm_mday**|Den v měsíci (1-31)|
|**tm_min**|Počet minut po hodině (0-59)|
|**tm_mon**|Měsíc (0-11; Ledna = 0)|
|**tm_sec**|Sekund za minutu (0-59)|
|**tm_wday**|Den v týdnu (0-6; Neděle = 0)|
|**tm_yday**|Den v roce (0-365; 1. ledna = 0)|
|**tm_year**|Rok (aktuálního roku minus 1900)|

Řetězec převedený znaků se také upraví podle nastavení zóny Místní čas. Najdete v článku [doba, _time32 –, _time64 –](time-time32-time64.md), [_ftime – _ftime32 –, _ftime64 –](ftime-ftime32-ftime64.md), a [localtime_s –, _localtime32_s –, _localtime64_s –](localtime-s-localtime32-s-localtime64-s.md) funkce informace o konfiguraci místní čas a [_tzset –](tzset.md) funkce informace o definování časové pásmo prostředí a globální proměnné.

Výsledek řetězec produkovaný **asctime_s –** obsahuje přesně 26 znaků a má tvar `Wed Jan 02 02:03:55 1980\n\0`. 24 hodin se používá. Všechna pole mít konstantní šířky. Znak nového řádku a znak hodnoty null zabírají posledních dvou pozic řetězce. Hodnota předaná jako druhý parametr by mělo obsahovat aspoň Tento velký. Pokud je menší, kód chyby, **einval –**, bude vrácen.

**_wasctime_s –** je verze široká charakterová **asctime_s –**. **_wasctime_s –** a **asctime_s –** chovat jinak shodně.

### <a name="generic-text-routine-mapping"></a>Rutiny mapování obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s –**|**asctime_s**|**asctime_s**|**_wasctime_s**|

V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení lze odvodit délka vyrovnávací paměti automaticky, takže není nutné zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**asctime_s**|\<Time.h >|
|**_wasctime_s**|\<Time.h > nebo \<wchar.h >|

## <a name="security"></a>Zabezpečení

Pokud je ukazatel vyrovnávací paměti není **NULL** a ukazatele neodkazuje na platný vyrovnávací paměť, funkce přepíše vše, co je v umístění. To může také způsobit porušení přístupu.

A [přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795) může dojít, když velikost argument předaná je větší než skutečná velikost vyrovnávací paměti.

## <a name="example"></a>Příklad

Tento program umístí systémového času v dlouhých celých čísel **aclock**, překládá do struktury **newtime** a převede jej na řetězec formulář pro výstup, pomocí **asctime_s –** funkce.

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

[Správa času](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
