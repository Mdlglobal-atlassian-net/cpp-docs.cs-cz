---
title: "fmod, fmodf – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fmod
- fmodf
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
- fmod
- _fmodl
- fmodf
dev_langs: C++
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 53c191639222df29d8a1101d4ebfa7ea44377f48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fmod-fmodf"></a>fmod, fmodf
Vypočítá zbytek s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double fmod(   
   double x,  
   double y   
);  
float fmod(  
   float x,  
   float y   
);  // C++ only  
long double fmod(  
   long double x,  
   long double y  
);  // C++ only  
float fmodf(   
   float x,  
   float y   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`, `y`  
 Hodnoty s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 `fmod`Vrátí s plovoucí desetinnou čárkou zbytek `x`  /  `y`. Pokud hodnota `y` je 0,0, `fmod` vrátí quiet NaN. Informace o reprezentace quiet NaN pomocí `printf` rodiny, viz [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
## <a name="remarks"></a>Poznámky  
 `fmod` Funkce vypočítá s plovoucí desetinnou čárkou zbývající `f` z `x`  /  `y` tak, aby `x`  =  `i` `*` `y`  +  `f`, kde `i` je celé číslo, `f` má stejné znaménko jako `x`a absolutní hodnotu `f` je menší než absolutní hodnotu `y`.  
  
 C++ umožňuje přetížení, takže můžete volat přetížení `fmod`. V programu C `fmod` vždy přebírá dva hodnoty Double a vrátí hodnotu typu double.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`fmod`, `fmodf`|\<Math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fmod.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = fmod( w, x );  
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );  
}  
```  
  
```Output  
The remainder of -10.00 / 3.00 is -1.000000  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [ceil, ceilf –, ceill –](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [fabs, fabsf –, fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [Floor, floorf –, floorl –](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [_CIfmod](../../c-runtime-library/cifmod.md)