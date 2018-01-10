---
title: "strcmp – wcscmp –, _mbscmp – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
apitype: DLLExport
f1_keywords:
- _mbscmp
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
dev_langs: C++
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
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f133027b2f1e7dfef494baeed9df6e9e56447889
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="strcmp-wcscmp-mbscmp"></a>strcmp, wcscmp, _mbscmp
Porovnávání řetězců.  
  
> [!IMPORTANT]
>  `_mbscmp`nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `string1`, `string2`  
 Řetězce ukončené hodnotou Null pro porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Určuje pořadí vztah z návratovou hodnotu pro každou z těchto funkcí `string1` k `string2`.  
  
|Hodnota|Relace řetězec1 k řetězec2|  
|-----------|----------------------------------------|  
|< 0|`string1`je menší než`string2`|  
|0|`string1`je stejný jako`string2`|  
|> 0|`string1`je větší než`string2`|  
  
 Parametr chyby ověření `_mbscmp` vrátí `_NLSCMPERROR`, která je definována v \<string.h > a \<mbstring.h >.  
  
## <a name="remarks"></a>Poznámky  
 `strcmp` Funkce provádí porovnávání pomocí pořadového čísla `string1` a `string2` a vrátí hodnotu, která určuje jejich vztahu. `wcscmp`a `_mbscmp` , jsou široká charakterová a vícebajtových znaků verze `strcmp`. `_mbscmp`rozpozná sekvencí vícebajtových znaků podle aktuální vícebajtové znakové stránky a vrátí `_NLSCMPERROR` na chybu. Další informace najdete v tématu [znakové stránky](../../c-runtime-library/code-pages.md). Navíc pokud `string1` nebo `string2` je ukazatel s hodnotou null, `_mbscmp` volá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `_mbscmp` vrátí `_NLSCMPERROR` a nastaví `errno` k `EINVAL`. `strcmp`a `wcscmp` neověřují jejich parametrů. Tyto tři funkce chovají stejně jako jinak.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcscmp`|`strcmp`|`_mbscmp`|`wcscmp`|  
  
 `strcmp` Funkce liší od `strcoll` funkce v tom, že `strcmp` porovnání se podle pořadového čísla a nemá vliv národního prostředí. `strcoll`Porovná řetězce lexicographically pomocí `LC_COLLATE` kategorii aktuální národní prostředí. Další informace o `LC_COLLATE` kategorie, najdete v části [setlocale _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 Pořadí znaky znakové sady (znaková sada ASCII) v národním prostředí "C", je stejná jako pořadí lexicographic znaků. V jiným národním prostředím, ale pořadí znaků ve znakové sadě může lišit od lexicographic pořadí. Například v některých evropských národní prostředí znak "a" (hodnota 0x61) zaslána před znak 'č. (hodnota 0xE4) v znaková sada, ale znak 'č' dodává před znak "a" lexicographically.  
  
 V národní prostředí, pro které se liší znakovou sadu a znak lexicographic pořadí, můžete použít `strcoll` místo `strcmp` lexicographic porovnání řetězců. Alternativně můžete použít `strxfrm` na původní řetězce a pak použít `strcmp` výsledné řetězce.  
  
 `strcmp` Funkce jsou malá a velká písmena. `_stricmp`, `_wcsicmp`, a `_mbsicmp` porovnávání řetězců první převede do formulářů malá písmena. Dva řetězce, které obsahují znaky, které se nachází mezi 'Z' a 'a' v tabulce ASCII ('[','`\`', '] ','`^`','`_`', a s ') porovnat odlišně, v závislosti na jejich případě. Například dva řetězce `"ABCDE"` a `"ABCD^"` porovnání jedním ze způsobů, pokud je výsledkem porovnávání je malá písmena (`"abcde"` > `"abcd^"`) a jiným způsobem (`"ABCDE"` < `"ABCD^"`) Pokud je výsledkem porovnávání velká písmena.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strcmp`|< string.h >|  
|`wcscmp`|< string.h > nebo < wchar.h >|  
|`_mbscmp`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
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
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [memcmp wmemcmp –](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [_memicmp –, _memicmp_l –](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [strcoll – funkce](../../c-runtime-library/strcoll-functions.md)   
 [_stricmp –, _wcsicmp –, _mbsicmp –, _stricmp_l –, _wcsicmp_l –, _mbsicmp_l –](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l –](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp –, _wcsnicmp –, _mbsnicmp –, _strnicmp_l –, _wcsnicmp_l –, _mbsnicmp_l –](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr –, wcsrchr –, _mbsrchr –, _mbsrchr_l –](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn –, wcsspn –, _mbsspn –, _mbsspn_l –](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)