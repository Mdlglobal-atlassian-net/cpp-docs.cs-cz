---
title: "strpbrk –, wcspbrk –, _mbspbrk –, _mbspbrk_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbspbrk
- wcspbrk
- _mbspbrk_l
- strpbrk
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
- _fstrpbrk
- _mbspbrk
- strpbrk
- _tcspbrk
- _ftcspbrk
- wcspbrk
dev_langs: C++
helpviewer_keywords:
- fstrpbrk function
- _ftcspbrk function
- _mbspbrk_l function
- strpbrk function
- _fstrpbrk function
- mbspbrk function
- characters [C++], scanning strings
- _tcspbrk function
- wcspbrk function
- ftcspbrk function
- character sets [C++], scanning strings for characters
- strings [C++], scanning
- tcspbrk function
- _mbspbrk function
- mbspbrk_l function
ms.assetid: 80b504f7-a167-4dde-97ad-4ae3000dc810
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aef34a8cddfde1088c8535a1835b157146400faa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strpbrk-wcspbrk-mbspbrk-mbspbrkl"></a>strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l
Kontroluje řetězců znaků v zadané znakových sad.  
  
> [!IMPORTANT]
>  `_mbspbrk`a `_mbspbrk_l` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *strpbrk(  
   const char *str,  
   const char *strCharSet   
); // C only  
char *strpbrk(  
   char *str,  
   const char *strCharSet   
); // C++ only  
const char *strpbrk(  
   const char *str,  
   const char *strCharSet   
); // C++ only  
wchar_t *wcspbrk(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
); // C only  
wchar_t *wcspbrk(  
   wchar_t *str,  
   const wchar_t *strCharSet   
); // C++ only  
const wchar_t *wcspbrk(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
); // C++ only  
unsigned char *_mbspbrk(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
); // C only  
unsigned char *_mbspbrk(  
   unsigned char *str,  
   const unsigned char *strCharSet   
); // C++ only  
const unsigned char *_mbspbrk(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
); // C++ only  
unsigned char *_mbspbrk_l(  
   const unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
); // C only  
unsigned char *_mbspbrk_l(  
   unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbspbrk_l(  
   const unsigned char *str,  
   const unsigned char* strCharSet,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Řetězce ukončené hodnotou Null, vyhledávaná.  
  
 `strCharSet`  
 Ukončené hodnotou Null znakovou sadu.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na první výskyt libovolný znak z `strCharSet` v `str`, nebo `NULL` ukazatele, pokud dva řetězcové argumenty mají společný žádné znaky.  
  
## <a name="remarks"></a>Poznámky  
 `strpbrk` Funkce vrací ukazatel na první výskyt znaku v `str` který patří do sady znaků v `strCharSet`. Hledání nezahrnuje ukončující znak hodnoty null.  
  
 `wcspbrk`a `_mbspbrk` jsou široká charakterová a vícebajtových znaků verze `strpbrk`. Argumenty a vrací hodnotu `wcspbrk` jsou široká charakterová řetězce; u `_mbspbrk` jsou řetězců vícebajtových znaků.  
  
 `_mbspbrk`ověří jeho parametry. Pokud `str` nebo `strCharSet` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `_mbspbrk` vrátí `NULL` a nastaví `errno` k `EINVAL`. `strpbrk`a `wcspbrk` neověřují jejich parametrů. Tyto tři funkce chovají stejně jako jinak.  
  
 `_mbspbrk`je podobná `_mbscspn` s tím rozdílem, že `_mbspbrk` vrátí ukazatel, nikoli hodnotu typu [size_t –](../../c-runtime-library/standard-types.md).  
  
 V jazyce C, proveďte tyto funkce `const` pro první argument ukazatel. V jazyce C++ jsou k dispozici dva přetížení. Přetížení trvá ukazatel na `const` vrací ukazatel na `const`; na verzi, která přebírá ukazatel na jinou hodnotu než`const` vrací ukazatel na jinou hodnotu než`const`. Makro `_CRT_CONST_CORRECT_OVERLOADS` je definována, pokud obě `const` a jiných-`const` verze tyto funkce jsou k dispozici. Pokud budete potřebovat jinou hodnotu než`const` chování pro obě přetížení C++ definujte symbol `_CONST_RETURN`.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; Další informace najdete v části [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). Verze tyto funkce bez `_l` použijte příponu aktuální národní prostředí pro toto chování závislých na národním prostředí; a verzí s `_l` přípona se shoduje s tím rozdílem, že používá parametr národního prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|  
|**není k dispozici**|**není k dispozici**|`_mbspbrk_l`|**není k dispozici**|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strpbrk`|\<String.h >|  
|`wcspbrk`|\<String.h > nebo \<wchar.h >|  
|`_mbspbrk`, `_mbspbrk_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_strpbrk.c  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[100] = "The 3 men and 2 boys ate 5 pigs\n";  
   char *result = NULL;  
  
   // Return pointer to first digit in "string".  
   printf( "1: %s\n", string );  
   result = strpbrk( string, "0123456789" );  
   printf( "2: %s\n", result++ );  
   result = strpbrk( result, "0123456789" );  
   printf( "3: %s\n", result++ );  
   result = strpbrk( result, "0123456789" );  
   printf( "4: %s\n", result );  
}  
```  
  
```Output  
1: The 3 men and 2 boys ate 5 pigs  
  
2: 3 men and 2 boys ate 5 pigs  
  
3: 2 boys ate 5 pigs  
  
4: 5 pigs  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn –, wcscspn –, _mbscspn –, _mbscspn_l –](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strchr –, wcschr –, _mbschr –, _mbschr_l –](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)   
 [strrchr –, wcsrchr –, _mbsrchr –, _mbsrchr_l –](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)