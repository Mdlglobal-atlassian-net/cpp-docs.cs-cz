---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 4/2/2020
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
- _o__mbsnbicmp
- _o__mbsnbicmp_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
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
ms.openlocfilehash: 80d2708396cdaeb86c25932c3d13129fb318719a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340568"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp, _mbsnbicmp_l

Porovná **n** bajtů dvou vícebajtových řetězců znaků a ignoruje malá a velká písmena.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězce ukončené hodnotou null k porovnání.

*Počet*<br/>
Počet bajtů k porovnání.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota označuje vztah mezi podřetězci.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|podřetězec *string1* menší než podřetězec *string2.*|
|0|*podřetězec string1* shodný s podřetězcem *string2.*|
|> 0|podřetězec *string1* větší než podřetězec *string2.*|

Při chybě **vrátí _mbsnbicmp** **_NLSCMPERROR**, který je definován v souborech String.h a Mbstring.h.

## <a name="remarks"></a>Poznámky

Funkce **_mbsnbicmp** provádí řadové porovnání nejvýše prvních *bajtů prvního počtu* *řetězce1* a *string2*. Porovnání se provádí převodem každého znaku na malá písmena; [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) je verze **_mbsnbicmp**rozlišující malá a velká písmena . Porovnání končí, pokud je dosaženo ukončujícího znaku null v obou řetězci před porovnáním znaků *počtu.* Pokud řetězce jsou stejné při ukončení null znak je dosaženo v obou řetězců před *počet* znaků jsou porovnány, kratší řetězec je menší.

**_mbsnbicmp** je podobná [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), s tím rozdílem, že porovnává řetězce až *počet* bajtů namísto podle znaků.

Dva řetězce obsahující znaky umístěné mezi "Z" a 'a' v tabulce ASCII ('[', ',\\', ',,,,,,,,,,,,,,,,,\`různé porovnání v závislosti na jejich případě. Například dva řetězce "ABCDE" a "ABCD^" porovnat jedním způsobem, pokud je porovnání malá písmena ("abcde" > "abcd^") a jiným způsobem ("ABCDE" < "ABCD^"), pokud je velká písmena.

**_mbsnbicmp** rozpoznává vícebajtové sekvence znaků podle aktuálně používáné [vícebajtové znakové stránky.](../../c-runtime-library/code-pages.md) Aktuální nastavení národního prostředí na něj nemá vliv.

Pokud je *buď string1* nebo *string2* ukazatel null, **_mbsnbicmp** vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí **_NLSCMPERROR** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
