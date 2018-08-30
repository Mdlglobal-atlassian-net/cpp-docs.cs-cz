---
title: asctime_s, _wasctime_s – – | Dokumentace Microsoftu
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
ms.openlocfilehash: 5b5414a59aac41bec29886b1aa83c20395b3e916
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208676"
---
# <a name="asctimes-wasctimes"></a>asctime_s, _wasctime_s

Převést **tm** čas struktury na řetězec znaků. Tyto funkce jsou verze [asctime, _wasctime – –](asctime-wasctime.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ukazatel na vyrovnávací paměť pro ukládání výsledek řetězce znaků. Tuto funkci předpokládá ukazatel na platný paměti umístění a velikost určeného *numberOfElements*.

*numberOfElements*<br/>
Velikost vyrovnávací paměti používané k ukládání výsledků.

*tmSource*<br/>
Struktura času a data. Tato funkce se předpokládá ukazatel na platný **struktura** **tm** objektu.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud dojde k selhání, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrácená hodnota je chybový kód. Kódy chyb jsou definovány v ERRNO. H. Další informace najdete v tématu [errno – konstanty](../../c-runtime-library/errno-constants.md). Skutečné chybové kódy pro všechny chybové stavy jsou uvedeny v následující tabulce.

### <a name="error-conditions"></a>Chybové podmínky

|*Vyrovnávací paměti*|*numberOfElements*|*tmSource*|Vrátí|Hodnota v *vyrovnávací paměti*|
|--------------|------------------------|----------|------------|-----------------------|
|**HODNOTU NULL**|Všechny|Všechny|**EINVAL**|Nezměněno|
|Není **NULL** (odkazuje na platný paměti)|0|Všechny|**EINVAL**|Nezměněno|
|Není **NULL**|0 < velikost < 26|Všechny|**EINVAL**|Prázdný řetězec|
|Není **NULL**|>= 26|**HODNOTU NULL**|**EINVAL**|Prázdný řetězec|
|Není **NULL**|>= 26|Neplatný čas struktury nebo je mimo rozsah hodnoty pro součásti času|**EINVAL**|Prázdný řetězec|

> [!NOTE]
> Chybové stavy pro **wasctime_s –** jsou podobné **asctime_s –** s tím rozdílem, že omezení velikosti se měří ve slovech.

## <a name="remarks"></a>Poznámky

**Asctime –** funkce převede čas uložené jako struktury na řetězec znaků. *TmSource* hodnota se obvykle získá z volání **gmtime** nebo **localtime**. Obě funkce je možné k vyplnění **tm** struktury, jak je definováno v čase. H.

|člen timeptr|Hodnota|
|--------------------|-----------|
|**tm_hour**|Hodiny od půlnoci (0-23)|
|**tm_isdst**|Kladná, pokud je v platnosti; letního času 0, pokud není platná; letního času záporná, pokud stav letní čas není znám. Knihovny run-time jazyka C předpokládá použita pravidla Spojených států pro implementaci výpočtu letního času (DST).|
|**tm_mday**|Den v měsíci (1-31)|
|**tm_min**|Minuty po hodině (0 – 59)|
|**tm_mon**|Měsíc (0 – 11; Leden = 0)|
|**tm_sec**|Sekundy po minutě (0 – 59)|
|**tm_wday**|Den v týdnu (0 – 6; Neděle = 0)|
|**tm_yday**|Den roku (0-365; 1. ledna = 0)|
|**tm_year**|Rok (aktuální rok minus 1900)|

Řetězec převedený znak je také upravena podle nastavení místní časové pásmo. Najdete v článku [čas, _time32 –, _time64](time-time32-time64.md), [_ftime _ftime32, _ftime64](ftime-ftime32-ftime64.md), a [localtime_s – _localtime32_s –, _localtime64_s –](localtime-s-localtime32-s-localtime64-s.md) funkce informace o konfiguraci místní čas a [_tzset –](tzset.md) funkce informace o definování prostředí časové pásmo a globální proměnné.

Řetězec výsledek produkovaný **asctime_s –** obsahuje přesně 26 znaků a má tvar `Wed Jan 02 02:03:55 1980\n\0`. Se používá 24hodinový formát. Všechna pole mají konstantní šířce. Znak nového řádku a znak null zabírat posledních dvou pozic řetězce. Hodnota předaná v jako druhý parametr by měl mít velké. Pokud je méně, kód chyby **EINVAL**, bude vrácen.

**_wasctime_s –** je verze širokého znaku **asctime_s –**. **_wasctime_s –** a **asctime_s –** se jinak chovají stejně.

### <a name="generic-text-routine-mapping"></a>Rutiny mapování obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s –**|**asctime_s**|**asctime_s**|**_wasctime_s**|

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky, takže odpadá nutnost určit velikost argumentu. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**asctime_s**|\<Time.h >|
|**_wasctime_s**|\<Time.h > nebo \<wchar.h >|

## <a name="security"></a>Zabezpečení

Pokud ukazatel vyrovnávací paměti není **NULL** a ukazatel neodkazuje na platnou vyrovnávací paměť, funkce přepíše cokoli, co je v umístění. Také to může vést k narušení přístupu.

A [přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns) může dojít, pokud je velikost předaného argumentu v větší než skutečná velikost vyrovnávací paměti.

## <a name="example"></a>Příklad

Tento program umístí systémový čas dlouhé celé číslo **aclock**, přeloží ho do struktury **newtime** a poté převádí řetězec formuláře pro výstup, pomocí **asctime_s –** funkce.

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

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
