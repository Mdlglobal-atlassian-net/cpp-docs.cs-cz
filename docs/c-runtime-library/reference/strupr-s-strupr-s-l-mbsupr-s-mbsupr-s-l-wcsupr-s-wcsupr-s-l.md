---
title: _strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l
ms.date: 11/04/2016
api_name:
- _strupr_s
- _strupr_s_l
- _mbsupr_s
- _wcsupr_s_l
- _mbsupr_s_l
- _wcsupr_s
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strupr_s
- mbsupr_s
- wcsupr_s
- _mbsupr_s_l
- mbsupr_s_l
- wcsupr_s_l
- _wcsupr_s
- _tcsupr_s_l
- _mbsupr_s
- _tcsupr_s
- strupr_s_l
- _wcsupr_s_l
- _strupr_s
- _strupr_s_l
helpviewer_keywords:
- mbsupr_s_l function
- strupr_s_l function
- _wcsupr_s_l function
- _tcsupr_s_l function
- mbsupr_s function
- _wcsupr_s function
- uppercase, converting strings to
- tcsupr_s function
- string conversion [C++], case
- strupr_s function
- wcsupr_s_l function
- _mbsupr_s function
- _mbsupr_s_l function
- _strupr_s_l function
- tcsupr_s_l function
- strings [C++], case
- converting case, CRT functions
- _tcsupr_s function
- strings [C++], converting case
- _strupr_s function
- wcsupr_s function
ms.assetid: 82d3a273-9f6f-4a26-9560-919d891e4581
ms.openlocfilehash: 4789116854c8975f58336984d03f1d2897851fdc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957578"
---
# <a name="_strupr_s-_strupr_s_l-_mbsupr_s-_mbsupr_s_l-_wcsupr_s-_wcsupr_s_l"></a>_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l

Převede řetězec na velká písmena pomocí aktuálního národního prostředí nebo zadaného národního prostředí, které je předáno. Tyto verze [_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbsupr_s** a **_mbsupr_s_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _strupr_s(
   char *str,
   size_t numberOfElements
);
errno_t _wcsupr_s(
   wchar_t * str,
   size_t numberOfElements
);
errno_t _strupr_s_l(
   char * str,
   size_t numberOfElements,
   _locale_t locale
);
errno_t _wcsupr_s_l(
   wchar_t * str,
   size_t numberOfElements,
   _locale_t locale
);
errno_t _mbsupr_s(
   unsigned char *str,
   size_t numberOfElements
);
errno_t _mbsupr_s_l(
   unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
template <size_t size>
errno_t _strupr_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wcsupr_s(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
errno_t _strupr_s_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _wcsupr_s_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _mbsupr_s(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
errno_t _mbsupr_s_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Řetězec na velká písmena.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; nenulový kód chyby při selhání.

Tyto funkce ověřují své parametry. Pokud je *str* ukazatel s **hodnotou null** , je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, funkce vrátí **EINVAL** a nastaví **errno** na **EINVAL**. Pokud je *numberOfElements* menší než délka řetězce, funkce vrátí **ERANGE** a nastaví **errno** na **ERANGE**.

## <a name="remarks"></a>Poznámky

Funkce **_strupr_s** převádí na místě každé malé písmeno v *str* na velká písmena. **_wcsupr_s** je verze **_strupr_s**pro nejrůznější znaky. **_mbsupr_s** je Vícebajtová znaková verze **_strupr_s**.

Převod je určen nastavením kategorie **LC_CTYPE** národního prostředí. Jiné znaky nejsou ovlivněny. Další informace o **LC_CTYPE**naleznete v tématu [setlocale](setlocale-wsetlocale.md). Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí; vize s příponou **_l** jsou stejné s tím rozdílem, že místo toho používají předané národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFD. Pokud chcete toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsupr_s**|**_strupr_s**|**_mbsupr_s**|**_wcsupr_s**|
|**_tcsupr_s_l**|**_strupr_s_l**|**_mbsupr_s_l**|**_wcsupr_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strupr_s**, **_strupr_s_l**|\<String. h >|
|**_wcsupr_s**, **_wcsupr_s_l**, **_mbsupr_s**, **_mbsupr_s_l**|\<String. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md) .

## <a name="see-also"></a>Viz také:

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)<br/>
