---
title: _create_locale, _wcreate_locale
ms.date: 11/04/2016
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: a7098dc572ecdbefd891efc8443e977b01850fa4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938853"
---
# <a name="_create_locale-_wcreate_locale"></a>_create_locale, _wcreate_locale

Vytvoří objekt národního prostředí.

## <a name="syntax"></a>Syntaxe

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parametry

*Kategorie*<br/>
Kategorií.

*jazyka*<br/>
Specifikátor národního prostředí

## <a name="return-value"></a>Návratová hodnota

Pokud je zadáno platné *národní prostředí* a *kategorie* , vrátí zadané nastavení národního prostředí jako objekt **_locale_t** . Aktuální nastavení národního prostředí programu se nezmění.

## <a name="remarks"></a>Poznámky

Funkce **_create_locale** umožňuje vytvořit objekt, který představuje určitá nastavení konkrétní oblasti pro použití ve verzích různých funkcí CRT specifických pro národní prostředí (funkce s příponou **_l** ). Chování je podobné jako **setlocale**, s tím rozdílem, že místo použití zadaného nastavení národního prostředí pro aktuální prostředí je nastavení uloženo ve **_locale_t** struktuře, která je vrácena. Struktura **_locale_t** by měla být uvolněna pomocí [_free_locale](free-locale.md) , pokud již není potřebná.

**_wcreate_locale** je **_create_locale**verze s velkým znakem; Argument *locale* pro **_wcreate_locale** je řetězec s velkým znakem. **_wcreate_locale** a **_create_locale** se chovají stejně jinak.

Argument *Category* určuje části chování specifického pro národní prostředí, které jsou ovlivněny. Příznaky používané pro *kategorii* a části programu, které ovlivňují, jsou uvedené v této tabulce:

| příznak *kategorie* | Ovlivňuje |
|-----------------|---------|
| **LC_ALL** |Všechny kategorie, jak je uvedeno níže. |
| **LC_COLLATE** |Funkce **strcoll –** , **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**a **Wcsxfrm** . |
| **LC_CTYPE** | Funkce pro zpracování znaků (s výjimkou **číslic**, **isxdigit**, **mbstowcs**a **mbtowc**, které nejsou ovlivněny). |
| **LC_MONETARY** | Informace o formátování měny vrácené funkcí **localeconv** . |
| **LC_NUMERIC** | Znak desetinné čárky pro naformátované výstupní rutiny (například **printf**) pro rutiny převodu dat a pro nepeněžní informace o formátování vrácené funkcí **localeconv**. Kromě znaku desetinné čárky **LC_NUMERIC** nastaví oddělovač tisíců a řídicí řetězec seskupení vrácený [localeconv](localeconv.md). |
| **LC_TIME** | Funkce **strftime** a **wcsftime** . |

Tato funkce ověří parametry *kategorie* a *národního prostředí* . Pokud parametr Category není jedna z hodnot uvedených v předchozí tabulce nebo pokud má *národní prostředí* **hodnotu null**, vrátí funkce **hodnotu null**.

Argument *locale* je ukazatel na řetězec, který určuje národní prostředí. Informace o formátu argumentu *národního prostředí* najdete v tématu [názvy národních prostředí, jazyky a řetězce země/oblasti](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

Argument *locale* může mít název národního prostředí, řetězec jazyka, řetězec jazyka a kód země nebo oblasti, znakovou stránku nebo řetězec jazyka, kód země/oblasti a znakovou stránku. Sada dostupných názvů národního prostředí, jazyků, kódů zemí a oblastí a znakových stránek obsahuje všechny, které jsou podporovány rozhraním API systému Windows NLS s výjimkou znakových stránek, které vyžadují více než dva bajty na znak, například UTF-7 a UTF-8. Pokud zadáte znakovou stránku jako UTF-7 nebo UTF-8, **_create_locale** se nezdaří a vrátí **hodnotu null**. Sada názvů národních prostředí podporovaných nástrojem **_create_locale** je popsána v tématu [názvy národních prostředí, jazyky a řetězce země/oblasti](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Sada řetězců jazyka a země/oblasti, kterou podporuje **_create_locale** , jsou uvedeny v části [jazyky](../../c-runtime-library/language-strings.md) řetězce a [země/oblasti](../../c-runtime-library/country-region-strings.md).

Další informace o nastavení národního prostředí naleznete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Předchozí název této funkce, **__create_locale** (se dvěma předními podtržítky), byl zastaralý.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_create_locale**|\<locale. h >|
|**_wcreate_locale**|\<locale. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>Viz také:

[Názvy národních prostředí, jazyky a řetězce země/oblasti](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Řetězce jazyků](../../c-runtime-library/language-strings.md)<br/>
[Řetězce země/oblasti](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
