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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 805e355fe12cb2f7ead6180edd45ad0748570141
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920380"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp, wcscmp, _mbscmp, _mbscmp_l

Porovnejte řetězce.

> [!IMPORTANT]
> **_mbscmp** a **_mbscmp_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězec zakončený hodnotou null k porovnání

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota pro každou z těchto funkcí označuje ordinální relaci *řetězec1* do *řetězec2*.

|Hodnota|Vztah řetězec1 k řetězec2|
|-----------|----------------------------------------|
|< 0|*řetězec1* je menší než *řetězec2*|
|0|*řetězec1* je totožný s *řetězec2*|
|> 0|*řetězec1* je větší než *řetězec2*|

V případě chyby ověřování parametru **_mbscmp** a **_mbscmp_l** vrácení **_NLSCMPERROR**, které je definováno v \<řetězci. h> a \<Mbstring. h>.

## <a name="remarks"></a>Poznámky

Funkce **strcmp** provede ordinální porovnání hodnot *řetězec1* a *řetězec2* a vrátí hodnotu, která označuje jejich relaci. **wcscmp** a **_mbscmp** jsou, v uvedeném pořadí, verze **strcmp**a vícebajtových znaků. **_mbscmp** rozpozná vícebajtové znakové sekvence podle aktuální vícebajtové znakové stránky a vrátí **_NLSCMPERROR** při chybě. **_mbscmp_l** má stejné chování, ale používá předaný parametr národního prostředí namísto aktuálního národního prostředí. Další informace najdete v tématu [znakové stránky](../../c-runtime-library/code-pages.md). Také, pokud je *řetězec1* nebo *řetězec2* ukazatel s hodnotou null, **_mbscmp** vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **_mbscmp** a **_mbscmp_l** vrácení **_NLSCMPERROR** a nastavení **errno** na **EINVAL**. **strcmp** a **wcscmp** neověřují své parametry. Tyto funkce se chovají identicky jinak.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

Funkce **strcmp** se liší od funkcí **strcoll –** v tom, že porovnání **strcmp** jsou ordinální a nejsou ovlivněny národním prostředím. **strcoll –** porovná řetězce lexikograficky pomocí kategorie **LC_COLLATE** aktuálního národního prostředí. Další informace o kategorii **LC_COLLATE** naleznete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md).

V národním prostředí "C" je pořadí znaků ve znakové sadě (znaková sada ASCII) stejné jako pořadí znaků lexikografickým pořadím. V jiných národních prostředích se však pořadí znaků v sadě znaků může lišit od pořadí lexikografickým pořadím. Například v určitých evropských národních prostředích se znak "a" (hodnota 0x61) nachází před znakem "ä" (0xE4) ve znakové sadě, ale znak "ä" přichází před znakem "a" lexikograficky.

V národních prostředích, pro která se liší znaková sada a lexikografickým pořadím znaků, můžete použít **strcoll –** namísto **strcmp** pro lexikografickým pořadím porovnávání řetězců. Alternativně můžete použít **strxfrm** na původní řetězce a potom použít **strcmp** na výsledných řetězcích.

Funkce **strcmp** rozlišují velká a malá písmena. stricmp, ** \_wcsicmp**a ** \_mbsicmp** porovnávají řetězce, a to tak, že je nejdříve převedete na jejich tvary malých písmen. ** \_** Dva řetězce, které obsahují znaky, které jsou umístěné mezi ' Z ' a ' a ' v tabulce ASCII (' [',\\', '] ', ' ^ ', ' _ ' a '\`') porovnat odlišně v závislosti na jejich velikosti. Například dva řetězce "ABCDE" a "ABCD ^" porovnávají jeden ze způsobů, pokud je porovnávání malými písmeny ("abcde" > "abcd ^") a druhým způsobem ("ABCDE" < "ABCD ^"), pokud je porovnání velká.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strcmp**|\<String. h>|
|**wcscmp**|\<String. h> nebo \<WCHAR. h>|
|**_mbscmp**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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
