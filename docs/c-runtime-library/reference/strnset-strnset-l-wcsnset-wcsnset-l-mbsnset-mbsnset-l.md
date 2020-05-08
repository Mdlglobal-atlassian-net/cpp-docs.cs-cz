---
title: _strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l
ms.date: 4/2/2020
api_name:
- _mbsnset
- _strnset
- _mbsnset_l
- _wcsnset_l
- _wcsnset
- _strnset_l
- _o__mbsnset
- _o__mbsnset_l
- _o__wcsnset
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsncset_l
- mbsnset_l
- _tcsnset_l
- _fstrnset
- _wcsnset_l
- _ftcsnset
- wcsnset_l
- _mbsnset_l
- _strnset
- _tcsnset
- _strnset_l
- mbsnset
- strnset_l
- _mbsnset
- _wcsnset
- _tcsncset
helpviewer_keywords:
- _wcsnset function
- strnset_l function
- tcsnset function
- tcsncset function
- characters [C++], initializing to formats
- mbsnset function
- _tcsnset_l function
- _mbsnset function
- _strnset function
- _tcsncset_l function
- mbsnset_l function
- _tcsnset function
- initializing characters
- _tcsncset function
- ftcsnset function
- wcsnset_l function
- _ftcsnset function
- _wcsnset_l function
- _fstrnset function
- _mbsnset_l function
- _strnset_l function
- fstrnset function
- strings [C++], initializing
- tcsnset_l function
ms.assetid: 3f306489-5763-48e5-b939-aefee7c94ef5
ms.openlocfilehash: 2bd0c31b025b9a11cbdb10e8607a283d6ae1f84b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911187"
---
# <a name="_strnset-_strnset_l-_wcsnset-_wcsnset_l-_mbsnset-_mbsnset_l"></a>_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l

Inicializuje znaky řetězce na daný znak. Existují bezpečnější verze těchto funkcí; viz [_strnset_s, _strnset_s_l, _wcsnset_s, _wcsnset_s_l, _mbsnset_s, _mbsnset_s_l](strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md).

> [!IMPORTANT]
> **_mbsnset** a **_mbsnset_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strnset(
   char *str,
   int c,
   size_t count
);
char *_strnset_l(
   char *str,
   int c,
   size_t count,
   locale_t locale
);
wchar_t *_wcsnset(
   wchar_t *str,
   wchar_t c,
   size_t count
);
wchar_t *_wcsnset_l(
   wchar_t *str,
   wchar_t c,
   size_t count,
   _locale_t locale
);
unsigned char *_mbsnset(
   unsigned char *str,
   unsigned int c,
   size_t count
);
unsigned char *_mbsnset_l(
   unsigned char *str,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Řetězec, který má být změněn.

*r*<br/>
Nastavení znaků.

*výpočtu*<br/>
Počet znaků, které mají být nastaveny.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na upravený řetězec.

## <a name="remarks"></a>Poznámky

Funkce **_strnset** nastaví maximálně první *počet* znaků str na typ *str* *(převedeno na* **char**). Pokud je *počet* větší než délka *str*, místo funkce *Count*se použije délka *str* .

**_wcsnset** a **_mbsnset** jsou verze **_strnset**a vícebajtových znaků. Argumenty řetězce a návratová hodnota **_wcsnset** jsou řetězce s velkým počtem znaků; **_mbsnset** jsou vícebajtové znakové řetězce. Tyto tři funkce se chovají identicky jinak.

**_mbsnset** ověří své parametry; Pokud je *str* ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, **_mbsnset** vrátí **hodnotu null** a nastaví **errno** na **EINVAL**. **_strnset** a **_wcsnset** neověřují své parametry.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** kategorie národního prostředí; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md) . Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnset**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strnset**|\<String. h>|
|**_strnset_l**|\<Tchar. h>|
|**_wcsnset**|\<String. h> nebo \<WCHAR. h>|
|**_wcsnset_l**|\<Tchar. h>|
|**_mbsnset** **_mbsnset_l**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strnset.c
// compile with: /W3
#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 characters of string to be *'s */
   printf( "Before: %s\n", string );
   _strnset( string, '*', 4 ); // C4996
   // Note: _strnset is deprecated; consider using _strnset_s
   printf( "After:  %s\n", string );
}
```

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
