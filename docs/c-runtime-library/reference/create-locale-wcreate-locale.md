---
title: _create_locale, _wcreate_locale
ms.date: 11/04/2016
apiname:
- _create_locale
- __create_locale
- _wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 0ede14d56dc093b83078bf28eb01f5b5c55d8949
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545922"
---
# <a name="createlocale-wcreatelocale"></a>_create_locale, _wcreate_locale

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
Kategorie.

*Národní prostředí*<br/>
Specifikátor národního prostředí

## <a name="return-value"></a>Návratová hodnota

Pokud platné *národní prostředí* a *kategorie* jsou uvedeny, vrátí zadané nastavení národního prostředí jako **_locale_t –** objektu. Aktuální nastavení národního prostředí programu se nezmění.

## <a name="remarks"></a>Poznámky

**_Create_locale** funkce vám umožní vytvořit objekt, který představuje určité specifické regionální nastavení pro použití ve verzích specifických pro národní prostředí mnoha funkcí CRT (funkce s **_l** příponu ). Chování je podobné **setlocale**, s tím rozdílem, že místo použití nastavení zadaného národního prostředí v aktuálním prostředí, nastavení se ukládají v **_locale_t –** struktura, která je vrácena. **_Locale_t –** struktury by měla být uvolněna pomocí [_free_locale –](free-locale.md) když je už nepotřebujete.

**_wcreate_locale** je verze širokého znaku **_create_locale**; *národní prostředí* argument **_wcreate_locale** je širokoznaký řetězec. **_wcreate_locale** a **_create_locale** se jinak chovají stejně.

*Kategorie* argument určuje části chování specifického pro národní prostředí, které tím ovlivníte. Příznaky použité pro *kategorie* a části programu, které ovlivňují, jak je znázorněno v následující tabulce jsou.

|*kategorie* příznak|Ovlivňuje|
|-|-|
**LC_ALL**|Všechny kategorie, jak je uvedeno níže.
**LC_COLLATE**|**Strcoll –**, **_stricoll –**, **wcscoll –**, **_wcsicoll –**, **strxfrm –**, **_ strncoll –**, **_strnicoll –**, **_wcsncoll –**, **_wcsnicoll –**, a **wcsxfrm –** funkce.
**LC_CTYPE**|Funkce zpracování znaků (s výjimkou **isdigit**, **isxdigit**, **mbstowcs**, a **mbtowc**, které nejsou ovlivněny).
**LC_MONETARY**|Informace o formátování měny vrácené **localeconv** funkce.
**LC_NUMERIC**|Znak pro rutiny formátovaného výstupu desetinné čárky (například **printf**), pro rutiny převodu dat a informace nefinančního formátování vrácené **localeconv**. Kromě znaku desetinné čárky **LC_NUMERIC** nastaví oddělovač tisíců a seskupení vrácený řetězec řídící [localeconv](localeconv.md).
**LC_TIME**|**Strftime** a **wcsftime** funkce.

Tato funkce ověřuje *kategorie* a *národní prostředí* parametry. Pokud parametr kategorie není jedna z hodnot uvedených v předchozí tabulce, nebo pokud *národní prostředí* je **NULL**, funkce vrátí **NULL**.

*Národní prostředí* argument je ukazatel na řetězec, který určuje národní prostředí. Informace o formátu *národní prostředí* argument, naleznete v tématu [názvy národních prostředí, jazyků a Country/Region Strings](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

*Národní prostředí* argument přijímá název národního prostředí, řetězec jazyka, řetězec jazyka a země nebo oblasti, znakovou stránku nebo řetězec jazyka, kód země/oblasti a znakovou stránku. Sada dostupných názvů národního prostředí, jazyků, kódů země/oblasti a znakových stránek obsahuje všechny, které jsou podporovány v rozhraní API Windows NLS kromě znakových stránek, které vyžadují více než dva bajty na znak, například UTF-7 a UTF-8. Pokud zadáte kódovou stránku jako UTF-7 nebo UTF-8, **_create_locale** selže a vrátí **NULL**. Sada názvů národních prostředí podporovaných **_create_locale** jsou popsány v [názvy národních prostředí, jazyků a Country/Region Strings](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Sada řetězců jazyka a země/oblast nepodporuje **_create_locale** jsou uvedeny v [Language Strings](../../c-runtime-library/language-strings.md) a [Country/Region Strings](../../c-runtime-library/country-region-strings.md).

Další informace o nastavení národního prostředí najdete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md).

Předchozí název této funkce **__create_locale –** (se dvěma vedoucími podtržítky), se už nepoužívá.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_create_locale**|\<Locale.h >|
|**_wcreate_locale**|\<Locale.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

[Názvy národních prostředí, jazyků a Country/Region Strings](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Řetězce jazyků](../../c-runtime-library/language-strings.md)<br/>
[Řetězce zemí/oblastí](../../c-runtime-library/country-region-strings.md)<br/>
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
