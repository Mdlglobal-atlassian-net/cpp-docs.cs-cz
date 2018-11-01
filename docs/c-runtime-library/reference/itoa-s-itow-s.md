---
title: _itoa_s – _itow_s – funkce
ms.date: 03/21/2018
apiname:
- _itoa_s
- _ltoa_s
- _ultoa_s
- _i64toa_s
- _ui64toa_s
- _itow_s
- _ltow_s
- _ultow_s
- _i64tow_s
- _ui64tow_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _itoa_s
- _ltoa_s
- _ultoa_s
- _i64toa_s
- _ui64toa_s
- _itow_s
- _ltow_s
- _ultow_s
- _i64tow_s
- _ui64tow_s
- _itot_s
- _ltot_s
- _ultot_s
- _i64tot_s
- _ui64tot_s
- itoa_s
- ltoa_s
- ultoa_s
- i64toa_s
- ui64toa_s
- itow_s
- ltow_s
- ultow_s
- i64tow_s
- ui64tow_s
- itot_s
- ltot_s
- ultot_s
- i64tot_s
- ui64tot_s
helpviewer_keywords:
- _ui64toa_s function
- _itow_s function
- _i64tow_s function
- _itot_s function
- converting integers
- itow_s function
- i64toa_s function
- _ui64tow_s function
- integers, converting
- _i64tot_s function
- itoa_s function
- _itoa_s function
- ui64toa_s function
- i64tow_s function
- converting numbers, to strings
- _ui64tot_s function
- _i64toa_s function
ms.assetid: eb746581-bff3-48b5-a973-bfc0a4478ecf
ms.openlocfilehash: 47eb030790359f25a7df5275a247c071fb3d599f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441702"
---
# <a name="itoas-ltoas-ultoas-i64toas-ui64toas-itows--ltows--ultows-i64tows-ui64tows"></a>_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s,  _ltow_s,  _ultow_s, _i64tow_s, _ui64tow_s

Převede celé číslo na řetězec. Jde o verzích [_itoa – _itow – funkce](itoa-itow.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _itoa_s( int value, char * buffer, size_t size, int radix );
errno_t _ltoa_s( long value, char * buffer, size_t size, int radix );
errno_t _ultoa_s( unsigned long value, char * buffer, size_t size, int radix );
errno_t _i64toa_s( long long value, char *buffer,
   size_t size, int radix );
errno_t _ui64toa_s( unsigned long long value, char *buffer,
   size_t size, int radix );

errno_t _itow_s( int value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ltow_s( long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ultow_s( unsigned long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _i64tow_s( long long value, wchar_t *buffer,
   size_t size, int radix );
errno_t _ui64tow_s( unsigned long long value, wchar_t *buffer,
   size_t size, int radix
);

// These template functions are C++ only:
template <size_t size>
errno_t _itoa_s( int value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _ltoa_s( long value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _ultoa_s( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
errno_t _itow_s( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
errno_t _ltow_s( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
errno_t _ultow_s( unsigned long value, wchar_t (&buffer)[size], int radix );
```

### <a name="parameters"></a>Parametry

*value*<br/>
Číslo, které má být převeden.

*Vyrovnávací paměti*<br/>
Výstupní vyrovnávací paměť, který obsahuje výsledek převodu.

*Velikost*<br/>
Velikost *vyrovnávací paměti* znaky nebo širokých znaků.

*radix*<br/>
Základ číselné soustavy nebo číselný základ pro převod *hodnota*, která musí být v rozsahu 2 až 36.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; Kód chyby při selhání. Pokud platí kterákoli z následujících podmínek, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

### <a name="error-conditions"></a>Chybové podmínky

|value|Vyrovnávací paměti|velikost|základ číselné soustavy|Vrátí|
|-----------|------------|----------------------|-----------|------------|
|Všechny|**HODNOTU NULL**|Všechny|Všechny|**EINVAL**|
|Všechny|Všechny|<=0|Všechny|**EINVAL**|
|Všechny|Všechny|< = delka výsledném řetězci vyžaduje|Všechny|**EINVAL**|
|Všechny|Všechny|Všechny|*základ číselné soustavy* < 2 nebo *základ číselné soustavy* > 36|**EINVAL**|

### <a name="security-issues"></a>Problémy se zabezpečením

Tyto funkce můžete vygenerovat narušení přístupu, pokud *vyrovnávací paměti* neodkazuje na platný paměti a není **NULL**, nebo pokud délka vyrovnávací paměti není dostatečně dlouhé pro uchování výsledného řetězce.

## <a name="remarks"></a>Poznámky

S výjimkou parametry a návratové hodnoty **_itoa_s –** a **_itow_s –** rodiny funkce mají stejné chování jako odpovídající méně bezpečné **_itoa –** a **_itow –** verze.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze knihovny z těchto funkcí nejprve naplní vyrovnávací paměť hodnotou 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

Knihovna CRT zahrnuje praktické makra definují velikost vyrovnávací paměti vyžadované k převodu nejdelší možnou hodnotu každého celočíselného typu, včetně ukončovacího znaku null a podepsat znak, pro několik běžných základních tříd. Informace najdete v tématu [maximální převodu počtu maker](itoa-itow.md#maximum-conversion-count-macros).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot_s –**|**_itoa_s**|**_itoa_s**|**_itow_s**|
|**_ltot_s**|**_ltoa_s**|**_ltoa_s**|**_ltow_s**|
|**_ultot_s**|**_ultoa_s**|**_ultoa_s**|**_ultow_s**|
|**_i64tot_s –**|**_i64toa_s**|**_i64toa_s**|**_i64tow_s**|
|**_ui64tot_s –**|**_ui64toa_s**|**_ui64toa_s**|**_ui64tow_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_itoa_s –**, **_ltoa_s –**, **_ultoa_s –**, **_i64toa_s –**, **_ui64toa_s –**|\<stdlib.h>|
|**_itow_s –**, **_ltow_s –**, **_ultow_s –**, **_i64tow_s –**, **_ui64tow_s –**|\<stdlib.h > nebo \<wchar.h >|

Tyto funkce jsou specifické pro společnost Microsoft. Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento příklad ukazuje použití některé z funkcí převodu celého čísla. Všimněte si, [_countof](countof-macro.md) – makro funguje jenom pro určení velikosti vyrovnávací paměti při deklaraci pole je viditelné kompilátoru a ne pro parametry, které mají zkažená na ukazatele.

```C
// crt_itoa_s.c
// Compile by using: cl /W4 crt_itoa_s.c
#include <stdlib.h>     // for _itoa_s functions, _countof, count macro
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen

int main( void )
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;
    for ( r = 10; r >= 2; --r )
    {
        _itoa_s( -1, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
    printf( "\n" );
    for ( r = 10; r >= 2; --r )
    {
        _i64toa_s( -1LL, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
    printf( "\n" );
    for ( r = 10; r >= 2; --r )
    {
        _ui64toa_s( 0xffffffffffffffffULL, buffer, _countof(buffer), r );
        printf( "base %d: %s (%d chars)\n",
            r, buffer, strnlen(buffer, _countof(buffer)) );
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[_itoa – _itow – funkce](itoa-itow.md)<br/>
