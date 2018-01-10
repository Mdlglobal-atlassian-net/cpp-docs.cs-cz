---
title: "ldexp – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: ldexp
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ldexp
- _ldexpl
dev_langs: C++
helpviewer_keywords:
- calculating real numbers
- computing real numbers
- mantissas, floating-point variables
- ldexp function
- exponent, floating-point numbers
- floating-point functions, mantissa and exponent
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a5e38d9a8df63fd4c2880fda7becec545c9584a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ldexp"></a>ldexp
Vynásobí celočíselný násobek dvou číslo s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double ldexp(  
   double x,  
   int exp   
);  
float ldexp(  
   float x,  
   int exp  
);  // C++ only  
long double ldexp(  
   long double x,  
   int exp  
);  // C++ only   
float ldexpf(  
   float x,  
   int exp  
);   
long double ldexpl(  
   long double x,  
   int exp  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota s plovoucí desetinnou čárkou.  
  
 `exp`  
 Exponent celé číslo.  
  
## <a name="return-value"></a>Návratová hodnota  
 `ldexp` Funkce vrátí hodnotu `x` * 2<sup>exp</sup> v případě úspěchu. Na přetečení a v závislosti na znaménko `x`, `ldexp` vrátí `HUGE_VAL`; `errno` nastavena na hodnotu `ERANGE`.  
  
 Další informace o `errno` a možná chyba návratové hodnoty, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `ldexp` trvají `float` nebo `long double` typy. V programu C `ldexp` má vždy `double` a `int` a vrátí `double`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Hlavička C|Hlavička C++|  
|-------------|--------------|------------------|  
|`ldexp`, `ldexpf`, `ldexpl`|\<Math.h >|\<cmath – >|  
  
 Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_ldexp.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 4.0, y;  
   int p = 3;  
  
   y = ldexp( x, p );  
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
4.0 times two to the power of 3 is 32.0  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [frexp –](../../c-runtime-library/reference/frexp.md)   
 [modf, modff, modfl](../../c-runtime-library/reference/modf-modff-modfl.md)