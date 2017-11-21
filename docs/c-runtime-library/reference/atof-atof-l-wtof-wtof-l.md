---
title: "atof –, _atof_l –, _wtof –, _wtof_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wtof_l
- atof
- _atof_l
- _wtof
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
- _tstof
- _ttof
- atof
- stdlib/atof
- math/atof
- _atof_l
- stdlib/_atof_l
- math/_atof_l
- _wtof
- corecrt_wstdlib/_wtof
- _wtof_l
- corecrt_wstdlib/_wtof_l
dev_langs: C++
helpviewer_keywords:
- tstof function
- atof_l function
- _atof_l function
- atof function
- _tstof function
- _ttof function
- wtof function
- _wtof_l function
- ttof function
- wtof_l function
- _wtof function
- string conversion, to floating point values
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72c6538cea2b1eaca61615a8b2db9041aa1eb74b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atof-atofl-wtof-wtofl"></a>atof, _atof_l, _wtof, _wtof_l
Převeďte řetězec na hodnotu double.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double atof(  
   const char *str   
);  
double _atof_l(  
   const char *str,  
   _locale_t locale  
);  
double _wtof(  
   const wchar_t *str   
);  
double _wtof_l(  
   const wchar_t *str,  
   _locale_t locale  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `str`  
 Řetězec, který má být převeden.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jednotlivé funkce vrátí `double` hodnotu vyprodukované interpretace vstupu znaky jako číslo. Vrácená hodnota je 0,0, pokud vstupní nelze převést na hodnotu typu.  
  
 Ve všech případech out-of-range, kód chyby je nastavena na `ERANGE`. Pokud parametr byl předán v `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí 0.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce převést znakového řetězce na hodnotu Dvojitá přesnost, s plovoucí desetinnou čárkou.  
  
 Vstupní řetězec je posloupnost znaků, které lze interpretovat jako hodnotu zadaného typu. Funkce zastaví čtení vstupní řetězec u prvního znaku, který nelze rozpoznat jako součást číslo. Tento znak může být znak hodnoty null ('\0' nebo L '\0') ukončující řetězec.  
  
 `str` Argument `atof` a `_wtof` má následující formát:  
  
 [`whitespace`] [`sign`] [`digits`] [`.digits`] [ {`e` &#124; `E` }[`sign`]`digits`]  
  
 A `whitespace` se skládá z místa nebo kartě znaků, které se mají ignorovat; `sign` je buď plus (+) nebo minus (-) a `digits` jsou jeden nebo více desetinných míst. Pokud se zobrazí bez číslic od desetinné čárky, alespoň jeden musí být uvedena za desetinnou čárkou. Desetinných míst může následovat exponentem, který se skládá z úvodní písmeno (`e`, nebo `E`) a volitelně podepsaný desítkové celé číslo.  
 
 Verze UCRT tyto funkce nepodporuje převod Fortran stylu (`d` nebo `D`) exponentu písmena. Toto nestandardní rozšíření byl podporován ve starších verzích CRT a může být narušující změně kódu.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstof`|`atof`|`atof`|`_wtof`|  
|`_ttof`|`atof`|`atof`|`_wtof`|  
  
## <a name="requirements"></a>Požadavky  
  
|Routine(s)|Požadovaný hlavičkový soubor|  
|------------------|---------------------|  
|`atof`, `_atof_l`|C: \<math.h > nebo \<stdlib.h > C++: \<cstdlib – >, \<stdlib.h >, \<cmath – > nebo \<math.h >|  
|`_wtof`, `_wtof_l`|C: \<stdlib.h > nebo \<wchar.h > C++: \<cstdlib – >, \<stdlib.h > nebo \<wchar.h >|  
  
## <a name="example"></a>Příklad  
 Tento program ukazuje, jak lze převést čísla uložená jako řetězce do číselných hodnot pomocí `atof` a `_atof_l` funkce.  
  
```C  
// crt_atof.c  
//  
// This program shows how numbers stored as   
// strings can be converted to numeric  
// values using the atof and _atof_l functions.  

#include <stdlib.h>  
#include <stdio.h>  
#include <locale.h>  

int main(void)
{
    char    *str = NULL;
    double value = 0;
    _locale_t fr = _create_locale(LC_NUMERIC, "fr-FR");

    // An example of the atof function  
    // using leading and training spaces.  
    str = "  3336402735171707160320 ";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // Another example of the atof function  
    // using the 'E' exponential formatting keyword.  
    str = "3.1412764583E210";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // An example of the atof and _atof_l functions  
    // using the 'e' exponential formatting keyword  
    // and showing different decimal point interpretations.  
    str = "  -2,309e-25";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);
    value = _atof_l(str, fr);
    printf("Function: _atof_l(\"%s\", fr)) = %e\n", str, value);
}  
```  
  
```Output  
Function: atof("  3336402735171707160320 ") = 3.336403e+21
Function: atof("3.1412764583E210") = 3.141276e+210
Function: atof("  -2,309e-25") = -2.000000e+00
Function: _atof_l("  -2,309e-25", fr)) = -2.309000e-25  
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