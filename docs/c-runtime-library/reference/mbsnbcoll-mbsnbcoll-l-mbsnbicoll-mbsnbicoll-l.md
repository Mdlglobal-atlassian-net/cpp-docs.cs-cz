---
title: _mbsnbcoll –, _mbsnbcoll_l –, _mbsnbicoll –, _mbsnbicoll_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19e17552a674d4931134eb9d7b436a0f858843d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405390"
---
# <a name="mbsnbcoll-mbsnbcolll-mbsnbicoll-mbsnbicolll"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Porovná *n* bajtů dvou řetězců vícebajtových znaků pomocí informací o vícebajtové znakové stránky.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*řetězec1*, *řetězec2*<br/>
Řetězce k porovnání.

*Počet*<br/>
Počet bajtů k porovnání.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota označuje vztah podřetězce *řetězec1* a *řetězec2*.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|*řetězec1* substring menší než *řetězec2* dílčí řetězec.|
|0|*řetězec1* substring identické *řetězec2* dílčí řetězec.|
|> 0|*řetězec1* substring větší než *řetězec2* dílčí řetězec.|

Pokud *řetězec1* nebo *řetězec2* je **NULL** nebo *počet* je větší než **INT_MAX**, neplatný Obslužná rutina parametru je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **_NLSCMPERROR** a nastavte **errno** k **einval –**. Chcete-li použít **_NLSCMPERROR**, zahrnout String.h nebo Mbstring.h.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí seřadí, maximálně první *počet* bajtů *řetězec1* a *řetězec2* a vrátí hodnotu, která určuje vztah mezi Výsledná podřetězce z *řetězec1* a *řetězec2*. Pokud poslední bajtů v dílčí řetězec z *řetězec1* nebo *řetězec2* vedoucím bajtem, není zahrnutý v porovnání; tyto funkce Porovnat pouze dokončení znaky v dílčích řetězců. **_mbsnbicoll –** je velká a malá písmena verze **_mbsnbcoll –**. Jako [_mbsnbcmp –](mbsnbcmp-mbsnbcmp-l.md) a [_mbsnbicmp –](mbsnbicmp-mbsnbicmp-l.md), **_mbsnbcoll –** a **_mbsnbicoll –** collate dvou řetězců vícebajtových znaků podle požadavků lexicographic pořadí zadaném vícebajtových [znaková stránka](../../c-runtime-library/code-pages.md) aktuálně používán.

Pro některé znakové stránky a odpovídající znakových sad může být pořadí znaků ve znakové sadě liší od pořadí lexicographic znaků. V národním prostředí "C", to tak není: pořadí znaků ve znakové sadě ASCII je stejný jako lexicographic pořadí znaky. Ale v některých evropských znakové stránky, například znak "a" (hodnota 0x61) předchází znak 'č. (hodnota 0xE4) v znak nastavit, ale znak 'č' předchází znak "a" lexicographically. Chcete-li provést bajtů v takové instanci lexicographic porovnání řetězců, použijte **_mbsnbcoll –** místo **_mbsnbcmp –**; chcete pouze vyhledávat rovnosti řetězec, použijte **_mbsnbcmp –**.

Protože **kol** funkce collate řetězce lexicographically pro porovnání, zatímco **cmp** funkce jednoduše testování rovnosti řetězec, **kol** jsou funkce mnohem nižší než odpovídající **cmp** verze. Proto **kol** funkce by měly používat jenom v případě, že je rozdíl mezi pořadí sady znaků a pořadí lexicographic znaků na aktuální stránce kódu a tento rozdíl je určen pro porovnání.

Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncoll –**|[_strncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll –**|[_wcsncoll](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsncoll_l**|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|**_mbsnbcoll_l**|[_wcsncoll_l](strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|
|**_tcsnicoll –**|[_strnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll –**|[_wcsnicoll](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|
|**_tcsnicoll_l**|[_strnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|**_mbsnbicoll_l**|[_wcsnicoll_l](strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcoll –**|\<Mbstring.h >|
|**_mbsnbcoll_l**|\<Mbstring.h >|
|**_mbsnbicoll –**|\<Mbstring.h >|
|**_mbsnbicoll_l**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
