---
title: "modf – modff –, modfl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- modff
- modf
- modfl
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
dev_langs:
- C++
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9744b82cd14d29234fabf1edbe379c2c5d14ac85
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="modf-modff-modfl"></a>modf – modff –, modfl
Rozdělí do desetinnou hodnotu s plovoucí desetinnou čárkou a částí celé číslo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double modf(  
   double x,  
   double * intptr   
);  
float modf(  
   float x,  
   float * intptr  
);  // C++ only  
long double modf(  
   long double x,  
   long double * intptr  
);  // C++ only  
float modff(  
   float x,  
   float * intptr   
);  
long double modfl(  
   long double x,  
   long double * intptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 Hodnota s plovoucí desetinnou čárkou.  
  
 `intptr`  
 Ukazatel na uložené celočíselnou část.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato funkce vrátí podepsaný zlomkové části *x*. Neexistuje žádný návratový chyby.  
  
## <a name="remarks"></a>Poznámky  
 `modf` Funkce rozdělení s plovoucí desetinnou čárkou `x` do zlomkové části celé číslo, z nichž každá má stejné znaménko jako a `x`. Podepsaný zlomkové části `x` je vrácen. Celočíselnou část je uložený jako hodnotu s plovoucí desetinnou čárkou v `intptr.`  
  
 `modf` má implementace, která používá Streaming SIMD Extensions 2 (SSE2). V tématu [_set_sse2_enable –](../../c-runtime-library/reference/set-sse2-enable.md) informace a omezení používání SSE2 implementace.  
  
 C++ umožňuje přetížení, takže můžete volat přetížení `modf` , přijmout a vrátit `float` nebo `long double` parametry. V programu C `modf` vždy má dvě hodnoty double a vrátí hodnotu double.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`modf`, `modff`, `modfl`|C: \<math.h ><br /><br /> C++:, \<cmath – > nebo \<math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_modf.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x, y, n;  
  
   x = -14.87654321;      /* Divide x into its fractional */  
   y = modf( x, &n );     /* and integer parts            */  
  
   printf( "For %f, the fraction is %f and the integer is %.f\n",   
           x, y, n );  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
For -14.876543, the fraction is -0.876543 and the integer is -14  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)