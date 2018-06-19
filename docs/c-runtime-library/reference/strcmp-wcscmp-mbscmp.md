---
title: strcmp – wcscmp –, _mbscmp – | Microsoft Docs
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
ms.openlocfilehash: df2168da257c6d1d07cff6400122830da60b5fef
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417442"
---
# <a name="strcmp-wcscmp-mbscmp"></a>strcmp, wcscmp, _mbscmp

Porovnávání řetězců.

> [!IMPORTANT]
> **_mbscmp –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězce ukončené hodnotou Null pro porovnání.

## <a name="return-value"></a>Návratová hodnota

Určuje pořadí vztah z návratovou hodnotu pro každou z těchto funkcí *řetězec1* k *řetězec2*.

|Hodnota|Relace řetězec1 k řetězec2|
|-----------|----------------------------------------|
|< 0|*řetězec1* je menší než *řetězec2*|
|0|*řetězec1* je stejný jako *řetězec2*|
|> 0|*řetězec1* je větší než *řetězec2*|

Parametr chyby ověření **_mbscmp –** vrátí **_NLSCMPERROR**, která je definována v \<string.h > a \<mbstring.h >.

## <a name="remarks"></a>Poznámky

**Strcmp –** funkce provádí porovnávání pomocí pořadového čísla *řetězec1* a *řetězec2* a vrátí hodnotu, která určuje jejich vztahu. **wcscmp –** a **_mbscmp –** , jsou široká charakterová a vícebajtových znaků verze **strcmp –**. **_mbscmp –** rozpozná sekvencí vícebajtových znaků podle aktuální vícebajtové znakové stránky a vrátí **_NLSCMPERROR** na chybu. Další informace najdete v tématu [znakové stránky](../../c-runtime-library/code-pages.md). Navíc pokud *řetězec1* nebo *řetězec2* je ukazatel s hodnotou null, **_mbscmp –** volá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **_mbscmp –** vrátí **_NLSCMPERROR** a nastaví **errno** k **einval –**. **strcmp –** a **wcscmp –** neověřují jejich parametrů. Tyto tři funkce chovají stejně jako jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp –**|**strcmp –**|**_mbscmp**|**wcscmp –**|

**Strcmp –** funkce liší od **strcoll –** funkce v tom, že **strcmp –** porovnání se podle pořadového čísla a nemá vliv národního prostředí. **strcoll –** porovná řetězce lexicographically pomocí **lc_collate –** kategorii aktuální národní prostředí. Další informace o **lc_collate –** kategorie, najdete v části [setlocale _wsetlocale](setlocale-wsetlocale.md).

Pořadí znaky znakové sady (znaková sada ASCII) v národním prostředí "C", je stejná jako pořadí lexicographic znaků. V jiným národním prostředím, ale pořadí znaků ve znakové sadě může lišit od lexicographic pořadí. Například v některých evropských národní prostředí znak "a" (hodnota 0x61) zaslána před znak 'č. (hodnota 0xE4) v znaková sada, ale znak 'č' dodává před znak "a" lexicographically.

V národní prostředí, pro které se liší znakovou sadu a znak lexicographic pořadí, můžete použít **strcoll –** místo **strcmp –** lexicographic porovnání řetězců. Alternativně můžete použít **strxfrm –** na původní řetězce a pak použít **strcmp –** výsledné řetězce.

**Strcmp –** funkce jsou malá a velká písmena. **_stricmp –**, **_wcsicmp –**, a **_mbsicmp –** porovnávání řetězců první převede do formulářů malá písmena. Dva řetězce, které obsahují znaky, které se nachází mezi 'Z' a 'a' v tabulce ASCII ('[','\\', ']', ' ^', '_', a '\`') porovnat odlišně, v závislosti na jejich případě. Například dva řetězce "ABCDE" a "ABCD ^" porovnat jedním ze způsobů, je-li porovnání malá písmena ("abcde" > "abcd ^") a jiným způsobem ("ABCDE" < "ABCD ^") je-li porovnání velká písmena.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strcmp –**|< string.h >|
|**wcscmp –**|< string.h > nebo < wchar.h >|
|**_mbscmp**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také

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
