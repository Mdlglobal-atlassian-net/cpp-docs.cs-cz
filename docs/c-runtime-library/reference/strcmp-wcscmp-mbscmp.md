---
title: strcmp – wcscmp –, _mbscmp – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcscmp
- _mbscmp
- strcmp
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _mbscmp
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
dev_langs:
- C++
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca1591bba9518b1b5f6122f51bf60f5a23fc7a26
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44319003"
---
# <a name="strcmp-wcscmp-mbscmp"></a>strcmp, wcscmp, _mbscmp

Porovnávání řetězců.

> [!IMPORTANT]
> **_mbscmp –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int strcmp(
   const char *string1,
   const char *string2
);
int wcscmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscmp(
   const unsigned char *string1,
   const unsigned char *string2
);
```

### <a name="parameters"></a>Parametry

*řetězec1*, *řetězec2*<br/>
Řetězec zakončený hodnotou Null pro srovnání.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota pro každou z těchto funkcí označuje ordinální vztah *řetězec1* k *řetězec2*.

|Hodnota|Vztah řetězec1 k řetězec2|
|-----------|----------------------------------------|
|< 0|*řetězec1* je menší než *řetězec2*|
|0|*řetězec1* je stejný jako *řetězec2*|
|> 0|*řetězec1* je větší než *řetězec2*|

Na chybu ověření parametru **_mbscmp –** vrátí **_NLSCMPERROR**, který je definován v \<string.h > a \<mbstring.h >.

## <a name="remarks"></a>Poznámky

**Strcmp –** funkce provádí řadové porovnání z *řetězec1* a *řetězec2* a vrátí hodnotu, která určuje jejich vzájemný vztah. **wcscmp –** a **_mbscmp –** , jsou širokoznaké a vícebajtové verze **strcmp –**. **_mbscmp –** rozpozná vícebajtové znakové sekvence podle aktuální vícebajtové znakové stránce a vrátí **_NLSCMPERROR** v případě chyby. Další informace najdete v tématu [znakové stránky](../../c-runtime-library/code-pages.md). Navíc pokud *řetězec1* nebo *řetězec2* je ukazatel s hodnotou null, **_mbscmp –** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **_mbscmp –** vrátí **_NLSCMPERROR** a nastaví **errno** k **EINVAL**. **strcmp –** a **wcscmp –** neověří jejich parametry. Tyto tři funkce chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp –**|**strcmp –**|**_mbscmp**|**wcscmp –**|

**Strcmp –** funkce se liší od **strcoll –** funkce v dané **strcmp –** porovnání podle pořadového čísla jsou a nejsou ovlivněná národním prostředím. **strcoll –** lexikograficky porovná řetězce pomocí **LC_COLLATE** kategorie aktuálního národního prostředí. Další informace o **LC_COLLATE** kategorie, naleznete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md).

Pořadí znaků ve znakové sadě (znaková sada ASCII) v národním prostředí "C", je stejné jako pořadí lexikografických znaků. V ostatních národních prostředí, ale pořadí znaků ve znakové sadě může lišit od lexikografické pořadí. Například v některých evropských národní prostředí, znak "a" (hodnota 0x61) předchází znak "č. (hodnota 0xE4) v znakové sady, ale před znak"č' obsahuje znak "a" lexicographically.

V prostředí, pro které se liší znakové sady a lexikografickým pořadím znaků, můžete použít **strcoll –** místo **strcmp –** pro lexikografického porovnání řetězců. Alternativně můžete použít **strxfrm –** na původním řetězců a pak použijte **strcmp –** na výsledného řetězce.

**Strcmp –** funkce jsou malá a velká písmena. **_stricmp –**, **_wcsicmp –**, a **_mbsicmp –** porovnávání řetězců převedením první na malá písmena formuláře. Dva řetězce, které obsahují znaky umístěné mezi "Z" a "a" v tabulce ASCII ('[','\\","] "," ^ ","_"a"\`") porovnávají různě v závislosti na velikosti jejich písmen. Například dva řetězce "ABCDE" a "ABCD ^" porovnávají jeden ze způsobů, pokud je výsledkem porovnávání malá písmena ("abcde" > "abcd ^") a jiným způsobem ("ABCDE" < "ABCD ^") je-li porovnání velká písmena.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strcmp –**|\<String.h >|
|**wcscmp –**|\<String.h > nebo \<wchar.h >|
|**_mbscmp**|\<Mbstring.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_strcmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof (tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
