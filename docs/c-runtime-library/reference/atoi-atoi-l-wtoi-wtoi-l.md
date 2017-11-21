---
title: "atoi –, _atoi_l –, _wtoi –, _wtoi_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wtoi
- _wtoi_l
- atoi
- _atoi_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tstoi
- _wtoi
- _ttoi
- atoi
- _atoi_l
- _wtoi_l
dev_langs: C++
helpviewer_keywords:
- _atoi_l function
- ttoi function
- atoi_l function
- string conversion, to integers
- _wtoi function
- wtoi_l function
- tstoi function
- _ttoi function
- _tstoi function
- _wtoi_l function
- atoi function
- wtoi function
ms.assetid: ad7fda30-28ab-421f-aaad-ef0b8868663a
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c23ba6cc06e06a6c1f6ad43cb7bc833494aaba60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atoi-atoil-wtoi-wtoil"></a>atoi, _atoi_l, _wtoi, _wtoi_l
Převeďte řetězec na celé číslo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int atoi(  
   const char *str   
);  
int _wtoi(  
   const wchar_t *str   
);  
int _atoi_l(  
   const char *str,  
   _locale_t locale  
);  
int _wtoi_l(  
   const wchar_t *str,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Řetězec, který má být převeden.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jednotlivé funkce vrátí `int` hodnotu vyprodukované interpretace vstupu znaky jako číslo. Vrácená hodnota je 0 pro `atoi` a `_wtoi`, pokud vstupní nelze převést na hodnotu daného typu.  
  
 V případě přetečení s velké záporné celočíselné hodnoty `LONG_MIN` je vrácen. `atoi`a `_wtoi` vrátit `INT_MAX` a `INT_MIN` na těchto podmínkách. Ve všech případech out-of-range `errno` je nastaven na `ERANGE`. Pokud parametr byl předán v `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí 0.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce převést řetězec znaků na celočíselnou hodnotu (`atoi` a `_wtoi`). Vstupní řetězec je posloupnost znaků, které lze interpretovat jako hodnotu zadaného typu. Funkce zastaví čtení vstupní řetězec u prvního znaku, který nelze rozpoznat jako součást číslo. Tento znak může být znak hodnoty null ('\0' nebo L '\0') ukončující řetězec.  
  
 `str` Argument `atoi` a `_wtoi` má následující formát:  
  
 [`whitespace`] [`sign`] [`digits`]]  
  
 A `whitespace` se skládá z místa nebo kartě znaků, které se mají ignorovat; `sign` je buď plus (+) nebo minus (-) a `digits` jsou jeden nebo více číslic.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstoi`|`atoi`|`atoi`|`_wtoi`|  
|`_ttoi`|`atoi`|`atoi`|`_wtoi`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutiny|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`atoi`|\<stdlib.h >|  
|`_atoi_l`, `_wtoi`, `_wtoi_l`|\<stdlib.h > nebo \<wchar.h >|  
  
## <a name="example"></a>Příklad  
 Tento program ukazuje, jak lze převést čísla uložená jako řetězce do číselných hodnot pomocí `atoi` funkce.  
  
```  
// crt_atoi.c  
// This program shows how numbers   
// stored as strings can be converted to  
// numeric values using the atoi functions.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    int     value = 0;  
  
    // An example of the atoi function.  
    str = "  -2309 ";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atoi function.  
    str = "31412764";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atoi function   
    // with an overflow condition occuring.  
    str = "3336402735171707160320";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
```Output  
Function: atoi( "  -2309 " ) = -2309  
Function: atoi( "31412764" ) = 31412764  
Function: atoi( "3336402735171707160320" ) = 2147483647  
Overflow condition occurred.  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [_ecvt –](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt –](../../c-runtime-library/reference/fcvt.md)   
 [_gcvt –](../../c-runtime-library/reference/gcvt.md)   
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_atodbl –, _atodbl_l –, _atoldbl –, _atoldbl_l –, _atoflt –, _atoflt_l –](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)