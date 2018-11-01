---
title: _stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l
ms.date: 11/04/2016
apiname:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- stricoll
- _stricoll
- _wcsicoll
- mbsicoll_l
- _mbsicoll
- _ftcsicoll
- wcsicoll_l
- _tcsicoll
- mbsicoll
- stricoll_l
helpviewer_keywords:
- code pages, using for string comparisons
- _ftcsicoll function
- _mbsicoll_l function
- _mbsicoll function
- mbsicoll function
- stricoll function
- tcsicoll function
- string comparison [C++], culture-specific
- _tcsicoll function
- _stricoll function
- _stricoll_l function
- _wcsicoll function
- mbsicoll_l function
- stricoll_l function
- strings [C++], comparing by code page
- ftcsicoll function
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
ms.openlocfilehash: bd2406751fd2855afd02743c98938e530398e7d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579666"
---
# <a name="stricoll-wcsicoll-mbsicoll-stricolll-wcsicolll-mbsicolll"></a>_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l

Porovná řetězce pomocí informací specifických pro národní prostředí.

> [!IMPORTANT]
> **_mbsicoll –** a **_mbsicoll_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _stricoll(
   const char *string1,
   const char *string2
);
int _wcsicoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*řetězec1*, *řetězec2*<br/>
Řetězec zakončený hodnotou Null pro srovnání.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací hodnotu určující vztah *řetězec1* k *řetězec2*, následujícím způsobem.

|Návratová hodnota|Vztah řetězec1 k řetězec2|
|------------------|----------------------------------------|
|< 0|*řetězec1* menší než *řetězec2*|
|0|*řetězec1* shodné s *řetězec2*|
|> 0|*řetězec1* větší než *řetězec2*|
|**_NLSCMPERROR**|Došlo k chybě.|

Každá z těchto funkcí vrací **_NLSCMPERROR**. Chcete-li použít **_NLSCMPERROR**, zahrňte \<string.h > nebo \<mbstring.h >. **_wcsicoll –** může selhat, pokud buď *řetězec1* nebo *řetězec2* obsahuje kódy širokého znaku mimo doménu pořadí řazení. Pokud dojde k chybě, **_wcsicoll –** může nastavit **errno** k **EINVAL**. Chcete-li zkontrolovat chyby volání **_wcsicoll –**, nastavte **errno** na hodnotu 0 a zkontrolujte **errno** po volání **_wcsicoll –**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí provádí porovnávání bez *řetězec1* a *řetězec2* podle kódové stránky, aktuálně používán. Tyto funkce by měla sloužit pouze v případě, že existuje rozdíl mezi znakové sady a lexikografickým pořadím znaků v aktuální znakové stránce a tento rozdíl je relevantní pro porovnání řetězců.

**_stricmp –** se liší od **_stricoll –** v tom, že **_stricmp –** porovnání je ovlivňován **LC_CTYPE**, že **_stricoll –** je podle porovnání **LC_CTYPE** a **LC_COLLATE** kategorie národního prostředí. Další informace o **LC_COLLATE** kategorie, naleznete v tématu [setlocale](setlocale-wsetlocale.md) a [kategorie národního prostředí](../../c-runtime-library/locale-categories.md). Verze těchto funkcí bez **_l** přípony použití aktuálního národního prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají předané národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Všechny tyto funkce ověřují své parametry. Pokud *řetězec1* nebo *řetězec2* jsou **NULL** vyvolána ukazatele, obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **_NLSCMPERROR** a nastavte **errno** k **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicoll –**|**_stricoll**|**_mbsicoll –**|**_wcsicoll**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_stricoll –**, **_stricoll_l –**|\<String.h >|
|**_wcsicoll –**, **_wcsicoll_l**|\<wchar.h >, \<string.h >|
|**_mbsicoll –**, **_mbsicoll_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
