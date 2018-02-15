---
title: div | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- div
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- div
dev_langs:
- C++
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2090ca5e08af74854177f02d6313d6c1304ed2c6
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="div"></a>div
Vypočítá podílu a zbývající dva celočíselné hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
div_t div(   
   int numer,  
   int denom   
);  
ldiv_t div(  
   long numer,  
   long denom  
); /* C++ only */   
lldiv_t div(  
   long long numer,  
   long long denom  
); /* C++ only */  
```  
  
#### <a name="parameters"></a>Parametry  
 `numer`  
 Čítači.  
  
 `denom`  
 Jmenovatel.  
  
## <a name="return-value"></a>Návratová hodnota  
 `div` volat pomocí argumenty typu `int` vrací strukturu typu `div_t`, což zahrnuje podílu a zbytek. Návratová hodnota přetížení argumentů typu `long` je `ldiv_t`. Obě `div_t` a `ldiv_t` jsou definovány v STDLIB. H.  
  
## <a name="remarks"></a>Poznámky  
 `div` Funkce vydělí `numer` podle `denom` a tím vypočítá podílu a zbytek. [Div_t –](../../c-runtime-library/standard-types.md) struktura obsahuje podílu, `int quot`a zbývající, `int rem`. Znaménko podílu je stejný jako u matematickém podílu. Jeho absolutní hodnota je největší číslo typu integer, která je menší než hodnota absolutní matematickém podílu. Pokud jmenovatel hodnotu 0, program se ukončí s chybovou zprávou.  
  
 Přetížení, které nepřebírají argumenty typu `long` nebo `long long` jsou dostupné jenom pro C++ – kód. Návratový typ [ldiv_t –](../../c-runtime-library/standard-types.md) obsahuje členy `long quot` a `long rem`a návratový typ [lldiv_t](../../c-runtime-library/standard-types.md) obsahuje členy `long long quot` a `long long rem`, které mají stejné významy jako členy `div_t`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`div`|\<stdlib.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_div.c  
// arguments: 876 13  
  
// This example takes two integers as command-line  
// arguments and displays the results of the integer  
// division. This program accepts two arguments on the  
// command line following the program name, then calls  
// div to divide the first argument by the second.  
// Finally, it prints the structure members quot and rem.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <math.h>  
  
int main( int argc, char *argv[] )  
{  
   int x,y;  
   div_t div_result;  
  
   x = atoi( argv[1] );  
   y = atoi( argv[2] );  
  
   printf( "x is %d, y is %d\n", x, y );  
   div_result = div( x, y );  
   printf( "The quotient is %d, and the remainder is %d\n",  
           div_result.quot, div_result.rem );  
}  
```  
  
```Output  
x is 876, y is 13  
The quotient is 67, and the remainder is 5  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [ldiv –, lldiv –](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)