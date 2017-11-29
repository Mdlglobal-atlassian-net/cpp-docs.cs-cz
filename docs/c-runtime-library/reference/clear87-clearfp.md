---
title: "_clear87 –, _clearfp – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _clearfp
- _clear87
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clearfp
- _clearfp
- _clear87
- clear87
dev_langs: C++
helpviewer_keywords:
- clearing floating point status word
- clearfp function
- _clear87 function
- _clearfp function
- clear87 function
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 674ea06964fe245db863763169fe7b900b89cc84
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="clear87-clearfp"></a>_clear87, _clearfp
Získá a vymaže s plovoucí desetinnou čárkou stavového slova.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned int _clear87( void );  
unsigned int _clearfp( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Bity v hodnotě vrácené označují s plovoucí desetinnou čárkou stav před voláním `_clear87` nebo `_clearfp`. Pro dokončení definice bits vrácený `_clear87`, najdete v části float.h –. Mnoho funkcí knihovny math upravit 8087/80287 stavového slova, s vést k neočekávaným výsledkům. Návratové hodnoty z `_clear87` a `_status87` stát spolehlivější při provádění operací méně s plovoucí desetinnou čárkou mezi známé stavy s plovoucí desetinnou čárkou stavového slova.  
  
## <a name="remarks"></a>Poznámky  
 `_clear87` Funkce vymaže příznaky výjimka v aplikaci word s plovoucí desetinnou čárkou stav, nastaví zaneprázdněn bit na hodnotu 0 a vrátí stavového slova. S plovoucí desetinnou čárkou stavového slova je kombinací 8087/80287 stavového slova a další podmínky zjištěný obslužná rutina výjimky 8087/80287, jako je přetečení zásobníku s plovoucí desetinnou čárkou a podtečení.  
  
 `_clearfp`je nezávislé na platformě, přenosné verze `_clear87` rutiny. Je stejný jako `_clear87` na platformách Intel (x86) a také podporuje x64 a ARM platformy. K zajištění, že váš kód s plovoucí desetinnou čárkou je přenosné x64 a ARM, použijte `_clearfp`. Pokud cílíte pouze x86 platformy, můžete použít buď `_clear87` nebo `_clearfp`.  
  
 Tyto funkce jsou zastaralé, když kompilujete s [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) protože modul common language runtime podporuje pouze výchozí přesnost s plovoucí desetinnou čárkou.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_clear87`|\<float.h – >|  
|`_clearfp`|\<float.h – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_clear87.c  
// compile with: /Od  
  
// This program creates various floating-point   
// problems, then uses _clear87 to report on these problems.  
// Compile this program with Optimizations disabled (/Od).   
// Otherwise the optimizer will remove the code associated with   
// the unused floating-point values.  
//  
  
#include <stdio.h>  
#include <float.h>  
  
int main( void )  
{  
   double a = 1e-40, b;  
   float x, y;  
  
   printf( "Status: %.4x - clear\n", _clear87()  );  
  
   // Store into y is inexact and underflows:  
   y = a;  
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );  
  
   // y is denormal:   
   b = y;  
   printf( "Status: %.4x - denormal\n", _clear87() );  
}  
```  
  
```Output  
Status: 0000 - clear  
Status: 0003 - inexact, underflow  
Status: 80000 - denormal  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [_status87 – _statusfp –, _statusfp2 –](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)