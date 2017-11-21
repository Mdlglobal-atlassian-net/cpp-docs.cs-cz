---
title: "ldiv –, lldiv – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ldiv
- lldiv
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
- ldiv
- lldiv
dev_langs: C++
helpviewer_keywords:
- ldiv function
- lldiv function
- quotients, computing
- computing remainders
- remainder computing
- computing quotients
ms.assetid: 68ab5d83-27a4-479c-9d52-d055eb139eca
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1c1da38d40c45ecd6dc36eed594304894a25dcc7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ldiv-lldiv"></a>ldiv, lldiv
Vypočítá podílu a zbytek dvě celá čísla jako jednu operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ldiv_t ldiv(  
   long numer,  
   long denom   
);  
lldiv_t lldiv(  
   long long numer,  
   long long denom   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `numer`  
 Čítači.  
  
 `denom`  
 Jmenovatel.  
  
## <a name="return-value"></a>Návratová hodnota  
 `ldiv`Vrátí struktura typu [ldiv_t –](../../c-runtime-library/standard-types.md) , se skládá z podílu a zbytek. `lldiv`Vrátí struktura typu [lldiv_t](../../c-runtime-library/standard-types.md) , se skládá z podílu a zbytek.  
  
## <a name="remarks"></a>Poznámky  
 `ldiv` a `lldiv` funkce rozdělení `numer` podle `denom`a tím výpočetní podílu a zbytek. Znaménko podílu je stejný jako u matematickém podílu. Absolutní hodnota podílu je největší číslo typu integer, která je menší než hodnota absolutní matematickém podílu. Pokud jmenovatel hodnotu 0, program se ukončí s chybovou zprávou. `ldiv`a `lldiv` jsou stejné jako `div`kromě toho, že argumenty `ldiv` a členové struktury vrácený jsou všechny typu `long`a argumenty `lldiv` a členů struktury vráceného typu `long long`.  
  
 `ldiv_t` a `lldiv_t` struktury jsou definovány v \<stdlib.h >.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`ldiv`, `lldiv`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_ldiv.c  
  
#include <stdlib.h>  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   long x = 5149627, y = 234879;  
   ldiv_t div_result;  
  
   div_result = ldiv( x, y );  
   printf( "For %ld / %ld, the quotient is ", x, y );  
   printf( "%ld, and the remainder is %ld\n",   
            div_result.quot, div_result.rem );  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
For 5149627 / 234879, the quotient is 21, and the remainder is 217168  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [imaxdiv –](../../c-runtime-library/reference/imaxdiv.md)