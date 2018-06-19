---
title: _create_locale –, _wcreate_locale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9be41a2d156a522c74349c3457295502ae6d4f43
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451937"
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

Pokud je to platná *národního prostředí* a *kategorie* zadána, vrátí nastavení zadaný národní prostředí jako **_locale_t –** objektu. Aktuální nastavení národního prostředí programu, nebudou změněny.

## <a name="remarks"></a>Poznámky

**_Create_locale –** funkce vám umožní vytvořit objekt, který představuje určité oblasti specifické nastavení pro použití v konkrétní národní prostředí verze mnoho funkcí CRT (funguje s **_l** příponu ). Toto chování je podobné pro **setlocale**kromě toho, že místo použití nastavení zadaný národní prostředí v aktuálním prostředí, nastavení se ukládají v **_locale_t –** struktura, která je vrácena. **_Locale_t –** struktura by měl být uvolněno pomocí [_free_locale –](free-locale.md) Pokud se už nepotřebuje.

**_wcreate_locale** je verze široká charakterová **_create_locale –**; *národního prostředí* argument **_wcreate_locale** je široká charakterová řetězec. **_wcreate_locale** a **_create_locale –** chovat jinak shodně.

*Kategorie* argument určuje části chování specifická pro národní prostředí, které se vztahuje. Příznaky použité pro *kategorie* a součástí programu, které mají vliv na jsou uvedeny v následující tabulce.

|*kategorie* příznak|Ovlivňuje|
|-|-|
**LC_ALL –**|Všechny kategorie, jak je uvedeno dále.
**LC_COLLATE –**|**Strcoll –**, **_stricoll –**, **wcscoll –**, **_wcsicoll –**, **strxfrm –**, **_ strncoll –**, **_strnicoll –**, **_wcsncoll –**, **_wcsnicoll –**, a **wcsxfrm –** funkce.
**LC_CTYPE –**|Funkce znak zpracování (s výjimkou **IsDigit –**, **isxdigit –**, **mbstowcs –**, a **mbtowc –**, které jsou poškozena).
**LC_MONETARY –**|Informace o formátování měnovou vrácené **localeconv –** funkce.
**LC_NUMERIC –**|Desetinnou znak pro formátovaný výstup rutiny (například **printf**) pro převod dat rutiny a -peněžní formátování informace vrácené **localeconv –**. Kromě znak desetinné čárky **lc_numeric –** řetězec vrácený řízení oddělovače tisíců sady a seskupení [localeconv –](localeconv.md).
**LC_TIME –**|**STRFTIME –** a **wcsftime –** funkce.

Ověří, tato funkce *kategorie* a *národního prostředí* parametry. Pokud parametr kategorie není jedním z hodnoty uvedené v předchozí tabulce, nebo pokud *národního prostředí* je **NULL**, funkce vrátí hodnotu **NULL**.

*Národního prostředí* argument je ukazatel na řetězec, který určuje národní prostředí. Informace o formátu *národního prostředí* argument, najdete v části [názvy národních prostředí, jazyků a řetězce zemí/oblastí](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

*Národního prostředí* argument může trvat název národního prostředí, jazyk řetězec, řetězec jazyka a kód země nebo oblasti, znakové stránky, nebo řetězec jazyka, kód země nebo oblasti a znaková stránka. Sada názvy dostupné národních prostředí, jazyků, kódy zemí a znakové stránky obsahuje všechny, které podporuje rozhraní API systému Windows NLS kromě znakové stránky, které vyžadují více než dva bajty na znak – například ve formátu UTF-7 a UTF-8. Pokud zadáte znakové stránky, jako je UTF-7 nebo UTF-8, **_create_locale –** se nezdaří a vrátí **NULL**. Sada názvů národního prostředí podporuje **_create_locale –** jsou popsané v [názvy národních prostředí, jazyků a řetězce zemí/oblastí](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Sada jazyka a země nebo oblast řetězce nepodporuje **_create_locale –** jsou uvedeny v [řetězce jazyků](../../c-runtime-library/language-strings.md) a [řetězce zemí/oblastí](../../c-runtime-library/country-region-strings.md).

Další informace o nastavení národního prostředí naleznete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md).

Předchozí název této funkce **__create_locale –** (se dvěma úvodní podtržítka), se již nepoužívá.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_create_locale –**|\<Locale.h >|
|**_wcreate_locale**|\<Locale.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Názvy národních prostředí, jazyků a řetězce zemí/oblastí](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
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
