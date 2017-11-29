---
title: "strcpy – wcscpy –, _mbscpy – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strcpy
- wcscpy
- _mbscpy
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
- _mbscpy
- _ftcscpy
- wcscpy
- _tcscpy
- strcpy
dev_langs: C++
helpviewer_keywords:
- strcpy function
- tcscpy function
- ftcscpy function
- mbscpy function
- wcscpy function
- copying strings
- strings [C++], copying
- _tcscpy function
- _ftcscpy function
- _mbscpy function
ms.assetid: f97a4f81-e9ee-4f15-888a-0fa5d7094c5a
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 466565dcb957e98efccc9f2037f98c869775e36f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strcpy-wcscpy-mbscpy"></a>strcpy, wcscpy, _mbscpy
Zkopíruje řetězec. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [strcpy_s – wcscpy_s –, _mbscpy_s –](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md).  
  
> [!IMPORTANT]
>  `_mbscpy`nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *strcpy(  
   char *strDestination,  
   const char *strSource   
);  
wchar_t *wcscpy(  
   wchar_t *strDestination,  
   const wchar_t *strSource   
);  
unsigned char *_mbscpy(  
   unsigned char *strDestination,  
   const unsigned char *strSource   
);  
template <size_t size>  
char *strcpy(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
wchar_t *wcscpy(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
unsigned char *_mbscpy(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `strDestination`  
 Cílový řetězec.  
  
 `strSource`  
 Řetězce ukončené hodnotou Null zdroje.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí cílový řetězec. Žádnou návratovou hodnotu je vyhrazena indikující chybu.  
  
## <a name="remarks"></a>Poznámky  
 `strcpy` Funkce kopie `strSource`, včetně ukončující znak hodnoty null do umístění, která je zadána `strDestination`. Chování `strcpy` není definován, pokud se překrývají zdrojové a cílové řetězce.  
  
> [!IMPORTANT]
>  Protože `strcpy` nekontroluje dostatek místa v `strDestination` před kopíruje `strSource`, je potenciální příčinou přetečení vyrovnávací paměti. Proto doporučujeme použít [strcpy_s –](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) místo.  
  
 `wcscpy`a `_mbscpy` , jsou široká charakterová a vícebajtových znaků verze `strcpy`. Argumenty a vrací hodnotu `wcscpy` jsou široká charakterová řetězce; u `_mbscpy` jsou řetězců vícebajtových znaků. Tyto tři funkce chovají stejně jako jinak.  
  
 V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcscpy`|`strcpy`|`_mbscpy`|`wcscpy`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strcpy`|\<String.h >|  
|`wcscpy`|\<String.h > nebo \<wchar.h >|  
|`_mbscpy`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_strcpy.c  
// compile with: /W3  
// This program uses strcpy  
// and strcat to build a phrase.  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[80];  
  
   // If you change the previous line to  
   //   char string[20];  
   // strcpy and strcat will happily overrun the string  
   // buffer.  See the examples for strncpy and strncat  
   // for safer string handling.  
  
   strcpy( string, "Hello world from " ); // C4996  
   // Note: strcpy is deprecated; use strcpy_s instead  
   strcat( string, "strcpy " );           // C4996  
   // Note: strcat is deprecated; use strcat_s instead  
   strcat( string, "and " );              // C4996  
   strcat( string, "strcat!" );           // C4996  
   printf( "String = %s\n", string );  
}  
```  
  
```Output  
String = Hello world from strcpy and strcat!  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [strcat – wcscat –, _mbscat –](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncat –, _strncat_l, wcsncat –, _wcsncat_l, _mbsncat –, _mbsncat_l –](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l –](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy –, _strncpy_l –, wcsncpy –, _wcsncpy_l –, _mbsncpy –, _mbsncpy_l –](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [_strnicmp –, _wcsnicmp –, _mbsnicmp –, _strnicmp_l –, _wcsnicmp_l –, _mbsnicmp_l –](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr –, wcsrchr –, _mbsrchr –, _mbsrchr_l –](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn –, wcsspn –, _mbsspn –, _mbsspn_l –](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)