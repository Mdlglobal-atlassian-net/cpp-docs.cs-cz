---
title: "logb –, logbf –, logbl –, _logb –, _logbf – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- logb
- _logb
- _logbl
- logbf
- logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
dev_langs:
- C++
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f2c1ad71f5f81b7e21e788e8cdbeb9edce60944
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="logb-logbf-logbl-logb-logbf"></a>logb, logbf, logbl, _logb, _logbf
Extrahuje exponentu hodnoty s plovoucí desetinnou čárkou argumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double logb(  
   double x   
);  
float logb(  
   float x   
); // C++ only  
long double logb(  
   long double x   
); // C++ only   
float logbf(  
   float x   
);  
long double logbl(  
   long double x   
);  
double _logb(  
   double x   
);  
float _logbf(  
   float x   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 x  
 Hodnota s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 `logb` Vrátí hodnotu neposunutého exponentu `x` jako znaménkem reprezentován jako hodnotu s plovoucí desetinnou čárkou.  
  
## <a name="remarks"></a>Poznámky  
 `logb` Funkce extrahovat exponenciální hodnoty s plovoucí desetinnou čárkou argumentu `x`, jako kdyby `x` byly podobě s neomezenou rozsahu. Pokud argument `x` je nenormalizovanou, je zpracováván, jako by byly normalized.  
  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `logb` , přijmout a vrátit `float` nebo `long double` hodnoty. V programu C `logb` vždy provede a vrátí `double`.  
  
|Vstup|Výjimka SEH|Matherr – výjimka|  
|-----------|-------------------|-----------------------|  
|ROZMEZÍ QNAN, IND|Žádné|_DOMAIN|  
|± 0|ZERODIVIDE|–|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_logb`|\<float.h – >|  
|`logb`, `logbf`, `logbl`, `_logbf`|\<math.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)