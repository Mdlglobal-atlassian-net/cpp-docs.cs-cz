---
title: _strset_s –, _strset_s_l –, _wcsset_s –, _wcsset_s_l –, _mbsset_s –, _mbsset_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wcsset_s
- _wcsset_s_l
- _strset_s
- _mbsset_s_l
- _strset_s_l
- _mbsset_s
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wcsset_s_l
- strset_s
- _mbsset_s
- mbsset_s
- _strset_s
- _mbsset_s_l
- strset_s_l
- _wcsset_s
- mbsset_s_l
- wcsset_s_l
- wcsset_s
- _strset_s_l
- _tcsset_s_l
- _tcsset_s
dev_langs:
- C++
helpviewer_keywords:
- mbsset_s_l function
- wcsset_s function
- _mbsset_s function
- tcsset_s function
- strset_s_l function
- characters [C++], setting
- _wcsset_s_l function
- _strset_s function
- strset_s function
- wcsset_s_l function
- strings [C++], setting characters
- _strset_s_l function
- _mbsset_s_l function
- _wcsset_s function
- tcsset_s_l function
- _tcsset_s_l function
- _tcsset_s function
- mbsset_s function
ms.assetid: dceb2909-6b41-4792-acb7-888e45bb8b35
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ece29da9880967beb78a785d257dfbd431c50ded
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="strsets-strsetsl-wcssets-wcssetsl-mbssets-mbssetsl"></a>_strset_s, _strset_s_l, _wcsset_s, _wcsset_s_l, _mbsset_s, _mbsset_s_l

Nastaví znaky řetězce z znaku. Tyto verze nástroje [_strset –, _strset_l –, _wcsset –, _wcsset_l –, _mbsset –, _mbsset_l –](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbsset_s –** a **_mbsset_s_l –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _strset_s(
   char *str,
   size_t numberOfElements,
   int c
);
errno_t _strset_s_l(
   char *str,
   size_t numberOfElements,
   int c,
   locale_t locale
);
errno_t _wcsset_s(
   wchar_t *str,
   size_t numberOfElements,
   wchar_t c
);
errno_t *_wcsset_s_l(
   wchar_t *str,
   size_t numberOfElements,
   wchar_t c,
   locale_t locale
);
errno_t _mbsset_s(
   unsigned char *str,
   size_t numberOfElements,
   unsigned int c
);
errno_t _mbsset_s_l(
   unsigned char *str,
   size_t numberOfElements,
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str –*<br/>
Řetězce ukončené hodnotou Null nastavit.

*numberOfElements*<br/>
Velikost *str* vyrovnávací paměti.

*c*<br/>
Nastavení znaků.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, v opačném případě chybový kód.

Tyto funkce ověřit jejich argumentů. Pokud *str* je ukazatel s hodnotou null, nebo *numberOfElements* argument je menší než nebo rovna 0, nebo blok předaná není ukončené hodnotou null a pak je volána obslužná rutina neplatný parametr, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **einval –** a nastavte **errno** k **einval –**.

## <a name="remarks"></a>Poznámky

**_Strset_s –** funkce nastaví všechny znaky *str* k *c* (převést na **char**), s výjimkou ukončující znak hodnoty null. **_wcsset_s –** a **_mbsset_s –** jsou široká charakterová a vícebajtových znaků verze **_strset_s –**. Datové typy argumentů a návratové hodnoty se liší podle toho. Tyto funkce chovají stejně jako jinak.

Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

Ladicí verze těchto funkcí nejprve vyplnit vyrovnávací paměť s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsset_s –**|**_strset_s**|**_mbsset_s**|**_wcsset_s**|
|**_tcsset_s_l –**|**_strset_s_l**|**_mbsset_s_l**|**_wcsset_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strset_s**|\<String.h >|
|**_strset_s_l**|\<tchar.h>|
|**_wcsset_s**|\<String.h > nebo \<wchar.h >|
|**_wcsset_s_l**|\<tchar.h>|
|**_mbsset_s –**, **_mbsset_s_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strset_s.c
#include <string.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char string[] = "Fill the string with something.";
   printf( "Before: %s\n", string );
   _strset_s( string, _countof(string), '*' );
   printf( "After:  %s\n", string );
}
```

```Output
Before: Fill the string with something.
After:  *******************************
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
