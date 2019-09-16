---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 11/04/2016
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 19ffa4c47f0144ba136607fe5cef09e9bd65374f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952192"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp, _mbsnbicmp_l

Porovná **n** bajtů dvou vícebajtových znakových řetězců a ignoruje velikost písmen.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*řetězec1*, *řetězec2*<br/>
Řetězec zakončený hodnotou null k porovnání

*výpočtu*<br/>
Počet bajtů, které mají být porovnány.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota označuje vztah mezi podřetězci.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|podřetězec *řetězec1* menší než *řetězec2* podřetězce|
|0|řetězec *řetězec1* shodný s podřetězcem *řetězec2* .|
|> 0|podřetězec *řetězec1* větší než *řetězec2* podřetězce|

V případě chyby vrátí **_mbsnbicmp** hodnotu **_NLSCMPERROR**, která je definována v řetězci. h a Mbstring. h.

## <a name="remarks"></a>Poznámky

Funkce **_mbsnbicmp** provádí ordinální porovnání v nejvíce prvním *počtu* bajtů *řetězec1* a *řetězec2*. Porovnání je provedeno převodem každého znaku na malá. [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) je verze **_mbsnbicmp**s rozlišováním velkých a malých písmen. Porovnání končí, pokud je dosaženo ukončujícího znaku null v řetězci před porovnáním znaků *Count* . Pokud jsou řetězce stejné, když je dosaženo ukončujícího znaku null v řetězci předtím, než jsou znaky *Count* porovnány, kratší řetězec je menší.

**_mbsnbicmp** se podobá [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), s tím rozdílem, že porovnává řetězce až po *počet* bajtů místo znaků.

Dva řetězce, které obsahují znaky umístěné mezi ' Z ' a ' a ' v tabulce ASCII (' [',\\', '] ', ' @ ', ' _\`' a ' ') porovnávají odlišně v závislosti na jejich velikosti. Například dva řetězce "ABCDE" a "ABCD ^" porovnávají jeden ze způsobů, pokud je porovnávání malými písmeny ("abcde" > "abcd ^") a druhým způsobem ("ABCDE" < "ABCD ^"), pokud se jedná o velká písmena.

**_mbsnbicmp** rozpoznává vícebajtové znakové sekvence podle [vícebajtové znakové stránky](../../c-runtime-library/code-pages.md) , která se právě používá. Není ovlivněno aktuálním nastavením národního prostředí.

Pokud je buď *řetězec1* nebo *řetězec2* ukazatel s hodnotou null, vyvolá **_mbsnbicmp** neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbicmp**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
