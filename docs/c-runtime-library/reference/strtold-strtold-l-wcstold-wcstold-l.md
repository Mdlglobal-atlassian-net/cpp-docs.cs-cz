---
title: strtold, _strtold_l, wcstold, _wcstold_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
dev_langs: C++
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3ff8aa3f62a50ae544de61953054bd8906ed5971
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strtold-strtoldl-wcstold-wcstoldl"></a>strtold, _strtold_l, wcstold, _wcstold_l
Převede řetězce na hodnotu s plovoucí desetinnou čárkou dlouho dvojitou přesností.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long double strtold(  
   const char *nptr,  
   char **endptr   
);  
long double _strtold_l(  
   const char *nptr,  
   char **endptr,  
   _locale_t locale  
);  
long double wcstold(  
   const wchar_t *nptr,  
   wchar_t **endptr   
);  
long double wcstold_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nptr`  
 Řetězce ukončené hodnotou Null pro převod.  
  
 `endptr`  
 Ukazatel na znak, který zastaví kontroly.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 `strtold`Vrátí hodnotu číslo s plovoucí desetinnou čárkou jako `long double`, s výjimkou případů, kdy reprezentace by způsobilo přetečení – v takovém případě funkce vrátí hodnotu`HUGE_VALL`. Znaménko `HUGE_VALL` odpovídá znaménko hodnotu, která není možné vyjádřit. `strtold`Vrátí hodnotu 0, pokud žádný převod můžete provést, nebo dojde podtečení.  
  
 `wcstold`Vrátí hodnoty analogicky na `strtold`. Pro obě funkce `errno` je nastaven na `ERANGE` Pokud dojde k přetečení nebo podtečení a volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).  
  
 Další informace o návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Jednotlivé funkce převede vstupní řetězec `nptr` k `long double`. `strtold` Funkce převede `nptr` na hodnotu dlouho dvojitou přesností. `strtold`ukončí čtení řetězce `nptr` u prvního znaku nemůže rozpoznat jako součást číslo. To může být ukončující znak hodnoty null. Široká charakterová verzi `strtold` je `wcstold`; jeho `nptr` je argumentem široká charakterová řetězce. Tyto funkce, jinak hodnota chovají stejně jako.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstold`|`strtold`|`strtold`|`wcstold`|  
|`_tcstold_l`|`_strtold_l`|`_strtold_l`|`_wcstold_l`|  
  
 `LC_NUMERIC` Kategorie nastavení aktuální národní prostředí určuje rozpoznávání základ – znak v `nptr`. Další informace najdete v tématu [setlocale _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). Funkce bez `_l` příponu použít aktuální národní prostředí; `_strtold_l` a `_wcstold_l` jsou stejné jako `_strtold` a `_wcstold` s tím rozdílem, že místo toho používají národní prostředí, je předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Pokud `endptr` není `NULL`, ukazatel na znak, který zastavena kontroly je uložený v umístění, které ukazuje `endptr`. Pokud žádný převod lze provést (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základní), hodnota `nptr` je uložený v umístění, které ukazuje `endptr`.  
  
 `strtold`očekává `nptr` tak, aby odkazoval na řetězec v následujícím formátu:  
  
 [`whitespace`] [`sign`] [`digits`] [`.digits`] [ {`d` &#124; `D` &#124; `e` &#124; `E`}[`sign`]`digits`]  
  
 A `whitespace` může obsahovat místa a karta znaků, které se mají ignorovat; `sign` je buď plus (`+`) nebo minus (`-`); a `digits` jsou jeden nebo více desetinných míst. Pokud před základ – znak, který se zobrazí žádné číslice, alespoň jeden musí být uvedena za základ – znak. Desetinných míst může následovat exponentem, který se skládá z úvodní písmeno (`d`, `D`, `e`, nebo `E`) a volitelně znaménkem. Pokud exponentu část ani základ – znak zobrazí, předpokládá se základ – znak podle poslední číslice v řetězci. První znak, který se nevejde tento formulář zastaví kontroly.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strtold`, `_strtold_l`|\<stdlib.h >|  
|`wcstold`, `_wcstold_l`|\<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_strtold.c  
// Build with: cl /W4 /Tc crt_strtold.c  
// This program uses strtold to convert a  
// string to a long double-precision value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *string;  
   char *stopstring;  
   long double x;  
  
   string = "3.1415926535898This stopped it";  
   x = strtold(string, &stopstring);  
   printf("string = %s\n", string);  
   printf("   strtold = %.13Lf\n", x);  
   printf("   Stopped scan at: %s\n\n", stopstring);  
}  
```  
  
```Output  
string = 3.1415926535898This stopped it  
   strtold = 3.1415926535898  
   Stopped scan at: This stopped it  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Funkce řetězců na číselné hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod –, _strtod_l –, wcstod –, _wcstod_l –](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol –, wcstol –, _strtol_l –, _wcstol_l –](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul –, _strtoul_l –, wcstoul –, _wcstoul_l –](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof –, _atof_l –, _wtof –, _wtof_l –](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [localeconv –](../../c-runtime-library/reference/localeconv.md)   
 [_create_locale –, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale –](../../c-runtime-library/reference/free-locale.md)