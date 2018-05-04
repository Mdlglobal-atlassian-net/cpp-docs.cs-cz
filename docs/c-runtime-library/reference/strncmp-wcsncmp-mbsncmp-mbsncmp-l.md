---
title: strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
dev_langs:
- C++
helpviewer_keywords:
- _tcsnccmp function
- ftcsncmp function
- wcsncmp function
- _ftcsncmp function
- _mbsncmp function
- tcsncmp function
- mbsncmp function
- _mbsncmp_l function
- mbsncmp_l function
- strncmp function
- strings [C++], comparing characters of
- string comparison [C++], strncmp function
- _tcsncmp function
- tcsnccmp function
- ftcsnccmp function
- characters [C++], comparing
- _ftcsnccmp function
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a64d7248151287f4f2af38e666db62f9a15d833f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="strncmp-wcsncmp-mbsncmp-mbsncmpl"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Porovná až do zadaného počtu znaků dva řetězce.

> [!IMPORTANT]
> **_mbsncmp –** a **_mbsncmp_l –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int strncmp(
   const char *string1,
   const char *string2,
   size_t count
);
int wcsncmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsncmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*řetězec1*, *řetězec2*<br/>
Řetězce k porovnání.

*Počet*<br/>
Počet znaků, které mají být porovnány.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota označuje vztah podřetězce *řetězec1* a *řetězec2* následujícím způsobem.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|*řetězec1* substring menší než *řetězec2* dílčí řetězec|
|0|*řetězec1* substring identické *řetězec2* dílčí řetězec|
|> 0|*řetězec1* substring větší než *řetězec2* dílčí řetězec|

Parametr chyby ověření **_mbsncmp –** a **_mbsncmp_l –** vrátit **_NLSCMPERROR**, která je definována v \<string.h > a \< Mbstring.h >.

## <a name="remarks"></a>Poznámky

**Strncmp –** funkce provádí ordinální porovnávání maximálně prvního *počet* znaky v *řetězec1* a *řetězec2* a Vrátí hodnotu, která určuje vztah mezi dílčích řetězců. **strncmp –** je malá a velká písmena verze **_strnicmp –**. **wcsncmp –** a **_mbsncmp –** se malá a velká písmena verzích **_wcsnicmp –** a **_mbsnicmp –**.

**wcsncmp –** a **_mbsncmp –** jsou široká charakterová a vícebajtových znaků verze **strncmp –**. Argumenty **wcsncmp –** jsou široká charakterová řetězce; u **_mbsncmp –** jsou řetězců vícebajtových znaků. **_mbsncmp –** rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky a vrátí **_NLSCMPERROR** na chybu.

Navíc **_mbsncmp –** a **_mbsncmp_l –** ověřte parametry. Pokud *řetězec1* nebo *řetězec2* je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **_mbsncmp –** a **_mbsncmp_l –** vrátit **_NLSCMPERROR** a nastavte **errno** k  **Einval –**. **strncmp –** a **wcsncmp –** neověřují jejich parametrů. Tyto funkce chovají stejně jako jinak.

Porovnání chování **_mbsncmp –** a **_mbsncmp_l –** je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí. Tato volba určuje detekce úvodní a koncové bajtů více-bajtové znaky. Další informace najdete v tématu [setlocale](setlocale-wsetlocale.md). **_Mbsncmp –** funkce používá aktuální národní prostředí pro toto chování závislých na národním prostředí. **_Mbsncmp_l –** funkce se shoduje s tím rozdílem, že se používá *národního prostředí* parametr místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md). Pokud národní prostředí je národní prostředí jednobajtové, chování těchto funkcí je stejný jako **strncmp –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp –**|**strncmp –**|**_mbsncmp**|**wcsncmp –**|
|**_tcsncmp –**|**strncmp –**|**_mbsnbcmp**|**wcsncmp –**|
|**_tccmp**|Mapuje makro nebo vložené funkce|**_mbsncmp**|Mapuje makro nebo vložené funkce|
|**Není k dispozici**|**Není k dispozici**|**_mbsncmp_l**|**Není k dispozici**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strncmp –**|\<String.h >|
|**wcsncmp –**|\<String.h > nebo \<wchar.h >|
|**_mbsncmp –**, **_mbsncmp_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strncmp.c
#include <string.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n      %s\n      %s\n\n",
           string1, string2 );
   printf( "Function:   strncmp (first 10 characters only)\n" );
   result = strncmp( string1, string2 , 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n\n", tmp );
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );
   result = _strnicmp( string1, string2, 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
      The quick brown dog jumps over the lazy fox
      The QUICK brown fox jumps over the lazy dog

Function:   strncmp (first 10 characters only)
Result:      String 1 is greater than string 2

Function:   strnicmp _strnicmp (first 10 characters only)
Result:      String 1 is equal to string 2
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
