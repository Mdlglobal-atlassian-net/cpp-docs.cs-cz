---
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
ms.date: 4/2/2020
api_name:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
- _o__mbsncmp
- _o__mbsncmp_l
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
ms.openlocfilehash: deae95f8cf7d538dfe22ebbe0e86524765d9d234
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919319"
---
# <a name="strncmp-wcsncmp-_mbsncmp-_mbsncmp_l"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Porovnává až po zadaný počet znaků dvou řetězců.

> [!IMPORTANT]
> **_mbsncmp** a **_mbsncmp_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Řetězce, které se mají porovnat

*výpočtu*<br/>
Počet znaků, které mají být porovnány.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Návratová hodnota označuje vztah dílčích řetězců *řetězec1* a *řetězec2* následujícím způsobem.

|Návratová hodnota|Popis|
|------------------|-----------------|
|< 0|podřetězec *řetězec1* menší než *řetězec2* podřetězce|
|0|řetězec *řetězec1* shodný s podřetězcem *řetězec2*|
|> 0|podřetězec *řetězec1* větší než *řetězec2* podřetězce|

V případě chyby ověřování parametru **_mbsncmp** a **_mbsncmp_l** vrácení **_NLSCMPERROR**, které je definováno v \<řetězci. h> a \<Mbstring. h>.

## <a name="remarks"></a>Poznámky

Funkce **strncmp** provádí ordinální porovnání na nejvíce prvních *počtů* znaků v *řetězec1* a *řetězec2* a vrátí hodnotu, která označuje vztah mezi podřetězci. **strncmp** je verze **_strnicmp**citlivá na velká a malá písmena. **wcsncmp** a **_mbsncmp** jsou verze **_wcsnicmp** a **_mbsnicmp**rozlišující velká a malá písmena.

**wcsncmp** a **_mbsncmp** jsou verze **strncmp**pro velké znaky a vícebajtové znaky. Argumenty **wcsncmp** jsou řetězce s velkým počtem znaků; **_mbsncmp** jsou vícebajtové znakové řetězce. **_mbsncmp** rozpozná vícebajtové znakové sekvence podle vícebajtové znakové stránky a vrátí **_NLSCMPERROR** při chybě.

Také **_mbsncmp** a **_mbsncmp_l** ověřte parametry. Pokud je *řetězec1* nebo *řetězec2* ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **_mbsncmp** a **_mbsncmp_l** vrácení **_NLSCMPERROR** a nastavení **errno** na **EINVAL**. **strncmp** a **wcsncmp** neověřují své parametry. Tyto funkce se chovají identicky jinak.

Chování porovnání **_mbsncmp** a **_mbsncmp_l** je ovlivněno nastavením kategorie **LC_CTYPE** národního prostředí. Tato ovládací prvky detekuje úvodní a koncové bajty vícebajtových znaků. Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md). Funkce **_mbsncmp** používá aktuální národní prostředí pro toto chování závislé na národním prostředí. Funkce **_mbsncmp_l** je shodná s tím rozdílem, že místo toho používá parametr *národního prostředí* . Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md). Pokud je národní prostředí s jedním bajtem, chování těchto funkcí je stejné jako **strncmp**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp**|**strncmp**|**_mbsncmp**|**wcsncmp**|
|**_tcsncmp**|**strncmp**|**_mbsnbcmp**|**wcsncmp**|
|**_tccmp**|Mapuje se na makro nebo vloženou funkci.|**_mbsncmp**|Mapuje se na makro nebo vloženou funkci.|
|**nelze použít**|**nelze použít**|**_mbsncmp_l**|**nelze použít**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strncmp**|\<String. h>|
|**wcsncmp**|\<String. h> nebo \<WCHAR. h>|
|**_mbsncmp** **_mbsncmp_l**|\<Mbstring. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
