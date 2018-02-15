---
title: "remquo – remquof –, remquol – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- remquof
- remquo
- remquol
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
- remquof
- remquol
- remquo
dev_langs:
- C++
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: deb68c536acab80077870bbc0b16ef171edb1d87
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol
Vypočítá zbytek dvě celočíselné hodnoty a ukládá hodnotu celého čísla se přihlaste a přibližný odhad podílu v umístění zadaném v parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double remquo(   
   double numer,  
   double denom,  
   int* quo  
);  
float remquo(   
   float numer,  
   float denom,  
   int* quo  
); /* C++ only */  
long double remquo(   
   long double numer,  
   long double denom,  
   int* quo  
); /* C++ only */  
float remquof(   
   float numer,  
   float denom,  
   int* quo  
);  
long double remquol(   
   long double numer,  
   long double denom,  
   int* quo  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `numer`  
 Čítači.  
  
 `denom`  
 Jmenovatel.  
  
 `quo`  
 Ukazatel na celočíselnou hodnotu, která má přihlašovací a přibližný odhad podílu ukládat.  
  
## <a name="return-value"></a>Návratová hodnota  
 `remquo` Vrátí s plovoucí desetinnou čárkou zbytek `x`  /  `y`. Pokud hodnota `y` je 0,0, `remquo` vrátí quiet NaN. Informace o reprezentace quiet NaN pomocí `printf` rodiny, viz [printf _printf_l –, wprintf, _wprintf_l –](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
## <a name="remarks"></a>Poznámky  
 `remquo` Funkce vypočítá s plovoucí desetinnou čárkou zbývající `f` z `x`  /  `y` tak, aby `x`  =  `i` `*` `y`  +  `f`, kde `i` je celé číslo, `f` má stejné znaménko jako `x`a absolutní hodnotu `f` je menší než absolutní hodnotu `y`.  
  
 C++ umožňuje přetížení, takže můžete volat přetížení `remquo` , přijmout a vrátit `float` nebo `long double` hodnoty. V programu C `remquo` vždy přebírá dva hodnoty Double a vrátí hodnotu typu double.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`remquo`, `remquof`, `remquol`|\<math.h>|  
  
 Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_remquo.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
   int quo = 0;  
  
   z = remquo(w, x, &quo);  
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);  
   printf("Approximate signed quotient is %d\n", quo);  
}  
```  
  
```Output  
The remainder of -10.00 / 3.00 is -1.000000  
Approximate signed quotient is -3  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [ldiv –, lldiv –](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)   
 [fmod, fmodf –](../../c-runtime-library/reference/fmod-fmodf.md)   
 [remainder, remainderf, remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)