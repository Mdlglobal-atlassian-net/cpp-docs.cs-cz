---
title: strcmp, wcscmp, _mbscmp, _mbscmp_l
ms.date: 4/2/2020
api_name:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
- _o__mbscmp
- _o__mbscmp_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscmp
- _mbscmp_l
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- _mbscmp_l function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
ms.openlocfilehash: 16bb294f7bbdc0b95b59b845d7b714f823f9d962
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357289"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp, wcscmp, _mbscmp, _mbscmp_l

Porovnejte řetězce.

> [!IMPORTANT]
> **_mbscmp** a **_mbscmp_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
int _mbscmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*řetězec1*, *řetězec2*<br/>
Řetězce ukončené hodnotou null k porovnání.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota pro každou z těchto funkcí označuje řadový vztah *string1* k *string2*.

|Hodnota|Vztah string1 a string2|
|-----------|----------------------------------------|
|< 0|*string1* je menší než *string2*|
|0|*string1* je shodný s *string2*|
|> 0|*string1* je větší než *string2*|

Při chybě ověření parametru **_mbscmp** a **_mbscmp_l** vrátí \< **_NLSCMPERROR**, který je definován v souborech string.h> a \<mbstring.h>.

## <a name="remarks"></a>Poznámky

Funkce **strcmp** provádí řadové porovnání *string1* a *string2* a vrátí hodnotu, která označuje jejich vztah. **wcscmp** a **_mbscmp** jsou, respektive, široký-znak a multibyte-znak verze **strcmp**. **_mbscmp** rozpoznává vícebajtové sekvence znaků podle aktuální znakové stránky vícebajtů a vrací **_NLSCMPERROR** na chybu. **_mbscmp_l** má stejné chování, ale používá parametr národního prostředí, který je předán namísto aktuálního národního prostředí. Další informace naleznete v [tématu Code Pages](../../c-runtime-library/code-pages.md). Také pokud *string1* nebo *string2* je ukazatel null, **_mbscmp** vyvolá neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je umožněno pokračovat v provádění, **_mbscmp** a **_mbscmp_l** vrátí **_NLSCMPERROR** a nastavte **errno** na **EINVAL**. **strcmp** a **wcscmp** neověřují své parametry. Tyto funkce se chovají stejně jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

Funkce **strcmp** se liší od **strcoll** funkcí v tom, že **porovnání strcmp** jsou ordinální a nejsou ovlivněny národním prostředím. **strcoll** porovnává řetězce lexicographically pomocí **LC_COLLATE** kategorie aktuálního národního prostředí. Další informace o **kategorii LC_COLLATE** naleznete v [tématu setlocale, _wsetlocale](setlocale-wsetlocale.md).

V národním prostředí "C" je pořadí znaků v znakové sadě (znaková sada ASCII) stejné jako lexikografické pořadí znaků. V jiných národních prostředích se však pořadí znaků v znakové sadě může lišit od lexikografického pořadí. Například v některých evropských národních prostředích znak 'a' (hodnota 0x61) předchází znaku 'ä' (hodnota 0xE4) v znakové sadě, ale znak 'ä' je před znakem 'a' lexicographically.

V národních prostředích, pro která se liší znaková sada a lexikografické pořadí znaků, můžete použít **strcoll** namísto **strcmp** pro lexikografické porovnání řetězců. Alternativně můžete použít **strxfrm** na původní řetězce a pak použít **strcmp** na výsledné řetězce.

Funkce **strcmp** rozlišují malá a velká písmena. stricmp , ** \_wcsicmp**a ** \_mbsicmp** porovnávají řetězce tím, že je nejprve převedou na jejich malé tvary. ** \_** Dva řetězce, které obsahují znaky, které jsou umístěny mezi "Z" a 'a' v tabulce ASCII ('[', ', ',\\',]', ^', '', '' a '\`) porovnat odlišně, v závislosti na jejich případu. Například dva řetězce "ABCDE" a "ABCD^" porovnat jedním způsobem, pokud je porovnání malá písmena ("abcde" > "abcd^") a jiným způsobem ("ABCDE" < "ABCD^"), pokud je porovnání velká písmena.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strcmp**|\<string.h>|
|**wcscmp**|\<string.h> \<nebo wchar.h>|
|**_mbscmp**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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
