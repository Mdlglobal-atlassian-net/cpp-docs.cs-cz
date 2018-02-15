---
title: 'Besselovy funkce: _j0, _j1, _jn, _y0, _y1, _yn | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
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
- c.bessel
- _j0
- _j1
- _jn
- _y0
- _y1
- _yn
dev_langs:
- C++
helpviewer_keywords:
- Bessel functions
- _j0 function
- _j1 function
- _jn function
- _y0 function
- _y1 function
- _yn function
ms.assetid: a21a8bf1-df9d-4ba0-a8c2-e7ef71921d96
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6a31388bdf629ed1a133eaf91f715360b020319
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="bessel-functions-j0-j1-jn-y0-y1-yn"></a>Besselovy funkce: _j0, _j1, _jn, _y0, _y1, _yn
Vypočítá Besselovy funkce první nebo druhé druh, objednávky 0, 1 nebo n. Besselovy funkce se běžně používají v Matematika z teoreticky elektromagnetických wave.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double _j0(   
   double x   
);  
double _j1(   
   double x   
);  
double _jn(   
   int n,  
   double x   
);  
double _y0(   
   double x   
);  
double _y1(   
   double x   
);  
double _yn(   
   int n,  
   double x   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota s plovoucí desetinnou čárkou.  
  
 `n`  
 Besselovy funkce pořadí celé číslo.  
  
## <a name="return-value"></a>Návratová hodnota  
 Všechny tyto rutiny vrátí Besselovy funkce `x`. Pokud `x` záporné v `_y0`, `_y1`, nebo `_yn` funkce, rutiny nastaví `errno` k `EDOM`, vytiskne `_DOMAIN` chybovou zprávu `stderr`a vrátí `_HUGE_VAL`. Můžete upravit pomocí zpracování chyb `_matherr`.  
  
## <a name="remarks"></a>Poznámky  
 `_j0`, `_j1`, A `_jn` rutiny vrátí Besselovy funkce první druhu: řadí 0, 1, n, v uvedeném pořadí.  
  
|Vstup|Výjimka SEH|Matherr – výjimka|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|`INVALID`|`_DOMAIN`|  
  
 `_y0`, `_y1`, A `_yn` rutiny vrátí Besselovy funkce druhého typu: řadí 0, 1, n, v uvedeném pořadí.  
  
|Vstup|Výjimka SEH|Matherr – výjimka|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|`INVALID`|`_DOMAIN`|  
|± 0|`ZERODIVIDE`|`_SING`|  
|&#124;x&#124;<0.0|`INVALID`|`_DOMAIN`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_j0`, `_j1`, `_jn`, `_y0`, `_y1`, `_yn`|\<cmath – > (C++), \<math.h > (C, C++)|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_bessel1.c  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.387;  
   int n = 3, c;  
  
   printf( "Bessel functions for x = %f:\n", x );  
   printf( " Kind   Order  Function     Result\n\n" );  
   printf( " First  0      _j0( x )     %f\n", _j0( x ) );  
   printf( " First  1      _j1( x )     %f\n", _j1( x ) );  
   for( c = 2; c < 5; c++ )  
      printf( " First  %d      _jn( %d, x )  %f\n", c, c, _jn( c, x ) );  
   printf( " Second 0      _y0( x )     %f\n", _y0( x ) );  
   printf( " Second 1      _y1( x )     %f\n", _y1( x ) );  
   for( c = 2; c < 5; c++ )  
      printf( " Second %d      _yn( %d, x )  %f\n", c, c, _yn( c, x ) );  
}  
```  
  
```Output  
Bessel functions for x = 2.387000:  
 Kind   Order  Function     Result  
  
 First  0      _j0( x )     0.009288  
 First  1      _j1( x )     0.522941  
 First  2      _jn( 2, x )  0.428870  
 First  3      _jn( 3, x )  0.195734  
 First  4      _jn( 4, x )  0.063131  
 Second 0      _y0( x )     0.511681  
 Second 1      _y1( x )     0.094374  
 Second 2      _yn( 2, x )  -0.432608  
 Second 3      _yn( 3, x )  -0.819314  
 Second 4      _yn( 4, x )  -1.626833  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [_matherr](../../c-runtime-library/reference/matherr.md)