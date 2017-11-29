---
title: "imaxdiv – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: imaxdiv
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
f1_keywords: imaxdiv
dev_langs: C++
helpviewer_keywords: imaxdiv function
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65c7b71030bff65a2806d20690554a9828871268
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="imaxdiv"></a>imaxdiv
Vypočítá podílu a zbývající dva celočíselné hodnoty libovolnou velikost jako jednu operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
imaxdiv_t imaxdiv(   
   intmax_t numer,  
   intmax_t denom   
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `numer`  
 Čítači.  
  
 `denom`  
 Jmenovatel.  
  
## <a name="return-value"></a>Návratová hodnota  
 `imaxdiv`volat s argumenty typu [intmax_t](../../c-runtime-library/standard-types.md) vrací strukturu typu [imaxdiv_t](../../c-runtime-library/standard-types.md) , zahrnuje podílu a zbytek.  
  
## <a name="remarks"></a>Poznámky  
 `imaxdiv` Funkce vydělí `numer` podle `denom` a tím vypočítá podílu a zbytek. `imaxdiv_t` Struktura obsahuje podílu, `intmax_t quot`a zbývající, `intmax_t rem`. Znaménko podílu je stejný jako u matematickém podílu. Jeho absolutní hodnota je největší číslo typu integer, která je menší než hodnota absolutní matematickém podílu. Pokud jmenovatel hodnotu 0, program se ukončí s chybovou zprávou.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`imaxdiv`|\<inttypes.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_imaxdiv.c  
// Build using: cl /W3 /Tc crt_imaxdiv.c  
// This example takes two integers as command-line  
// arguments and calls imaxdiv to divide the first   
// argument by the second, then displays the results.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <inttypes.h>  
  
int main(int argc, char *argv[])  
{  
   intmax_t x,y;  
   imaxdiv_t div_result;  
  
   x = atoll(argv[1]);  
   y = atoll(argv[2]);  
  
   printf("The call to imaxdiv(%lld, %lld)\n", x, y);  
   div_result = imaxdiv(x, y);  
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",  
          div_result.quot, div_result.rem);  
}  
```  
  
 Když vytvořené a pak volána s parametry příkazového řádku `9460730470000000 8766`, kód generuje tento výstup:  
  
```Output  
The call to imaxdiv(9460730470000000, 8766)  
results in a quotient of 1079252848505, and a remainder of 5170  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [ldiv –, lldiv –](../../c-runtime-library/reference/ldiv-lldiv.md)