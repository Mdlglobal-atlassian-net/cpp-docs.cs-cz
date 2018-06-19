---
title: _strnicoll –, _wcsnicoll –, _mbsnicoll –, _strnicoll_l –, _wcsnicoll_l –, _mbsnicoll_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnicoll_l
- _mbsnicoll
- _wcsnicoll_l
- _strnicoll
- _strnicoll_l
- _wcsnicoll
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
- wcshicoll_l
- _ftcsncicoll
- strnicoll_l
- _wcsnicoll
- mbsnicoll_l
- _strnicoll
- mbsnicoll
- _ftcsnicoll
- wcsnicoll
- _tcsnicoll
- _mbsnicoll
- strinicoll
- _tcsncicoll
dev_langs:
- C++
helpviewer_keywords:
- code pages, using for string comparisons
- ftcsncicoll function
- mbsnicoll_l function
- _ftcsnicoll function
- mbsnicoll function
- _tcsnicoll function
- _wcsnicoll_l function
- _mbsnicoll function
- tcsncicoll function
- strnicoll function
- _ftcsncicoll function
- wcsnicoll_l function
- _mbsnicoll_l function
- _tcsncicoll function
- strnicoll_l function
- wcsnicoll function
- _strnicoll_l function
- _wcsnicoll function
- ftcsnicoll function
- strings [C++], comparing by code page
- tcsnicoll function
- _strnicoll function
ms.assetid: abf0c569-725b-428d-9ff2-924f430104b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f8592f40dda312f138351526509b69eadf9647c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32416524"
---
# <a name="strnicoll-wcsnicoll-mbsnicoll-strnicolll-wcsnicolll-mbsnicolll"></a>_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l

Porovnání řetězců pomocí informace specifické pro národní prostředí.

> [!IMPORTANT]
> **_mbsnicoll –** a **_mbsnicoll_l –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _strnicoll(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsnicoll(
   const wchar_t *string1,
   const wchar_t *string2 ,
   size_t count
);
int _mbsnicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strnicoll_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsnicoll_l(
   const wchar_t *string1,
   const wchar_t *string2 ,
   size_t count,
   _locale_t locale
);
int _mbsnicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*řetězec1*, *řetězec2*<br/>
Řetězce ukončené hodnotou null k porovnání

*Počet*<br/>
Počet znaků k porovnání

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Každou z těchto funkcí vrátí hodnotu, která určuje vztah podřetězce *řetězec1* a *řetězec2*, a to takto.

|Návratová hodnota|Relace řetězec1 k řetězec2|
|------------------|----------------------------------------|
|< 0|*řetězec1* menší než *řetězec2*|
|0|*řetězec1* identické *řetězec2*|
|> 0|*řetězec1* větší než *řetězec2*|

Každá z těchto funkcí vrátí **_NLSCMPERROR**. Chcete-li použít **_NLSCMPERROR**, zahrnout buď řetězec. H nebo MBSTRING. H. **_wcsnicoll –** může selhat, pokud buď *řetězec1* nebo *řetězec2* obsahuje kódy široká charakterová mimo doménu pořadí řazení. Když dojde k chybě, **_wcsnicoll –** může nastavit **errno** k **einval –**. Zkontrolujte chybu na volání **_wcsnicoll –**, nastavte **errno** na hodnotu 0 a poté zkontrolujte **errno** po volání **_wcsnicoll –**.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí provádí porovnávání prvního *počet* znaky v *řetězec1* a *řetězec2* podle znakové stránky. Tyto funkce by měly používat jenom v případě, že je rozdíl mezi znak nastavit pořadí a pořadí lexicographic znak v kódu stránky a tento rozdíl je určen pro porovnání řetězců. Verze tyto funkce bez **_l** příponu pomocí aktuální stránky národního prostředí a kód. Verzi pomocí **_l** příponu jsou shodné s tím rozdílem, že používají místo předaná národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

Všechny tyto funkce ověřit jejich parametrů. Pokud má jedna *řetězec1* nebo *řetězec2* je ukazatel s hodnotou null, nebo pokud je počet větší než **INT_MAX**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **_NLSCMPERROR** a nastavte **errno** k **einval –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicoll –**|**_strnicoll**|**_mbsnbicoll –**|**_wcsnicoll**|
|**_tcsnicoll –**|**_strnicoll**|[_mbsnbicoll –](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|**_wcsnicoll**|
|**_tcsnicoll_l**|**_strnicoll_l**|**_mbsnbicoll_l**|**_wcsnicoll_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strnicoll –**, **_strnicoll_l –**|\<String.h >|
|**_wcsnicoll –**, **_wcsnicoll_l –**|\<wchar.h > nebo \<string.h >|
|**_mbsnicoll –**, **_mbsnicoll_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
