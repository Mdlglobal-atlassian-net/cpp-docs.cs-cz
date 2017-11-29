---
title: "imaxabs – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: imaxabs
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
f1_keywords: imaxabs
dev_langs: C++
helpviewer_keywords: imaxabs function
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2bdd796b23275b4585f0e94aeb20197f7e6b893a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="imaxabs"></a>imaxabs
Vypočítá absolutní hodnotu celé jakékoli velikosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
intmax_t imaxabs(  
   intmax_t n   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *n*  
 Celočíselná hodnota.  
  
## <a name="return-value"></a>Návratová hodnota  
 `imaxabs` Funkce vrátí absolutní hodnotu argumentu. Neexistuje žádný návratový chyby.  
  
> [!NOTE]
>  Protože rozsahu záporné celých čísel, které může být reprezentovaný pomocí `intmax_t` je větší než je rozsah kladná celá čísla, které může být reprezentován, je možné poskytnout argumentu `imaxabs` , nelze převést. Pokud se absolutní hodnota argumentu nemůže být reprezentovaná návratový typ, chování `imaxabs` není definován.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`imaxabs`|\<inttypes.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_imaxabs.c  
// Build using: cl /W3 /Tc crt_imaxabs.c  
// This example calls imaxabs to compute an  
// absolute value, then displays the results.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <inttypes.h>  
  
int main(int argc, char *argv[])  
{  
   intmax_t x = LLONG_MIN + 2;  
  
   printf("The absolute value of %lld is %lld\n", x, imaxabs(x));  
}  
```  
  
```Output  
The absolute value of -9223372036854775806 is 9223372036854775806  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [Abs, labs, llabs –, _abs64 –](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [_cabs –](../../c-runtime-library/reference/cabs.md)   
 [fabs, fabsf –, fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   