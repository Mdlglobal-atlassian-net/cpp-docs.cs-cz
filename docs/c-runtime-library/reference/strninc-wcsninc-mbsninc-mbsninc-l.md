---
title: _strninc, _wcsninc, _mbsninc, _mbsninc_l
ms.date: 11/04/2016
api_name:
- _mbsninc
- _mbsninc_l
- _wcsninc
- _strninc
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
- strninc
- wcsninc
- mbsninc_l
- _strninc
- _tcsninc
- mbsninc
- _mbsninc_l
- _ftcsninc
- _wcsninc
- _mbsninc
helpviewer_keywords:
- _mbsninc_l function
- mbsninc function
- _strninc function
- tcsninc function
- wcsninc function
- _mbsninc function
- strninc function
- _wcsninc function
- mbsninc_l function
- _tcsninc function
ms.assetid: 6caace64-f9e4-48c0-afa8-ea51824ad723
ms.openlocfilehash: b03ca4c9515bd2c70a1ce2574850e23b3add44c5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947062"
---
# <a name="_strninc-_wcsninc-_mbsninc-_mbsninc_l"></a>_strninc, _wcsninc, _mbsninc, _mbsninc_l

Posune ukazatel řetězce o **n** znaků.

> [!IMPORTANT]
> **_mbsninc** a **_mbsninc_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strninc(
   const char *str,
   size_t count
);
wchar_t *_wcsninc(
   const wchar_t *str,
   size_t count
);
unsigned char *_mbsninc(
   const unsigned char *str,
   size_t count
);
unsigned char *_mbsninc(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Zdrojový řetězec

*výpočtu*<br/>
Počet znaků, které mají zvýšit ukazatel na řetězec.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrací ukazatel na *str* po zvýšení hodnoty *str* pomocí *počtu* znaků nebo **hodnoty null** , pokud je zadaný ukazatel **null**. Pokud je *počet* větší než nebo roven počtu znaků v *str*, výsledek není definován.

## <a name="remarks"></a>Poznámky

Funkce **_mbsninc** zvyšuje *str* podle *počtu* vícebajtových znaků. **_mbsninc** rozpoznává vícebajtové znakové sekvence podle [vícebajtové znakové stránky](../../c-runtime-library/code-pages.md) , která se právě používá.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsninc**|**_strninc**|**_mbsninc**|**_wcsninc**|

**_strninc** a **_wcsninc** jsou řetězce jednobajtových znaků a verze řetězců s velkým počtem znaků **_mbsninc**. **_wcsninc** a **_strninc** jsou k dispozici pouze pro toto mapování a neměla by být použita jinak. Další informace najdete v tématu [použití mapování obecného textu](../../c-runtime-library/using-generic-text-mappings.md) a [Mapování obecného textu](../../c-runtime-library/generic-text-mappings.md).

**_mbsninc_l** je totožný s tím rozdílem, že místo toho používá parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsninc**|\<Mbstring. h >|
|**_mbsninc_l**|\<Mbstring. h >|
|**_strninc**|\<tchar.h>|
|**_wcsninc**|\<tchar.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
