---
title: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
ms.date: 11/04/2016
apiname:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
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
ms.openlocfilehash: 0410aeda4bbec33738d01a9514181c19f351e2c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288358"
---
# <a name="ctimes-ctime32s-ctime64s-wctimes-wctime32s-wctime64s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

Převeďte hodnotu času na řetězec a proveďte úpravu pro nastavení místního časového pásma. Jde o verzích [ctime _ctime64, _wctime, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Musí být dostatečně velký pro uložení 26 znaků. Ukazatel na výsledek řetězce znaků, nebo **NULL** pokud:

- *sourceTime* představuje datum před půlnocí, 1. ledna 1970, UTC.

- Pokud používáte **_ctime32_s** nebo **_wctime32_s** a *sourceTime* představuje datum po 23:59:59 18. ledna 2038 UTC.

- Pokud používáte **_ctime64_s** nebo **_wctime64_s** a *sourceTime* představuje datum po 23:59:59, 31 prosince 3000 UTC.

- Pokud používáte **_ctime_s** nebo **_wctime_s**, tyto funkce jsou obálky pro předchozí funkce. V části poznámky.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

*sourceTime*<br/>
Ukazatel na uložený čas.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu. Pokud dojde k selhání z důvodu neplatného parametru, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí se kód chyby. Kódy chyb jsou definovány v ERRNO. H. seznam těchto chyb, naleznete v tématu [errno](../../c-runtime-library/errno-constants.md). V následující tabulce jsou uvedeny kódy Skutečná chyba vyvolána všechny chybové stavy.

## <a name="error-conditions"></a>Chybové podmínky

|*Vyrovnávací paměti*|*numberOfElements*|*sourceTime*|Vrátí|Hodnota v *vyrovnávací paměti*|
|--------------|------------------------|------------|------------|-----------------------|
|**NULL**|Všechny|Všechny|**EINVAL**|Nezměněno|
|Není **NULL** (odkazuje na platný paměti)|0|Všechny|**EINVAL**|Nezměněno|
|Není **NULL**|0 < velikost < 26|Všechny|**EINVAL**|Prázdný řetězec|
|Není **NULL**|>= 26|NULL|**EINVAL**|Prázdný řetězec|
|Není **NULL**|>= 26|< 0|**EINVAL**|Prázdný řetězec|

## <a name="remarks"></a>Poznámky

**Ctime_s** funkce převede hodnotu času, který je uložen jako [time_t](../../c-runtime-library/standard-types.md) struktury na znakové řetězce. *SourceTime* hodnota se obvykle získá z volání [čas](time-time32-time64.md), který vrátí dobu v sekundách uplynulých od půlnoci (00: 00:00), 1. ledna 1970, koordinovaného univerzálního času (UTC). Řetězec návratová hodnota obsahuje přesně 26 znaků a má formát:

`Wed Jan 02 02:03:55 1980\n\0`

Se používá 24hodinový formát. Všechna pole mají konstantní šířce. Znak nového řádku ('\n') a znak null ('\0') zabírají posledních dvou pozic řetězce.

Řetězec převedený znak je také upravena podle nastavení místní časové pásmo. Zobrazit [čas](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md), a [localtime32_s –](localtime-s-localtime32-s-localtime64-s.md) funkce informace o konfiguraci místního času a [_tzset –](tzset.md) funkce pro informace o definování prostředí časové pásmo a globální proměnné.

**_wctime32_s** a **_wctime64_s** jsou širokoznaké verze **_ctime32_s** a **_ctime64_s**; vrací ukazatel na řetězec širokých znaků. V opačném případě **_ctime64_s**, **_wctime32_s**, a **_wctime64_s** chovají stejně jako **_ctime32_s**.

**ctime_s** je vložená funkce, který se vyhodnotí **_ctime64_s** a **time_t** je ekvivalentní **__time64_t –**. Pokud je nutné donutit kompilátor k interpretaci **time_t** jako staré 32bitové **time_t**, můžete definovat **_USE_32BIT_TIME_T**. To způsobí, že to **ctime_s** vyhodnotilo **_ctime32_s**. Toto nastavení nedoporučujeme, protože může vaše aplikace selhat po 18. ledna 2038, a to není povoleno na 64bitových platformách.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky, takže odpadá nutnost určit velikost argumentu. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**ctime_s**, **_ctime32_s**, **_ctime64_s**|\<time.h>|
|**_wctime_s**, **_wctime32_s**, **_wctime64_s**|\<Time.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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
