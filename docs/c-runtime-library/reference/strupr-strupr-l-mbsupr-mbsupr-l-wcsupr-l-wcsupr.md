---
title: _strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr
ms.date: 4/2/2020
api_name:
- _mbsupr_l
- _mbsupr
- _strupr_l
- _wcsupr
- _wcsupr_l
- _strupr
- _o__mbsupr
- _o__mbsupr_l
- _o__strupr
- _o__strupr_l
- _o__wcsupr
- _o__wcsupr_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsupr
- _ftcsupr
- mbsupr
- _tcsupr
- strupr_l
- _fstrupr
- _strupr
- mbsupr_l
- _wcsupr
helpviewer_keywords:
- tcsupr_l function
- mbsupr function
- strupr function
- uppercase, converting strings to
- wcsupr function
- _wcsupr function
- string conversion [C++], case
- ftcsupr function
- _ftcsupr function
- _wcsupr_l function
- wcsupr_l function
- strings [C++], case
- tcsupr function
- _tcsupr_l function
- _fstrupr function
- _strupr_l function
- _mbsupr_l function
- converting case, CRT functions
- fstrupr function
- mbsupr_l function
- strupr_l function
- _strupr function
- _mbsupr function
- _tcsupr function
- strings [C++], converting case
ms.assetid: caac8f16-c233-41b6-91ce-575ec7061b77
ms.openlocfilehash: 5127c6f0be6375585be3b321788ba04a91364e57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362899"
---
# <a name="_strupr-_strupr_l-_mbsupr-_mbsupr_l-_wcsupr_l-_wcsupr"></a>_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr

Převede řetězec na velká písmena. K dispozici jsou bezpečnější verze těchto funkcí. viz [_strupr_s, _strupr_s_l, _mbsupr_s _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md).

> [!IMPORTANT]
> **_mbsupr** a **_mbsupr_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strupr(
   char *str
);
wchar_t *_wcsupr(
   wchar_t *str
);
unsigned char *_mbsupr(
   unsigned char *str
);
char *_strupr_l(
   char *str,
   _locale_t locale
);
wchar_t *_wcsupr_l(
   wchar_t *str,
   _locale_t locale
);
unsigned char *_mbsupr_l(
   unsigned char *str,
   _locale_t locale
);
template <size_t size>
char *_strupr(
   char (&str)[size]
); // C++ only
template <size_t size>
wchar_t *_wcsupr(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
unsigned char *_mbsupr(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
char *_strupr_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
wchar_t *_wcsupr_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
unsigned char *_mbsupr_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Řetězec pro velké písmena.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na změněný řetězec. Vzhledem k tomu, že změna se provádí na místě, je vrácený ukazatel stejný jako ukazatel předaná jako vstupní argument. Žádná vrácená hodnota je vyhrazena k označení chyby.

## <a name="remarks"></a>Poznámky

Funkce **_strupr** převede na místě každé malé písmeno v *str* na velká písmena. Převod je určen nastavením **kategorie LC_CTYPE** národního prostředí. Ostatní znaky nejsou ovlivněny. Další informace o **LC_CTYPE**naleznete v [tématu setlocale](setlocale-wsetlocale.md). Verze těchto funkcí bez **_l** přípony používají aktuální národní prostředí; verze s **příponou _l** jsou identické s tím rozdílem, že místo toho používají národní prostředí předané. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

**_wcsupr** a **_mbsupr** jsou verze **_strupr**s širokými znaky a vícebajtovými znaky . Argument a vrácená hodnota **_wcsupr** jsou řetězce širokých znaků; **_mbsupr** jsou vícebajtové řetězce znaků. Tyto tři funkce se chovají stejně jinak.

Pokud *str* je ukazatel null, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, tyto funkce vrátí původní řetězec a nastavit **errno** **eINVAL**.

V jazyce C++ mají tyto funkce přetížení šablony, které vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsupr**|**_strupr**|**_mbsupr**|**_wcsupr**|
|**_tcsupr_l**|**_strupr_l**|**_mbsupr_l**|**_wcsupr_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strupr** **_strupr_l**|\<string.h>|
|**_wcsupr**, **_wcsupr_l**|\<string.h> \<nebo wchar.h>|
|**_mbsupr**, **_mbsupr_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_strlwr](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md).

## <a name="see-also"></a>Viz také

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)<br/>
