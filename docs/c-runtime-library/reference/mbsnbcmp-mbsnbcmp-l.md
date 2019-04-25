---
title: _mbsnbcmp, _mbsnbcmp_l
ms.date: 11/04/2016
apiname:
- _mbsnbcmp
- _mbsnbcmp_l
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
apitype: DLLExport
f1_keywords:
- mbsnbcmp
- tcsnbmp
- _mbsnbcmp_l
- mbsnbcmp_l
- _mbsnbcmp
helpviewer_keywords:
- mbsnbcmp_l function
- mbsnbcmp function
- tcsncmp function
- _mbsnbcmp_l function
- _tcsncmp function
- _mbsnbcmp function
ms.assetid: dbc99e50-cf85-4e57-a13f-067591f18ac8
ms.openlocfilehash: 4b21fde122f9804633ac037efaf1f343b5cb9440
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285301"
---
# <a name="mbsnbcmp-mbsnbcmpl"></a>_mbsnbcmp, _mbsnbcmp_l

Porovnává první z nich **n** bajtů dvou vícebajtových znakových řetězců.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*string1*, *string2*<br/>
Řetězce k porovnání.

*Počet*<br/>
Počet bajtů k porovnání.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota označuje ordinální vztah mezi podřetězci *řetězec1* a *řetězec2*.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|*řetězec1* dílčí řetězec je menší než *řetězec2* dílčí řetězec.|
|0|*řetězec1* se shoduje s podřetězcem *řetězec2* dílčí řetězec.|
|> 0|*řetězec1* je větší než podřetězec *řetězec2* dílčí řetězec.|

Na chybu ověření parametru **_mbsnbcmp –** a **_mbsnbcmp_l –** vrátit **_NLSCMPERROR**, který je definován v \<string.h > a \< Mbstring.h >.

## <a name="remarks"></a>Poznámky

**_Mbsnbcmp –** funkce porovnání nanejvýš prvních *počet* bajtů *řetězec1* a *řetězec2* a vrací hodnotu, která označuje vztah mezi podřetězci. **_mbsnbcmp –** je velká a malá písmena verze **_mbsnbicmp –**. Na rozdíl od **_mbsnbcoll –**, **_mbsnbcmp –** není ovlivněno pořadím řazení národního prostředí. **_mbsnbcmp –** rozpozná vícebajtové znakové sekvence podle aktuální vícebajtovou [znaková stránka](../../c-runtime-library/code-pages.md).

**_mbsnbcmp –** se podobá **_mbsncmp –**, s tím rozdílem, že **_mbsncmp –** porovná řetězce podle znaků, nikoli podle bajtů.

Výstupní hodnota je ovlivněna **LC_CTYPE** kategorie nastavení národního prostředí, která určuje počet bajtů potenciálních zákazníků a koncové bajty vícebajtových znaků. Další informace najdete v tématu [setlocale](setlocale-wsetlocale.md). **_Mbsnbcmp –** funkce používá aktuální národní prostředí pro toto chování závislé na národním prostředí. **_Mbsnbcmp_l –** funkce je totožný s tím rozdílem, že používá *národní prostředí* parametr místo. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *řetězec1* nebo *řetězec2* je ukazatel s hodnotou null, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce **_NLSCMPERROR** a **errno** je nastavena na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|---------------------------------------|--------------------|-----------------------|
|**_tcsncmp**|[strncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|**_mbsnbcmp**|[wcsncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|
|**_tcsncmp_l**|[strncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|**_mbsnbcml**|[wcsncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcmp**|\<Mbstring.h >|
|**_mbsnbcmp_l**|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_mbsnbcmp.c
#include <mbstring.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n          %s\n", string1 );
   printf( "          %s\n\n", string2 );
   printf( "Function: _mbsnbcmp (first 10 characters only)\n" );
   result = _mbsncmp( string1, string2 , 10 );
   if( result > 0 )
      _mbscpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      _mbscpy_s( tmp, sizeof(tmp), "less than" );
   else
      _mbscpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:   String 1 is %s string 2\n\n", tmp );
   printf( "Function: _mbsnicmp _mbsnicmp (first 10 characters only)\n" );
   result = _mbsnicmp( string1, string2, 10 );
   if( result > 0 )
      _mbscpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      _mbscpy_s( tmp, sizeof(tmp), "less than" );
   else
      _mbscpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:   String 1 is %s string 2\n\n", tmp );
}
```

### <a name="output"></a>Výstup

```Output
Compare strings:
          The quick brown dog jumps over the lazy fox
          The QUICK brown fox jumps over the lazy dog

Function: _mbsnbcmp (first 10 characters only)
Result:   String 1 is greater than string 2

Function: _mbsnicmp _mbsnicmp (first 10 characters only)
Result:   String 1 is equal to string 2
```

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
