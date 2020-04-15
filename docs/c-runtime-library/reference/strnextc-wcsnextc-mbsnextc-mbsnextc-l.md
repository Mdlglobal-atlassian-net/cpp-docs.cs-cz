---
title: _strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l
ms.date: 4/2/2020
api_name:
- _strnextc
- _mbsnextc_l
- _mbsnextc
- _wcsnextc
- _o__mbsnextc
- _o__mbsnextc_l
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
- strnextc
- tcsnextc
- _mbsnextc_l
- _mbsnextc
- mbsnextc_l
- ftcsnextc
- mbsnextc
- _tcsnextc
- _wcsnextc
- _ftcsnextc
- _strnextc
- wcsnextc
helpviewer_keywords:
- _mbsnextc function
- _tcsnextc function
- _wcsnextc function
- tcsnextc function
- strnextc function
- mbsnextc function
- _strnextc function
- _mbsnextc_l function
- mbsnextc_l function
- wcsnextc function
ms.assetid: e3086173-9eb5-4540-a23a-5d866bd05340
ms.openlocfilehash: 69c9c3d89f2d74c133558eab99d6687fd0055ca2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364493"
---
# <a name="_strnextc-_wcsnextc-_mbsnextc-_mbsnextc_l"></a>_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l

Najde další znak v řetězci.

> [!IMPORTANT]
> **_mbsnextc** a **_mbsnextc_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _strnextc(
   const char *str
);
unsigned int _wscnextc(
   const wchar_t *str
);
unsigned int _mbsnextc(
   const unsigned char *str
);
unsigned int _mbsnextc_l(
   const unsigned char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Zdrojový řetězec.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrátí celou hodnotu dalšího znaku v *str*.

## <a name="remarks"></a>Poznámky

Funkce **_mbsnextc** vrátí celou hodnotu dalšího vícebajtového znaku v *str*, aniž by došlo k posunu ukazatele řetězce. **_mbsnextc** rozpozná vícebajtové sekvence znaků podle aktuálně používáné [vícebajtové znakové stránky.](../../c-runtime-library/code-pages.md)

Pokud *str* je **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí 0.

**Poznámka k zabezpečení** Toto rozhraní API vznikne potenciální hrozbu způsobené problém přetečení vyrovnávací paměti. Problémy s přetečením vyrovnávací paměti jsou častou metodou systémového útoku, což vede k neoprávněnému zvýšení oprávnění. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnextc**|**_strnextc**|**_mbsnextc**|**_wcsnextc**|

**_strnextc** a **_wcsnextc** jsou jednobajtové řetězce a širokoznakové řetězcové verze **_mbsnextc**. **_wcsnextc** vrátí celočíselnou hodnotu dalšího širokého znaku v *str*; **_strnextc** vrátí celočíselnou hodnotu dalšího jednobajtového znaku v *str*. **_strnextc** a **_wcsnextc** jsou k dispozici pouze pro toto mapování a jinak by neměly být používány. Další informace naleznete [v tématu Použití mapování obecného textu](../../c-runtime-library/using-generic-text-mappings.md) a mapování [obecného textu](../../c-runtime-library/generic-text-mappings.md).

**_mbsnextc_l** je totožný s tím rozdílem, že místo toho používá parametr národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnextc**|\<mbstring.h>|
|**_mbsnextc_l**|\<mbstring.h>|
|**_strnextc**|\<tchar.h>|
|**_wcsnextc**|\<tchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
