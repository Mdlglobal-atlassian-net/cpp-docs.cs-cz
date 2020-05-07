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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 4017dc4f72a0072df8d0969406169a26c1da43ac
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919267"
---
# <a name="_strnextc-_wcsnextc-_mbsnextc-_mbsnextc_l"></a>_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l

Najde další znak v řetězci.

> [!IMPORTANT]
> **_mbsnextc** a **_mbsnextc_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str*<br/>
Zdrojový řetězec

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací celočíselnou hodnotu dalšího znaku v *str*.

## <a name="remarks"></a>Poznámky

Funkce **_mbsnextc** vrací celočíselnou hodnotu dalšího vícebajtového znaku v *str*, aniž by byl posunut ukazatel na řetězec. **_mbsnextc** rozpozná vícebajtové znakové sekvence podle [vícebajtové znakové stránky](../../c-runtime-library/code-pages.md) , která se právě používá.

Pokud je parametr *str* **null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí 0.

**Poznámka k zabezpečení** Toto rozhraní API způsobuje potenciální hrozbu, o kterou vznikají problémy s přetečením vyrovnávací paměti. Problémy s přetečením vyrovnávací paměti představují častější způsob útoku na systém, což vede k neoprávněnému zvýšení oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnextc**|**_strnextc**|**_mbsnextc**|**_wcsnextc**|

**_strnextc** a **_wcsnextc** jsou řetězce jednobajtových znaků a verze řetězců s řetězci s velkým počtem znaků **_mbsnextc**. **_wcsnextc** vrátí celočíselnou hodnotu dalšího širšího znaku v *str*; **_strnextc** vrací celočíselnou hodnotu následujícího jednobajtové znaku v *str*. **_strnextc** a **_wcsnextc** jsou k dispozici pouze pro toto mapování a neměla by být používána jinak. Další informace najdete v tématu [použití mapování obecného textu](../../c-runtime-library/using-generic-text-mappings.md) a [Mapování obecného textu](../../c-runtime-library/generic-text-mappings.md).

**_mbsnextc_l** je totožný s tím rozdílem, že místo toho používá parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnextc**|\<Mbstring. h>|
|**_mbsnextc_l**|\<Mbstring. h>|
|**_strnextc**|\<Tchar. h>|
|**_wcsnextc**|\<Tchar. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
