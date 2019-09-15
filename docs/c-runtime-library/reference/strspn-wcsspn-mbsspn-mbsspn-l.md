---
title: strspn, wcsspn, _mbsspn, _mbsspn_l
ms.date: 11/04/2016
api_name:
- _mbsspn_l
- wcsspn
- strspn
- _mbsspn
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftcsspn
- wcsspn
- _mbsspn
- _tcsspn
- strspn
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
ms.openlocfilehash: 8e65e466e95464dbd928ff0d80d975ce23fc180c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946759"
---
# <a name="strspn-wcsspn-_mbsspn-_mbsspn_l"></a>strspn, wcsspn, _mbsspn, _mbsspn_l

Vrátí index prvního znaku v řetězci, který nepatří do sady znaků.

> [!IMPORTANT]
> **_mbsspn** a **_mbsspn_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str*<br/>
Řetězec zakončený hodnotou null pro hledání.

*strCharSet*<br/>
Znaková sada zakončená hodnotou null

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrací celočíselnou hodnotu určující délku podřetězce v *str* , která obsahuje pouze znaky v *strCharSet*. Pokud *str* začíná znakem, který není v *strCharSet*, vrátí funkce hodnotu 0.

## <a name="remarks"></a>Poznámky

Funkce **strspn** vrací index prvního znaku v *str* , který nepatří do sady znaků v *strCharSet*. Hledání nezahrnuje ukončující znaky null.

**wcsspn** a **_mbsspn** jsou verze s velkým znakem a vícebajtovým znakem **strspn**. Argumenty **wcsspn** jsou řetězce s velkým počtem znaků; ty z **_mbsspn** jsou vícebajtové znakové řetězce. **_mbsspn** ověří své parametry. Pokud parametr *str* nebo *StrCharSet* má **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, **_mbspn** nastaví **errno** na **EINVAL** a vrátí 0. **strspn** a **wcsspn** neověřují své parametry. Tyto tři funkce se chovají identicky jinak.

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) . Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že místo toho používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsspn**|**strspn**|**_mbsspn**|**wcsspn**|
|**není k dispozici**|**není k dispozici**|**_mbsspn_l**|**není k dispozici**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strspn**|\<String. h >|
|**wcsspn**|\<String. h > nebo \<WCHAR. h >|
|**_mbsspn**, **_mbsspn_l**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strspnp, _wcsspnp, _mbsspnp, _mbsspnp_l](strspnp-wcsspnp-mbsspnp-mbsspnp-l.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
