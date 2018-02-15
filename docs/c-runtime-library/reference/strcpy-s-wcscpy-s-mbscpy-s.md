---
title: "strcpy_s – wcscpy_s –, _mbscpy_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- wcscpy_s
- _mbscpy_s
- strcpy_s
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strcpy_s
- _mbscpy_s
- _tcscpy_s
- wcscpy_s
dev_langs:
- C++
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cdb37fe985340d2126cfc6f8db90cc236a2d5870
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="strcpys-wcscpys-mbscpys"></a>strcpy_s, wcscpy_s, _mbscpy_s
Zkopíruje řetězec. Tyto verze nástroje [strcpy – wcscpy –, _mbscpy –](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  `_mbscpy_s` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t strcpy_s(  
   char *strDestination,  
   size_t numberOfElements,  
   const char *strSource   
);  
errno_t wcscpy_s(  
   wchar_t *strDestination,  
   size_t numberOfElements,  
   const wchar_t *strSource   
);  
errno_t _mbscpy_s(  
   unsigned char *strDestination,  
   size_t numberOfElements,  
   const unsigned char *strSource   
);  
template <size_t size>  
errno_t strcpy_s(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
errno_t wcscpy_s(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
errno_t _mbscpy_s(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `strDestination`  
 Umístění cílové vyrovnávací paměti řetězců.  
  
 `numberOfElements`  
 Velikost cílové vyrovnávací paměti řetězců v `char` jednotky úzké a vícebajtové funkce, a `wchar_t` jednotky pro celou funkce.  
  
 `strSource`  
 Vyrovnávací paměť řetězce ukončené hodnotou Null zdroje.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěšného; jinak k chybě.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`strDestination`|`numberOfElements`|`strSource`|Návratová hodnota|Obsah `strDestination`|  
|----------------------|------------------------|-----------------|------------------|----------------------------------|  
|`NULL`|všechny|všechny|`EINVAL`|nedojde ke změně|  
|všechny|všechny|`NULL`|`EINVAL`|`strDestination`[0] nastaven na 0|  
|všechny|0, nebo příliš malá|všechny|`ERANGE`|`strDestination`[0] nastaven na 0|  
  
## <a name="remarks"></a>Poznámky  
 `strcpy_s` Funkce zkopíruje obsah v adresu `strSource`, včetně ukončující znak hodnoty null do umístění, která je zadána `strDestination`. Cílový řetězec musí být dostatečně velký pro uložení zdrojový řetězec a jeho ukončovací znak hodnoty null. Chování `strcpy_s` není definován, pokud se překrývají zdrojové a cílové řetězce.  
  
 `wcscpy_s` je verze široká charakterová `strcpy_s`, a `_mbscpy_s` je verze vícebajtových znaků. Argumenty a vrací hodnotu `wcscpy_s` jsou široká charakterová řetězce; u `_mbscpy_s` jsou řetězců vícebajtových znaků. Tyto tři funkce chovají stejně jako jinak.  
  
 Pokud `strDestination` nebo `strSource` je ukazatel s hodnotou null, nebo pokud cílový řetězec je příliš malá, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `EINVAL` a nastavte `errno` k `EINVAL` při `strDestination` nebo `strSource` je ukazatel s hodnotou null, a že budou vracet `ERANGE` a nastavte `errno` k `ERANGE` Pokud cílový řetězec je příliš malá.  
  
 Po úspěšné provedení cílový řetězec je vždy ukončené hodnotou null.  
  
 V jazyce C++ těchto funkcí se zjednodušilo díky šabloně přetížení, které lze odvodit délka vyrovnávací paměti automaticky tak, že nemusíte určit velikost argument a starší, méně bezpečné funkce můžou automaticky nahradit s jejich novější bezpečnější svými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
 Ladicí verze těchto funkcí nejprve vyplnit vyrovnávací paměť s Bugcheck 0xFE. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcscpy_s`|`strcpy_s`|`_mbscpy_s`|`wcscpy_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strcpy_s`|\<String.h >|  
|`wcscpy_s`|\<String.h > nebo \<wchar.h >|  
|`_mbscpy_s`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_strcpy_s.cpp  
// This program uses strcpy_s and strcat_s  
// to build a phrase.  
//  
  
#include <string.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   char string[80];  
   // using template versions of strcpy_s and strcat_s:  
   strcpy_s( string, "Hello world from " );  
   strcat_s( string, "strcpy_s " );  
   strcat_s( string, "and " );  
   // of course we can supply the size explicitly if we want to:  
   strcat_s( string, _countof(string), "strcat_s!" );  
  
   printf( "String = %s\n", string );  
}  
```  
  
```Output  
String = Hello world from strcpy_s and strcat_s!  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [strcat, wcscat, _mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)   
 [strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy_s –, _strncpy_s_l –, wcsncpy_s –, _wcsncpy_s_l –, _mbsncpy_s, _mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)