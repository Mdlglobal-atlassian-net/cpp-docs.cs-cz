---
title: "hypot –, hypotf –, hypotl –, _hypot –, _hypotf, _hypotl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _hypotf
- hypot
- hypotf
- _hypot
- _hypotl
- hypotl
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
- hypotf
- hypotl
- _hypotl
- hypot
- _hypot
- _hypotf
dev_langs: C++
helpviewer_keywords:
- hypotenuse calculation
- hypot function
- hypotf function
- triangles, calculating hypotenuse
- hypotl function
- calculating hypotenuses
- _hypot function
ms.assetid: 6a13887f-bd53-43fc-9d77-5b42d6e49925
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 36a9fee91a98b224d31df6b9af58ce4caf27030a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hypot-hypotf-hypotl-hypot-hypotf-hypotl"></a>hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl
Vypočítá přepony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double hypot(   
   double x,  
   double y   
);  
float hypotf(   
   float x,  
   float y   
);  
long double hypotl(  
   long double x,  
   long double y  
);  
double _hypot(   
   double x,  
   double y   
);  
float _hypotf(   
   float x,  
   float y   
);  
long double _hypotl(  
   long double x,  
   long double y  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`, `y`  
 Hodnoty s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `hypot` vrátí délku přepony; na přetečení, `hypot` vrátí INF (infinity) a `errno` proměnná je nastavená na `ERANGE`. Můžete použít `_matherr` k úpravě zpracování chyb.  
  
 Další informace o návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `hypot` Funkce Vypočítat délka přepony trojúhelníku vpravo, zadána délka sociálními `x` a `y` (jinými slovy, druhou odmocninu čísla `x` <sup>2</sup>  +  `y` <sup>2</sup>).  
  
 Verze funkcí, které mají počáteční podtržítka jsou k dispozici pro kompatibilitu s dřívější standardů. Jejich chování je stejná jako verze, které nemají úvodní podtržítka. Doporučujeme používat verze bez úvodní podtržítka pro nový kód.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`hypot`, `hypotf`, `hypotl`, `_hypot`, `_hypotf`, `_hypotl`|\<Math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_hypot.c  
// This program prints the hypotenuse of a right triangle.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 3.0, y = 4.0;  
  
   printf( "If a right triangle has sides %2.1f and %2.1f, "  
           "its hypotenuse is %2.1f\n", x, y, _hypot( x, y ) );  
}  
```  
  
```Output  
If a right triangle has sides 3.0 and 4.0, its hypotenuse is 5.0  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [_cabs –](../../c-runtime-library/reference/cabs.md)   
 [_matherr –](../../c-runtime-library/reference/matherr.md)