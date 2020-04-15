---
title: _mbsnbcat, _mbsnbcat_l
ms.date: 4/2/2020
api_name:
- _mbsnbcat_l
- _mbsnbcat
- _o__mbsnbcat
- _o__mbsnbcat_l
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
- mbsnbcat
- mbsnbcat_l
- _mbsnbcat
- _mbsnbcat_l
helpviewer_keywords:
- tcsncat_l function
- _tcsncat function
- mbsnbcat_l function
- mbsnbcat function
- _mbsnbcat_l function
- _tcsncat_l function
- _mbsnbcat function
- tcsncat function
ms.assetid: aa0f1d30-0ddd-48d1-88eb-c6884b20fd91
ms.openlocfilehash: 7598b20db4698ff8f95fbcefa00864be1b958447
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340808"
---
# <a name="_mbsnbcat-_mbsnbcat_l"></a>_mbsnbcat, _mbsnbcat_l

Připojí maximálně první **n** bajtů jednoho vícebajtového znakového řetězce k jinému. K dispozici jsou bezpečnější verze těchto funkcí. viz [_mbsnbcat_s, _mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned char *_mbsnbcat(
   unsigned char *dest,
   const unsigned char *src,
   size_t count
);
unsigned char *_mbsnbcat_l(
   unsigned char *dest,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
unsigned char *_mbsnbcat(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsnbcat_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*Dest*<br/>
Cílový řetězec s vícebajtovými znaky ukončený nulou.

*src*<br/>
Zdrojový řetězec s vícebajtovými znaky ukončený nulou.

*Počet*<br/>
Počet bajtů od *src* do připojit *k dest*.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_mbsnbcat** vrátí ukazatel na cílový řetězec. Žádná vrácená hodnota je vyhrazena k označení chyby.

## <a name="remarks"></a>Poznámky

Funkce **_mbsnbcat** připojí maximálně první *počet* bajtů *src* na *dest*. Pokud je bajt bezprostředně předcházející znaku null v *znaku dest* úvodní bajt, počáteční bajt *src* přepíše tento úvodní bajt zájemce. V opačném případě počáteční bajt *src* přepíše ukončující znak null *dest*. Pokud se v *src* před připojením bajtů *počtu* zobrazí nulový bajt, **_mbsnbcat** připojí všechny bajty z *src*až do nulového znaku. *Je-li počet* větší než délka *src*, použije se místo *počítání*délka *src* . Výsledný řetězec je ukončen s prázdným znakem. Pokud kopírování probíhá mezi řetězci, které se překrývají, chování není definováno.

Výstupní hodnota je ovlivněna nastavením nastavení **LC_CTYPE** kategorie národního prostředí; další informace naleznete [v tématu setlocale.](setlocale-wsetlocale.md) Verze **_mbsnbcat** funkce používá aktuální národní prostředí pro toto chování závislé na národním prostředí; **verze _mbsnbcat_l** je identická s tím rozdílem, že místo toho používají parametr národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

**Poznámka k zabezpečení** Použijte řetězec s ukončeným hodnotou null. Řetězec ukončený hodnotou null nesmí překročit velikost cílové vyrovnávací paměti. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Pokud *dest* nebo *src* je **NULL**, funkce vygeneruje neplatnou chybu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce vrátí **EINVAL** a nastaví **errno** na **EINVAL**.

V jazyce C++ mají tyto funkce přetížení šablony, které vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat (Strncat)](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat**|[wcsncat (wcsncat)](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_l**|**_strncat_l**|**_mbsnbcat_l**|**_wcsncat_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcat**|\<mbstring.h>|
|**_mbsnbcat_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[_mbsnbcat_s, _mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md)<br/>
