---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 11/04/2016
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
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
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
ms.openlocfilehash: 059d0781e465f6491f27fd634bbc4479104bc12f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331295"
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp, _mbsnbicmp_l

Porovná **n** bajtů dvou vícebajtových znakových řetězců a ignoruje velikost písmen.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*string1*, *string2*<br/>
Řetězec zakončený hodnotou Null pro srovnání.

*Počet*<br/>
Počet bajtů k porovnání.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota označuje vztah mezi podřetězci.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|*řetězec1* podřetězec menší než *řetězec2* dílčí řetězec.|
|0|*řetězec1* podřetězec shodný s *řetězec2* dílčí řetězec.|
|> 0|*řetězec1* větší než podřetězec *řetězec2* dílčí řetězec.|

V případě chyby **_mbsnbicmp –** vrátí **_NLSCMPERROR**, který je definován v souborech String.h a Mbstring.h.

## <a name="remarks"></a>Poznámky

**_Mbsnbicmp –** funkce provádí řadové porovnání nanejvýš prvních *počet* bajtů *řetězec1* a *řetězec2*. Porovnání je provedeno převedením na malá písmena; každý znak [_mbsnbcmp –](mbsnbcmp-mbsnbcmp-l.md) je velká a malá písmena verze **_mbsnbicmp –**. Porovnání končí, když je dosaženo ukončujícího znaku null v jednom z řetězců před *počet* znaků. Pokud jsou řetězce shodné při dosažení ukončujícího znaku null v jednom z řetězců před *počet* jsou porovnány znaky, kratší řetězec je menší.

**_mbsnbicmp –** je podobný [_mbsnbcmp –](mbsnbcmp-mbsnbcmp-l.md), s tím rozdílem, že porovná řetězce až *počet* bajtů namísto znaků.

Dva řetězce obsahují znaky umístěné mezi "Z" a "a" v tabulce ASCII ('[','\\","] "," ^ ","_"a"\`") porovnávají různě v závislosti na velikosti jejich písmen. Například dva řetězce "ABCDE" a "ABCD ^" porovnávají jeden ze způsobů, pokud je výsledkem porovnávání malá písmena ("abcde" > "abcd ^") a jiným způsobem ("ABCDE" < "ABCD ^") Pokud je velké písmeno.

**_mbsnbicmp –** rozpozná vícebajtové znakové sekvence podle [vícebajtové znakové stránky](../../c-runtime-library/code-pages.md) aktuálně používán. Není ovlivněna aktuálním nastavením národního prostředí.

Pokud *řetězec1* nebo *řetězec2* je ukazatel s hodnotou null, **_mbsnbicmp –** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **_NLSCMPERROR** a nastaví **errno** k **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbicmp**|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_mbsnbcmp – _mbsnbcmp_l –](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
