---
title: "lround –, lroundf –, lroundl –, llround –, llroundf –, llroundl – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- llround
- llroundf
- llroundl
- lroundf
- lround
- lroundl
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
- lround
- lroundl
- llroundl
- llround
- lroundf
- llroundf
dev_langs: C++
helpviewer_keywords:
- lround function
- llroundl function
- llround function
- lroundf function
- llroundf function
- lroundl function
ms.assetid: cfb88a35-54c6-469f-85af-f7d695dcfdd8
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 596d1d40043fceb9a75549a460776b5b7d9de552
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="lround-lroundf-lroundl-llround-llroundf-llroundl"></a>lround, lroundf, lroundl, llround, llroundf, llroundl
Zaokrouhlí na nejbližší celé číslo s plovoucí desetinnou čárkou hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long lround(   
   double x   
);  
long lround(  
   float x  
);  // C++ only  
long lround(  
   long double x  
);  // C++ only  
long lroundf(  
   float x  
);  
long lroundl(  
   long double x  
);  
long long llround(   
   double x   
);  
long long llround(  
   float x  
);  // C++ only  
long long llround(  
   long double x  
);  // C++ only  
long long llroundf(  
   float x  
);  
long long llroundl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota s plovoucí desetinnou čárkou má být zaokrouhleno.  
  
## <a name="return-value"></a>Návratová hodnota  
 `lround` a `llround` funkce vrátit na nejbližší `long` nebo `long long` celého `x`. Uprostřed hodnoty jsou zaokrouhleny směrem od nuly, bez ohledu na nastavení režimu zaokrouhlení s plovoucí desetinnou čárkou. Neexistuje žádný návratový chyby.  
  
|Vstup|Výjimka SEH|Matherr – výjimka|  
|-----------|-------------------|-----------------------|  
|± `QNAN`, `IND`|žádná|`_DOMAIN`|  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `lround` nebo `llround` , přijmout a vrátit `float` a `long double` hodnoty. V programu C `lround` a `llround` vždy přijmout a vrátit `double`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`lround`, `lroundf`, `lroundl`, `llround`, `llroundf`, `llroundl`|\<Math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_lround.c  
// Build with: cl /W3 /Tc crt_lround.c  
// This example displays the rounded results of  
// the floating-point values 2.499999, -2.499999,   
// 2.8, -2.8, 3.5 and -3.5.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.499999;  
   float y = 2.8f;  
   long double z = 3.5;  
  
   printf("lround(%f) is %d\n", x, lround(x));  
   printf("lround(%f) is %d\n", -x, lround(-x));  
   printf("lroundf(%f) is %d\n", y, lroundf(y));  
   printf("lroundf(%f) is %d\n", -y, lroundf(-y));  
   printf("lroundl(%Lf) is %d\n", z, lroundl(z));  
   printf("lroundl(%Lf) is %d\n", -z, lroundl(-z));  
}  
```  
  
```Output  
lround(2.499999) is 2  
lround(-2.499999) is -2  
lroundf(2.800000) is 3  
lroundf(-2.800000) is -3  
lroundl(2.500000) is 4  
lroundl(-2.500000) is -4  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [ceil, ceilf –, ceill –](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [Floor, floorf –, floorl –](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod, fmodf –](../../c-runtime-library/reference/fmod-fmodf.md)   
 [lrint, lrintf, lrintl, llrint, llrintf, llrintl](http://msdn.microsoft.com/en-us/312fd869-a9c0-4107-bb23-ab8299d04385)   
 [Round, roundf –, roundl –](../../c-runtime-library/reference/round-roundf-roundl.md)   
 [nearbyint – nearbyintf –, nearbyintl](http://msdn.microsoft.com/en-us/15111e73-331d-41d1-81b7-3e10df894848)   
 [tisknout, rintf, rintl](../../c-runtime-library/reference/rint-rintf-rintl.md)