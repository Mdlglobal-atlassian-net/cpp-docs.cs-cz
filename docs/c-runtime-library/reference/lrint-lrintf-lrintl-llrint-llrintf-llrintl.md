---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
dev_langs:
- C++
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80a331618df913040ea145346299ebd30509ce8e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl
Zaokrouhlí na nejbližší hodnotu integrální zadaná hodnota s plovoucí desetinnou čárkou s použitím aktuální režim zaokrouhlení a směr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long int lrint(  
   double x  
);  
  
long int lrint(  
   float x  
); //C++ only  
  
long int lrint(  
   long double x  
); //C++ only  
  
long int lrintf(  
   float x  
);  
  
long int lrintl(  
   long double x  
);  
  
long long int llrint(  
   double x  
);  
  
long long int llrint(  
   float x  
); //C++ only  
  
long long int llrint(  
   long double x  
); //C++ only  
  
long long int llrintf(  
   float x  
);  
  
long long int llrintl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `x`  
 Hodnota, která má být zaokrouhleno.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí zaokrouhlené integrální hodnotu `x`.  
  
|Problém|Vrátí|  
|-----------|------------|  
|`x` je mimo rozsah návratový typ<br /><br /> `x` = ±∞<br /><br /> `x` = NaN.|Vyvolá FE_INVALID a vrátí nula (0).|  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `lrint` a `llrint` které přebírají float a typy long double. V programu C `lrint` a `llrint` vždy provést datový typ double.  
  
 Pokud `x` nepředstavuje s plovoucí desetinnou čárkou ekvivalentní celočíselné hodnoty, tyto funkce vyvolat FE_INEXACT.  
  
 **Microsoft konkrétní**: Pokud výsledkem je mimo rozsah návratový typ, nebo pokud je parametr NaN nebo infinity, vrácená hodnota je implementace definované. Kompilátor Microsoft vrátí nula (0) hodnotu.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`lrint`,                `lrintf`, `lrintl`, `llrint`, `llrintf`, `llrintl`|\<math.h>|\<cmath>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Abecední seznam odkazů na funkce](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)