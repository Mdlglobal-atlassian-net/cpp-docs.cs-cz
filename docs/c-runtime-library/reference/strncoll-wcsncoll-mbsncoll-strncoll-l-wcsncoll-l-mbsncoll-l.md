---
title: _strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l
ms.date: 4/2/2020
api_name:
- _strncoll
- _mbsncoll_l
- _wcsncoll
- _wcsncoll_l
- _mbsncoll
- _strncoll_l
- _o__mbsncoll
- _o__mbsncoll_l
- _o__strncoll
- _o__strncoll_l
- _o__wcsncoll
- _o__wcsncoll_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsncoll_l
- strncoll
- _wcsncoll
- _tcsnccoll
- _ftcsnccoll
- wcsncoll
- _mbsncoll
- wcsncoll_l
- strncoll_l
- _ftcsncoll
- _strncoll
- _tcsncoll
- mbsncoll
helpviewer_keywords:
- _strncoll_l function
- code pages, using for string comparisons
- _strncoll function
- _mbsncoll function
- ftcsncoll function
- strncoll function
- _ftcsncoll function
- strncoll_l function
- wcsncoll function
- mbsncoll function
- _tcsncoll function
- _tcsnccoll function
- wcsncoll_l function
- tcsnccoll function
- mbsncoll_l function
- _mbsncoll_l function
- tcsncoll function
- _wcsncoll function
- strings [C++], comparing by code page
- _ftcsnccoll function
- ftcsnccoll function
- _wcsncoll_l function
ms.assetid: e659a5a4-8afe-4033-8e72-17ffd4bdd8e9
ms.openlocfilehash: c7abe5ce96d0fa3d198834f6923724321d60d666
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919305"
---
# <a name="_strncoll-_wcsncoll-_mbsncoll-_strncoll_l-_wcsncoll_l-_mbsncoll_l"></a>_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l

Porovná řetězce s použitím informací specifických pro národní prostředí.

> [!IMPORTANT]
> **_mbsncoll** a **_mbsncoll_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _strncoll(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsncoll(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strncoll_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsncoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count,
   _locale_t locale
);
int _mbsncoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*řetězec1*, *řetězec2*<br/>
Řetězec zakončený hodnotou null k porovnání

*výpočtu*<br/>
Počet znaků, které mají být porovnány.

*locale*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací hodnotu, která označuje vztah dílčích řetězců *řetězec1* a *řetězec2*, následovně.

|Návratová hodnota|Vztah řetězec1 k řetězec2|
|------------------|----------------------------------------|
|< 0|*řetězec1* je menší než *řetězec2*.|
|0|*řetězec1* je totožný s *řetězec2*.|
|> 0|*řetězec1* je větší než *řetězec2*.|

Každá z těchto funkcí vrací **_NLSCMPERROR**. Chcete-li použít **_NLSCMPERROR**, zahrňte buď String. h nebo Mbstring. h. **_wcsncoll** může selhat, pokud buď *řetězec1* nebo *řetězec2* obsahuje kódy číselných znaků, které jsou mimo doménu pořadí řazení. Pokud dojde k chybě, **_wcsncoll** může nastavit **errno** na **EINVAL**. Chcete-li vyhledat chybu při volání **_wcsncoll**, nastavte **errno** na hodnotu 0 a po volání **_wcsncoll**zaškrtněte **errno** .

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí provádí porovnání s prvními *počty* znaků v *řetězec1* a *řetězec2*v závislosti na znakové stránce, která se právě používá. Tyto funkce použijte pouze v případě, že existuje rozdíl mezi pořadím znakových sad a pořadím znaků lexikografickým pořadím na znakové stránce a pokud je tento rozdíl pro porovnání řetězců důležité. Pořadí znakových sad je závislé na národním prostředí. Verze těchto funkcí, které nemají příponu **_l** používají aktuální národní prostředí, ale verze s příponou **_l** používají předaný národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Všechny tyto funkce ověřují své parametry. Pokud je buď *řetězec1* nebo *řetězec2* ukazatel s hodnotou null, nebo je *počet* větší než **INT_MAX**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccoll**|**_strncoll**|**_mbsncoll**|**_wcsncoll**|
|**_tcsncoll**|**_strncoll**|[_mbsnbcoll](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|**_wcsncoll**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strncoll** **_strncoll_l**|\<String. h>|
|**_wcsncoll** **_wcsncoll_l**|\<WCHAR. h> nebo \<String. h>|
|**_mbsncoll** **_mbsncoll_l**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Jazyka](../../c-runtime-library/locale.md)<br/>
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
