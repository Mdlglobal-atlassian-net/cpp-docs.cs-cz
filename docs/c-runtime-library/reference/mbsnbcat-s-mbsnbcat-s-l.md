---
title: _mbsnbcat_s, _mbsnbcat_s_l
ms.date: 4/2/2020
api_name:
- _mbsnbcat_s_l
- _mbsnbcat_s
- _o__mbsnbcat_s
- _o__mbsnbcat_s_l
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
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
ms.openlocfilehash: b4a9540025ad039458203eec1cc950187b6316a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340788"
---
# <a name="_mbsnbcat_s-_mbsnbcat_s_l"></a>_mbsnbcat_s, _mbsnbcat_s_l

Připojí se k vícebajtovému znakovému řetězci, maximálně k **prvnímu n** bajtům jiného vícebajtového znakového řetězce. Jedná se o verze [_mbsnbcat, _mbsnbcat_l,](mbsnbcat-mbsnbcat-l.md) které mají vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _mbsnbcat_s(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count
);
errno_t _mbsnbcat_s_l(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcat_s(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcat_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*Dest*<br/>
Cílový řetězec s vícebajtovými znaky ukončený nulou.

*sizeInBytes*<br/>
Velikost vyrovnávací paměti *dest* v bajtů.

*src*<br/>
Zdrojový řetězec s vícebajtovými znaky ukončený nulou.

*Počet*<br/>
Počet bajtů od *src* do připojit *k dest*.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; v opačném případě kód chyby.

### <a name="error-conditions"></a>Chybové stavy

|**Dest**|*sizeInBytes*|*src*|Návratová hodnota|
|------------|-------------------|-----------|------------------|
|**Null**|jakékoli|jakékoli|**EINVAL**|
|Všechny|<= 0|jakékoli|**EINVAL**|
|Všechny|jakékoli|**Null**|**EINVAL**|

Pokud dojde k některéz chybových podmínek, funkce generuje neplatnou chybu parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce vrátí **EINVAL** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_mbsnbcat_s** připojí k *dest*, maximálně první *počet* bajtů *src*. Pokud bajt, který bezprostředně předchází znaknull v *dest* je úvodní bajt, je přepsán počáteční bajt *src*. V opačném případě počáteční bajt *src* přepíše ukončující znak null *dest*. Pokud se v *src* před připojením bajtů *počtu* zobrazí nulový bajt, **_mbsnbcat_s** připojí všechny bajty z *src*až do nulového znaku. *Je-li počet* větší než délka *src*, použije se místo *počítání*délka *src* . Výsledný řetězec je ukončen prázdným znakem. Pokud kopírování probíhá mezi řetězci, které se překrývají, chování není definováno.

Výstupní hodnota je ovlivněna nastavením nastavení **LC_CTYPE** kategorie národního prostředí; další informace naleznete [v _wsetlocale setlocale.](setlocale-wsetlocale.md) Verze těchto funkcí jsou identické, s tím rozdílem, že ty, které nemají **_l** příponu použít aktuální národní prostředí a ty, které mají **příponu _l** místo toho použít parametr národního prostředí, který je předán. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky a tím eliminovat potřebu zadat argument velikost a mohou automaticky použít své novější, bezpečnější funkce nahradit starší, méně zabezpečené funkce. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze knihovny těchto funkcí nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat (Strncat)](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat (wcsncat)](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring.h>|
|**_mbsnbcat_s_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
