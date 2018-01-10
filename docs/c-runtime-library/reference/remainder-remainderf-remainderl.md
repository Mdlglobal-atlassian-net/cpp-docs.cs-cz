---
title: "zbývající, remainderf –, remainderl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
dev_langs: C++
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a0da3e4a6e785b73ebf2bfb8a529581d52dcfe2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="remainder-remainderf-remainderl"></a>remainder, remainderf, remainderl
Vypočítá zbytek podíl dvou hodnot s plovoucí desetinnou čárkou, zaokrouhlí na nejbližší hodnotu integrálu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double remainder(   
   double numer,  
   double denom  
);  
float remainder(   
   float numer,  
   float denom  
); /* C++ only */  
long double remainder(   
   long double numer,  
   long double denom  
); /* C++ only */  
float remainderf(   
   float numer,  
   float denom  
);  
long double remainderl(   
   long double numer,  
   long double denom  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `numer`  
 Čítači.  
  
 `denom`  
 Jmenovatel.  
  
## <a name="return-value"></a>Návratová hodnota  
 S plovoucí desetinnou čárkou zbytek `x`  /  `y`. Pokud hodnota `y` je 0,0, `remainder` vrátí quiet NaN. Informace o reprezentace quiet NaN pomocí `printf` rodiny, viz [printf _printf_l –, wprintf, _wprintf_l –](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
## <a name="remarks"></a>Poznámky  
 `remainder` Funkce vypočítá s plovoucí desetinnou čárkou zbývající `r` z `x`  /  `y` tak, aby `x`  =  `n`  *  `y`  +  `r`, kde `n` je v hodnotu na nejbližší celé číslo `x`  /  `y` a `n` i je vždy, když &#124; `n`  -  `x`  /  `y` &#124; = 1/2. Když `r` = 0, `r` má stejné znaménko jako `x`.  
  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `remainder` , přijmout a vrátit `float` nebo `long double` hodnoty. V programu C `remainder` vždy přebírá dva hodnoty Double a vrátí hodnotu typu double.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`remainder`, `remainderf`, `remainderl`|\<Math.h >|  
  
 Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_remainder.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = remainder(w, x);  
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);  
}  
```  
  
```Output  
The remainder of -10.00 / 3.00 is -1.000000  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [ldiv –, lldiv –](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv –](../../c-runtime-library/reference/imaxdiv.md)   
 [fmod, fmodf –](../../c-runtime-library/reference/fmod-fmodf.md)   
 [remquo, remquof, remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)