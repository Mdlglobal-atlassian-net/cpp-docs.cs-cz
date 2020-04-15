---
title: _stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l
ms.date: 4/2/2020
api_name:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
- _o__mbsicoll
- _o__mbsicoll_l
- _o__stricoll
- _o__stricoll_l
- _o__wcsicoll
- _o__wcsicoll_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: d726d2d33f8f775d09e6197dfeda6abb91106a53
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355331"
---
# <a name="_stricoll-_wcsicoll-_mbsicoll-_stricoll_l-_wcsicoll_l-_mbsicoll_l"></a>_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l

Porovná řetězce pomocí informací specifických pro národní prostředí.

> [!IMPORTANT]
> **_mbsicoll** a **_mbsicoll_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězce ukončené hodnotou null k porovnání.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí hodnotu označující vztah *string1* k *string2*, takto.

|Návratová hodnota|Vztah string1 a string2|
|------------------|----------------------------------------|
|< 0|*string1* menší než *string2*|
|0|*string1* identické s *string2*|
|> 0|*string1* větší než *string2*|
|**_NLSCMPERROR**|Došlo k chybě.|

Každá z těchto funkcí vrátí **_NLSCMPERROR**. Chcete-li použít \< **_NLSCMPERROR**, zahrňte> řetězce m.h nebo \<> mbstring.h. **_wcsicoll** může selhat, pokud *string1* nebo *string2* obsahuje kódy širokých znaků mimo doménu pořadí řazení. Dojde-li k chybě, **může _wcsicoll** nastavit **errno** na **EINVAL**. Chcete-li zkontrolovat chybu při volání **_wcsicoll**, nastavte **errno** na 0 a **po** volání **_wcsicoll**chybovat.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí provádí porovnání bez rozlišování velkých a malých písmen *string1* a *string2* podle aktuálně používáné znakové stránky. Tyto funkce by měly být použity pouze v případě, že je rozdíl mezi pořadí znakové sady a lexikografické pořadí znaků v aktuální znakové stránce a tento rozdíl je zajímavé pro porovnání řetězců.

**_stricmp** se liší od **_stricoll** v tom, že **_stricmp** srovnání je ovlivněno **LC_CTYPE**, zatímco **_stricoll** srovnání je podle **LC_CTYPE** a **LC_COLLATE** kategorií národního prostředí. Další informace o **kategorii LC_COLLATE** naleznete v tématu [setlocale](setlocale-wsetlocale.md) a [Locale Categories](../../c-runtime-library/locale-categories.md). Verze těchto funkcí bez **_l** přípony používají aktuální národní prostředí; verze s **příponou _l** jsou identické s tím rozdílem, že místo toho používají národní prostředí předané. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Všechny tyto funkce ověřují jejich parametry. Pokud jsou ukazatele **NULL** *řetězcem 1* nebo *string2,* je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce vrátí **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicoll**|**_stricoll**|**_mbsicoll**|**_wcsicoll**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_stricoll**, **_stricoll_l**|\<string.h>|
|**_wcsicoll** **, _wcsicoll_l**|\<wchar.h>, \<string.h>|
|**_mbsicoll**, **_mbsicoll_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

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
