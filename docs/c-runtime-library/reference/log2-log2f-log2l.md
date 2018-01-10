---
title: "log2, log2f –, log2l | Microsoft Docs"
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
- log2
- log2l
- log2f
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
dev_langs: C++
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e96e572070471d59e91c8f10a382c2770dcc6385
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="log2-log2f-log2l"></a>log2, log2f –, log2l
Určuje binární logaritmus (základ 2) se zadanou hodnotou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double log2(  
   double x  
);  
  
float log2(  
   float x  
); //C++ only  
  
long double log2(  
   long double x  
); //C++ only  
  
float log2f(  
   float x  
);  
  
long double log2l(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`x`  
 Hodnota k určení logaritmus základu 2.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí vrátit log2 `x`.  
  
 Jinak může vrátit jednu z následujících hodnot:  
  
|Problém|Vrátí|  
|-----------|------------|  
|`x` < 0|NaN|  
|`x` = ±0|-INFINITY|  
|`x` = 1|+0|  
|+ INFINITY|+ INFINITY|  
|NaN|NaN|  
|chyby domény|NaN|  
|Chyba pólu|-Huge_val –, - HUGE_VALF, nebo - HUGE_VALL|  
  
 Vznikly chyby uvedené v [_matherr –](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Poznámky  
 Pokud x je celé číslo, vrátí funkce v podstatě index založený na nule nejvýznamnějších 1 bit z `x`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`log2`,                `log2f`,  `log2l`|\<Math.h >|\<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [exp2 – exp2f –, exp2l](../../c-runtime-library/reference/exp2-exp2f-exp2l.md)   
 [log, logf, log10, log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)