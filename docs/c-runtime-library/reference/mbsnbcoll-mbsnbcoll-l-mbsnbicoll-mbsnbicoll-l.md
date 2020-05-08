---
title: _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
ms.date: 4/2/2020
api_name:
- _mbsnbicoll_l
- _mbsnbcoll_l
- _mbsnbcoll
- _mbsnbicoll
- _o__mbsnbcoll
- _o__mbsnbcoll_l
- _o__mbsnbicoll
- _o__mbsnbicoll_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbcoll
- _mbsnbcoll_l
- _mbsnbicoll
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
- _tcsncoll_l function
- _tcsnicoll_l function
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
ms.openlocfilehash: 491a652f19e9e1895aa62092c5c890923008f6e1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911914"
---
# <a name="_mbsnbcoll-_mbsnbcoll_l-_mbsnbicoll-_mbsnbicoll_l"></a>_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l

Porovná *n* bajtů dvou vícebajtových znakových řetězců pomocí vícebajtových informací o znakové stránce.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězce, které se mají porovnat

*výpočtu*<br/>
Počet bajtů, které mají být porovnány.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota označuje vztah podřetězců *řetězec1* a *řetězec2*.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|podřetězec *řetězec1* menší než *řetězec2* podřetězce|
|0|řetězec *řetězec1* shodný s podřetězcem *řetězec2* .|
|> 0|podřetězec *řetězec1* větší než *řetězec2* podřetězce|

Pokud *je řetězec1* nebo *řetězec2* **null** nebo je *počet* větší než **INT_MAX**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **_NLSCMPERROR** a nastaví **errno** na **EINVAL**. Chcete-li použít **_NLSCMPERROR**, zahrňte buď String. h nebo Mbstring. h.

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí se seřazením z nejvyšší *počet* bajtů v řetězci *řetězec1* a *řetězec2* a vrátí hodnotu, která označuje vztah mezi výslednými podřetězci *řetězec1* a *řetězec2*. Pokud je finální bajt v podřetězci *řetězec1* nebo *řetězec2* vedoucí bajt, není zahrnut v porovnání; Tyto funkce porovnávají pouze kompletní znaky v podřetězcích. **_mbsnbicoll** je verze **_mbsnbcoll**bez rozlišení velkých a malých písmen. Podobně jako [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) a [_mbsnbicmp](mbsnbicmp-mbsnbicmp-l.md), **_mbsnbcoll** a **_mbsnbicoll** kompletují dva vícebajtové znakové řetězce podle pořadí lexikografickým pořadím určeného vícebajtovou [znakovou stránkou](../../c-runtime-library/code-pages.md) , která se právě používá.

Pro některé znakové stránky a odpovídající znakové sady se pořadí znaků ve znakové sadě může lišit od pořadí znaků lexikografickým pořadím. V národním prostředí "C" se nejedná o tento případ: pořadí znaků v sadě znaků ASCII je stejné jako lexikografickým pořadím pořadí znaků. V některých evropských kódových stránkách například znak "a" (Value 0x61) předchází znak "ä" (Value 0xE4) ve znakové sadě, ale znak "ä" před znakem "a" lexikograficky. Chcete-li provést lexikografickým pořadím porovnání řetězců podle bajtů v takové instanci, použijte **_mbsnbcoll** místo **_mbsnbcmp**; Chcete-li kontrolovat pouze rovnost řetězců, použijte **_mbsnbcmp**.

Vzhledem k tomu, že funkce **coll** vyhodnotí řetězce lexikograficky pro porovnání, zatímco funkce **CMP** jednoduše testuje rovnost řetězců, funkce **coll** jsou mnohem pomalejší než odpovídající verze **CMP** . Proto by měly být funkce **coll** použity pouze v případě, že existuje rozdíl mezi pořadím znakové sady a pořadím znaků lexikografickým pořadím na aktuální znakové stránce a tento rozdíl je pro porovnání důležité.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** kategorie národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) . Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

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
|**_mbsnbcoll**|\<Mbstring. h>|
|**_mbsnbcoll_l**|\<Mbstring. h>|
|**_mbsnbicoll**|\<Mbstring. h>|
|**_mbsnbicoll_l**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
