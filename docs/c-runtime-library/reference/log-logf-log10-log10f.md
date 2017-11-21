---
title: "protokol, logf –, log10, log10f – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- log10f
- logf
- log10
- log
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
- logf
- _log10l
- log
- _logl
- log10f
- log10
dev_langs: C++
helpviewer_keywords:
- calculating logarithms
- log10f function
- log10 function
- log function
- logf function
- logarithms
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8146d4ebe041fa3419aff3614edcd8fe9fa8b8d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="log-logf-log10-log10f"></a>log, logf, log10, log10f
Vypočítá logaritmů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      double log(  
   double x   
);  
float log(  
   float x  
);  // C++ only  
long double log(  
   long double x  
);  // C++ only  
float logf(  
   float x   
);  
double log10(  
   double x  
);  
float log10(  
   float x  
);  // C++ only  
long double log10(  
   long double x  
);  // C++ only  
float log10f (  
   float x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 Hodnota, jejíž logaritmus má být nalezen.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Protokolu** funkce vrátí přirozený logaritmus (se základem e) *x* v případě úspěchu. Funkce log10 Vrátí logaritmus o základu 10. Pokud *x* je záporná, vrátí tyto funkce dobu neurčitou, ve výchozím nastavení. Pokud *x* je 0, že budou vracet INF (nekonečné).  
  
|Vstup|Výjimka SEH|Matherr – výjimka|  
|-----------|-------------------|-----------------------|  
|ROZMEZÍ QNAN, IND|žádná|_DOMAIN –|  
|± 0|ZERODIVIDE|–|  
|x < 0|NEPLATNÝ|_DOMAIN –|  
  
 **protokol** a `log10` má implementace, která používá Streaming SIMD Extensions 2 (SSE2). V tématu [_set_sse2_enable –](../../c-runtime-library/reference/set-sse2-enable.md) informace a omezení používání SSE2 implementace.  
  
## <a name="remarks"></a>Poznámky  
 C++ umožňuje přetížení, takže můžete volat přetížení **protokolu** a `log10`. V programu C **protokolu** a `log10` vždy přijmout a vrátit datový typ double.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|**protokol**, `logf`, `log10`,`log10f`|\<Math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_log.c  
/* This program uses log and log10  
 * to calculate the natural logarithm and  
 * the base-10 logarithm of 9,000.  
 */  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 9000.0;  
   double y;  
  
   y = log( x );  
   printf( "log( %.2f ) = %f\n", x, y );  
   y = log10( x );  
   printf( "log10( %.2f ) = %f\n", x, y );  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
log( 9000.00 ) = 9.104980  
log10( 9000.00 ) = 3.954243  
```  
  
 Chcete-li vygenerovat logaritmů u jiných základů, použijte matematický vztah: protokolu základní b == přirozené protokolu (a) / přirozené protokolu (b).  
  
```  
// logbase.cpp  
#include <math.h>  
#include <stdio.h>  
  
double logbase(double a, double base)  
{  
   return log(a) / log(base);  
}  
  
int main()  
{  
   double x = 65536;  
   double result;  
  
   result = logbase(x, 2);  
   printf("Log base 2 of %lf is %lf\n", x, result);  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
Log base 2 of 65536.000000 is 16.000000  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [Exp, expf –, expl](../../c-runtime-library/reference/exp-expf.md)   
 [_matherr –](../../c-runtime-library/reference/matherr.md)   
 [Pow – powf – powl –](../../c-runtime-library/reference/pow-powf-powl.md)   
 [_Cilog –](../../c-runtime-library/cilog.md)   
 [_Cilog10 –](../../c-runtime-library/cilog10.md)