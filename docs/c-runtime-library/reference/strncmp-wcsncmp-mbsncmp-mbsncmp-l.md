---
title: "strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d3baca7feae2b45c7761e46daa4adeb7a0968580
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strncmp-wcsncmp-mbsncmp-mbsncmpl"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
Porovná až do zadaného počtu znaků dva řetězce.  
  
> [!IMPORTANT]
>  `_mbsncmp`a `_mbsncmp_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `string1, string2`  
 Řetězce k porovnání.  
  
 `count`  
 Počet znaků, které mají být porovnány.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota označuje vztah podřetězce `string1` a `string2` následujícím způsobem.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|< 0|`string1`substring menší než `string2` dílčí řetězec|  
|0|`string1`substring identické `string2` dílčí řetězec|  
|> 0|`string1`substring větší než `string2` dílčí řetězec|  
  
 Parametr chyby ověření `_mbsncmp` a `_mbsncmp_l` vrátit `_NLSCMPERROR`, která je definována v \<string.h > a \<mbstring.h >.  
  
## <a name="remarks"></a>Poznámky  
 `strncmp` Funkce provádí ordinální porovnávání maximálně prvního `count` znaky v `string1` a `string2` a vrátí hodnotu, která určuje vztah mezi dílčích řetězců. `strncmp`je malá a velká písmena verze `_strnicmp`. `wcsncmp`a `_mbsncmp` se malá a velká písmena verzích `_wcsnicmp` a `_mbsnicmp`.  
  
 `wcsncmp`a `_mbsncmp` jsou široká charakterová a vícebajtových znaků verze `strncmp`. Argumenty `wcsncmp` jsou široká charakterová řetězce; u `_mbsncmp` jsou řetězců vícebajtových znaků. `_mbsncmp`rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky a vrátí `_NLSCMPERROR` na chybu.  
  
 Navíc `_mbsncmp` a `_mbsncmp_l` ověřte parametry. Pokud `string1` nebo `string2` je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `_mbsncmp` a `_mbsncmp_l` vrátit `_NLSCMPERROR` a nastavte `errno` k `EINVAL`. `strncmp`a `wcsncmp` neověřují jejich parametrů. Tyto funkce chovají stejně jako jinak.  
  
 Porovnání chování `_mbsncmp` a `_mbsncmp_l` je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí. Tato volba určuje detekce úvodní a koncové bajtů více-bajtové znaky. Další informace najdete v tématu [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). `_mbsncmp` Funkce používá aktuální národní prostředí pro toto chování závislých na národním prostředí. `_mbsncmp_l` Funkce se shoduje s tím rozdílem, že se používá `locale` parametr místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md). Pokud národní prostředí je národní prostředí jednobajtové, chování těchto funkcí je stejný jako `strncmp`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsnccmp`|`strncmp`|`_mbsncmp`|`wcsncmp`|  
|`_tcsncmp`|`strncmp`|`_mbsnbcmp`|`wcsncmp`|  
|`_tccmp`|Mapuje makro nebo vložené funkce|`_mbsncmp`|Mapuje makro nebo vložené funkce|  
|**není k dispozici**|**není k dispozici**|`_mbsncmp_l`|**není k dispozici**|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strncmp`|\<String.h >|  
|`wcsncmp`|\<String.h > nebo \<wchar.h >|  
|`_mbsncmp`, `_mbsncmp_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
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
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbsnbcmp –, _mbsnbcmp_l –](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [_mbsnbicmp –, _mbsnbicmp_l –](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll – funkce](../../c-runtime-library/strcoll-functions.md)   
 [_strnicmp –, _wcsnicmp –, _mbsnicmp –, _strnicmp_l –, _wcsnicmp_l –, _mbsnicmp_l –](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr –, wcsrchr –, _mbsrchr –, _mbsrchr_l –](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset –, _strset_l –, _wcsset –, _wcsset_l –, _mbsset –, _mbsset_l –](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn –, wcsspn –, _mbsspn –, _mbsspn_l –](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)