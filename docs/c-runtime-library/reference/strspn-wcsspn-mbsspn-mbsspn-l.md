---
title: strspn –, wcsspn –, _mbsspn –, _mbsspn_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsspn_l
- wcsspn
- strspn
- _mbsspn
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
- _ftcsspn
- wcsspn
- _mbsspn
- _tcsspn
- strspn
dev_langs:
- C++
helpviewer_keywords:
- wcsspn function
- strings [C++], searching
- mbsspn function
- tcsspn function
- strspn function
- substrings, finding
- _mbsspn_l function
- ftcsspn function
- _mbsspn function
- _ftcsspn function
- mbsspn_l function
- _tcsspn function
ms.assetid: d077284a-809f-4068-959e-c6d6262677eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b7d826b72a006e0a8b011d89dfc96aa8aea4690
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415158"
---
# <a name="strspn-wcsspn-mbsspn-mbsspnl"></a>strspn, wcsspn, _mbsspn, _mbsspn_l

Vrátí index prvního znaku v řetězci, který nepatří do sadu znaků.

> [!IMPORTANT]
> **_mbsspn –** a **_mbsspn_l –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
size_t strspn(
   const char *str,
   const char *strCharSet
);
size_t wcsspn(
   const wchar_t *str,
   const wchar_t *strCharSet
);
size_t _mbsspn(
   const unsigned char *str,
   const unsigned char *strCharSet
);
size_t _mbsspn_l(
   const unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str –*<br/>
Řetězce ukončené hodnotou Null pro vyhledávání.

*strCharSet*<br/>
Ukončené hodnotou Null znakovou sadu.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrací celočíselnou hodnotu určující délku podřetězce v *str* který se skládá pouze z v *strCharSet*. Pokud *str* začíná znakem není ve *strCharSet*, funkce vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

**Strspn –** funkce vrátí index prvního znaku v *str* , nepatří do sady znaků v *strCharSet*. Hledání nezahrnuje ukončení znaky null.

**wcsspn –** a **_mbsspn –** jsou široká charakterová a vícebajtových znaků verze **strspn –**. Argumenty **wcsspn –** jsou široká charakterová řetězce; u **_mbsspn –** jsou řetězců vícebajtových znaků. **_mbsspn –** ověří jeho parametry. Pokud *str* nebo *strCharSet* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud chcete pokračovat, je povoleno spuštění **_mbspn** nastaví **errno** k **einval –** a vrátí hodnotu 0. **strspn –** a **wcsspn –** neověřují jejich parametrů. Tyto tři funkce chovají stejně jako jinak.

Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsspn –**|**strspn**|**_mbsspn**|**wcsspn**|
|**není k dispozici**|**není k dispozici**|**_mbsspn_l**|**není k dispozici**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strspn**|\<String.h >|
|**wcsspn**|\<String.h > nebo \<wchar.h >|
|**_mbsspn –**, **_mbsspn_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strspn.c
// This program uses strspn to determine
// the length of the segment in the string "cabbage"
// consisting of a's, b's, and c's. In other words,
// it finds the first non-abc letter.
//

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[] = "cabbage";
   int  result;
   result = strspn( string, "abc" );
   printf( "The portion of '%s' containing only a, b, or c "
           "is %d bytes long\n", string, result );
}
```

```Output
The portion of 'cabbage' containing only a, b, or c is 5 bytes long
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strspnp, _wcsspnp, _mbsspnp, _mbsspnp_l](strspnp-wcsspnp-mbsspnp-mbsspnp-l.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
