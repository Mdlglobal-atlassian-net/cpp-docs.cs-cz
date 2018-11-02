---
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
ms.date: 11/04/2016
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
ms.openlocfilehash: b8b5472289bacc940bb0cbea7876f246243660bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523761"
---
# <a name="strncmp-wcsncmp-mbsncmp-mbsncmpl"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Porovná až do zadaného počtu znaků dva řetězce.

> [!IMPORTANT]
> **_mbsncmp –** a **_mbsncmp_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota označuje vztah mezi podřetězci *řetězec1* a *řetězec2* následujícím způsobem.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|*řetězec1* podřetězec menší než *řetězec2* dílčí řetězec|
|0|*řetězec1* podřetězec shodný s *řetězec2* dílčí řetězec|
|> 0|*řetězec1* větší než podřetězec *řetězec2* dílčí řetězec|

Na chybu ověření parametru **_mbsncmp –** a **_mbsncmp_l –** vrátit **_NLSCMPERROR**, který je definován v \<string.h > a \< Mbstring.h >.

## <a name="remarks"></a>Poznámky

**Strncmp –** funkce provádí řadové porovnání nanejvýš prvních *počet* znaky v *řetězec1* a *řetězec2* a Vrátí hodnotu, která označuje vztah mezi podřetězci. **strncmp –** je velká a malá písmena verze **_strnicmp –**. **wcsncmp –** a **_mbsncmp –** jsou malá a velká písmena verze **_wcsnicmp –** a **_mbsnicmp –**.

**wcsncmp –** a **_mbsncmp –** jsou širokoznaké a vícebajtové verze **strncmp –**. Argumenty **wcsncmp –** jsou širokoznaké řetězce **_mbsncmp –** jsou vícebajtové znakové řetězce. **_mbsncmp –** rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránce a vrátí **_NLSCMPERROR** v případě chyby.

Navíc **_mbsncmp –** a **_mbsncmp_l –** ověřte parametry. Pokud *řetězec1* nebo *řetězec2* je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **_mbsncmp –** a **_mbsncmp_l –** vrátit **_NLSCMPERROR** a nastavte **errno** k  **EINVAL**. **strncmp –** a **wcsncmp –** neověří jejich parametry. Tyto funkce chovají identicky jinak.

Chování porovnání **_mbsncmp –** a **_mbsncmp_l –** je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí. Tato volba určuje detekce úvodní a koncové bajty vícebajtových znaků. Další informace najdete v tématu [setlocale](setlocale-wsetlocale.md). **_Mbsncmp –** funkce používá aktuální národní prostředí pro toto chování závislé na národním prostředí. **_Mbsncmp_l –** funkce je totožný s tím rozdílem, že používá *národní prostředí* parametr místo. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md). Pokud se národní prostředí je národní prostředí jednobajtové, chování těchto funkcí je stejný jako **strncmp –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp –**|**strncmp –**|**_mbsncmp**|**wcsncmp –**|
|**_tcsncmp –**|**strncmp –**|**_mbsnbcmp**|**wcsncmp –**|
|**_tccmp**|Mapuje se na makro nebo vloženou funkci|**_mbsncmp**|Mapuje se na makro nebo vloženou funkci|
|**Není k dispozici**|**Není k dispozici**|**_mbsncmp_l**|**Není k dispozici**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strncmp –**|\<String.h >|
|**wcsncmp –**|\<String.h > nebo \<wchar.h >|
|**_mbsncmp –**, **_mbsncmp_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

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
