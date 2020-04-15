---
title: strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l
ms.date: 4/2/2020
api_name:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
- _o__mbscoll
- _o__mbscoll_l
- _o__strcoll_l
- _o__wcscoll_l
- _o_strcoll
- _o_wcscoll
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
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
helpviewer_keywords:
- code pages, using for string comparisons
- mbscoll function
- wcscoll_l function
- ftcscoll function
- wcscoll function
- _strcoll_l function
- tcscoll function
- _ftcscoll function
- _tcscoll function
- _wcscoll_l function
- _mbscoll function
- strcoll_l function
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
ms.openlocfilehash: 9cbf24fafa78ac6a53a99abf0d1bb1ab3a0625c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358116"
---
# <a name="strcoll-wcscoll-_mbscoll-_strcoll_l-_wcscoll_l-_mbscoll_l"></a>strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l

Porovná řetězce pomocí aktuálního národního prostředí nebo zadané kategorie LC_COLLATE stavu převodu.

> [!IMPORTANT]
> **_mbscoll** a **_mbscoll_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int strcoll(
   const char *string1,
   const char *string2
);
int wcscoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _strcoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int wcscoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbscoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*řetězec1*, *řetězec2*<br/>
Řetězce ukončené hodnotou null k porovnání.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí hodnotu označující vztah *string1* k *string2*, takto.

|Návratová hodnota|Vztah string1 a string2|
|------------------|----------------------------------------|
|< 0|*string1* menší než *string2*|
|0|*string1* identické s *string2*|
|> 0|*string1* větší než *string2*|

Každá z těchto funkcí vrátí **_NLSCMPERROR** na chybu. Chcete-li použít **_NLSCMPERROR**, uveďte buď STRING. H nebo MBSTRING. H. **wcscoll** může selhat, pokud je *buď string1* nebo *string2* **NULL** nebo obsahuje kódy širokých znaků mimo doménu pořadí řazení. Když dojde k chybě, **wcscoll** může nastavit **errno** na **EINVAL**. Chcete-li zkontrolovat chybu při volání **wcscoll**, nastavte **errno** na 0 a poté zkontrolujte **errno** po volání **wcscoll**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí provádí porovnání rozlišování malých a velkých písmen *řetězce1* a *string2* podle aktuálně používáné znakové stránky. Tyto funkce by měly být použity pouze v případě, že je rozdíl mezi pořadí znakové sady a lexikografické pořadí znaků v aktuální znakové stránce a tento rozdíl je zajímavé pro porovnání řetězců.

Všechny tyto funkce ověřují jejich parametry. Pokud *buď string1* nebo *string2* je ukazatel null, nebo pokud *počet* je větší než **INT_MAX**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, tyto funkce vrátí **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

Porovnání těchto dvou řetězců je operace závislá na národním prostředí, protože každé národní prostředí má různá pravidla pro řazení znaků. Verze těchto funkcí bez **přípony _l** pro toto chování závislé na národním prostředí používají národní prostředí aktuálního vlákna. verze s **příponou _l** jsou shodné s odpovídající funkcí bez přípony s tím rozdílem, že používají národní prostředí předané jako parametr namísto aktuálního národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscoll**|**strcoll řekl:**|**_mbscoll**|**wcscoll řekl:**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strcoll řekl:**|\<string.h>|
|**wcscoll řekl:**|\<wchar.h>, \<string.h>|
|**_mbscoll**, **_mbscoll_l**|\<mbstring.h>|
|**_strcoll_l**|\<string.h>|
|**_wcscoll_l**|\<wchar.h>, \<string.h>|

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
