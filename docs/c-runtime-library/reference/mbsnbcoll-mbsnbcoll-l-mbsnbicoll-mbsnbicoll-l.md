---
title: _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
ms.date: 11/04/2016
apiname:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
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
apitype: DLLExport
f1_keywords:
- mbsnbicoll
- mbsnbcoll
- mbsnbicoll_l
- _mbsnbcoll
- _mbsnbicoll
- _ftcsnicoll
- _ftcsncoll
- mbsnbcoll_l
helpviewer_keywords:
- _mbsnbcoll_l function
- mbsnbcoll_l function
- _mbsnbcoll function
- _tcsnicoll function
- mbsnbcoll function
- mbsnbicoll_l function
- mbsnbicoll function
- _tcsncoll function
- _mbsnbicoll function
- _mbsnbicoll_l function
- tcsncoll function
- tcsnicoll function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
ms.openlocfilehash: c18faa3c93969a683b3ee3ef58dd02e1c1ae61f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156717"
---
# <a name="mbsnbcoll-mbsnbcolll-mbsnbicoll-mbsnbicolll"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Porovná *n* bajtů dvou vícebajtových znakových řetězců pomocí informací vícebajtové kódové stránky.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbsnbcoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
int _mbsnbicoll(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbicoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*string1*, *string2*<br/>
Řetězce k porovnání.

*Počet*<br/>
Počet bajtů k porovnání.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota označuje vztah mezi podřetězci *řetězec1* a *řetězec2*.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|*řetězec1* podřetězec menší než *řetězec2* dílčí řetězec.|
|0|*řetězec1* podřetězec shodný s *řetězec2* dílčí řetězec.|
|> 0|*řetězec1* větší než podřetězec *řetězec2* dílčí řetězec.|

Pokud *řetězec1* nebo *řetězec2* je **NULL** nebo *počet* je větší než **INT_MAX**, neplatný je vyvolána obslužná rutina parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **_NLSCMPERROR** a nastavte **errno** k **EINVAL**. Chcete-li použít **_NLSCMPERROR**, zahrňte String.h nebo Mbstring.h.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí kompletuje nanejvýš prvních *počet* bajtů *řetězec1* a *řetězec2* a vrátí hodnotu, která označuje vztah mezi výsledný podřetězce z *řetězec1* a *řetězec2*. Pokud poslední bajt v podřetězci *řetězec1* nebo *řetězec2* je vedoucí bajt, není zahrnut v porovnání; tyto funkce porovnají pouze kompletní znaky v podřetězcích. **_mbsnbicoll –** je velká a malá písmena verze **_mbsnbcoll –**. Stejně jako [_mbsnbcmp –](mbsnbcmp-mbsnbcmp-l.md) a [_mbsnbicmp –](mbsnbicmp-mbsnbicmp-l.md), **_mbsnbcoll –** a **_mbsnbicoll –** kompletují dva vícebajtové znakové řetězce podle lexikografickém pořadí určeném vícebajtovou [znaková stránka](../../c-runtime-library/code-pages.md) aktuálně používán.

Pro některé kódové stránky a příslušné znakové sady pořadí znaků ve znakové sadě může lišit od pořadí lexikografických znaků. V národním prostředí "C", to není případ: pořadí znaků ve znakové sadě ASCII je stejné jako lexikografické pořadí znaků. Ale v některých evropských znakových stránek, například znak "a" (hodnota 0x61) předchází znakové "č. (hodnota 0xE4) v znakové sady, ale znak"č' předchází znak "a" lexicographically. K provedení lexikografického porovnání řetězců pomocí bajtů v takové situaci, použijte **_mbsnbcoll –** spíše než **_mbsnbcmp –**; pro kontrolu pouze rovnosti řetězců použijte **_mbsnbcmp –**.

Protože **coll** funkce kompletují řetězce lexikograficky pro porovnávání, zatímco **cmp** funkce jednoduše testují rovnost řetězců, **coll** jsou funkce mnohem pomalejší než odpovídající **cmp** verze. Proto **coll** funkce by měly být používány pouze v případě, že existuje rozdíl mezi znakové sady a lexikografickým pořadím znaků v aktuální znakové stránce a tento rozdíl je relevantní pro porovnání.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí místo něho předán v. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l**|[_wcsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l**|[_wcsnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcoll**|\<Mbstring.h >|
|**_mbsnbcoll_l**|\<Mbstring.h >|
|**_mbsnbicoll**|\<Mbstring.h >|
|**_mbsnbicoll_l**|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
