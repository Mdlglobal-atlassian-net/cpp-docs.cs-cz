---
title: "exp2 – exp2f –, exp2l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- exp2
- exp2f
- exp2l
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
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
dev_langs: C++
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 19aeabbda33f4eb2e6b140ab2d887813f155b67f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l
Vypočítá 2, vyvolá se zadanou hodnotou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double exp2(  
   double x  
);  
  
float exp2(  
   float x  
);  // C++ only  
  
long double exp2(  
   long double x  
); // C++ only  
  
float exp2f(  
   float x  
);  
  
long double exp2l(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`x`  
 Hodnota exponent.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí exponent základu 2 `x`, který je 2<sup>x</sup>. Jinak vrátí jednu z následujících hodnot:  
  
|Problém|Vrátí|  
|-----------|------------|  
|`x` = ±0|1|  
|`x`= – INFINITY|+0|  
|`x`= + INFINITY|+ INFINITY|  
|`x`= NaN.|NaN|  
|Rozsah chybu přetečení|+ Huge_val – + HUGE_VALF, nebo + HUGE_VALL|  
|Podtečení rozsah chyby|Správný výsledek po zaokrouhlení|  
  
 Vznikly chyby uvedené v [_matherr –](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `exp2` , přijmout a vrátit **float** a **long double** typy. V programu C `exp2` vždy provede a vrátí **dvojité**.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Hlavička C|Hlavička C++|  
|-------------|--------------|------------------|  
|`exp`, `expf`, `expl`|\<Math.h >|\<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [Exp, expf –, expl](../../c-runtime-library/reference/exp-expf.md)   
 [log2, log2f –, log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)