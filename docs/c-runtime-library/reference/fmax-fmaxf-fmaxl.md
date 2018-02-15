---
title: "Fmax, fmaxf –, fmaxl | Microsoft Docs"
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
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
dev_langs:
- C++
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d9992c149dca5a2fc5be52ae0029494b10e4bbe
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl
Určení větší ze dvou zadaný číselných hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double fmax(  
   double x,   
   double y  
);  
  
float fmax(  
   float x,   
   float y  
); //C++ only  
  
long double fmax(  
   long double x,   
   long double y  
); //C++ only  
  
float fmaxf(  
   float x,   
   float y  
);  
  
long double fmaxl(  
   long double x,   
   long double y  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `x`  
 První hodnota pro porovnání.  
  
 [in] `y`  
 Druhá hodnota pro porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí větší z `x` nebo `y`. Hodnota vrácená je přesný a není závislá na jakoukoli formu zaokrouhlení.  
  
 Jinak může vrátit jednu z následujících hodnot:  
  
|Problém|Vrátí|  
|-----------|------------|  
|`x` = NaN.|`y`|  
|`y` = NaN.|`x`|  
|`x` a `y` = NaN.|NaN|  
  
 Tato funkce nepoužívá chyby uvedené v [_matherr –](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení fmax, která přijmout a vrátit float a typy long double. V programu C fmax vždy provede a vrátí hodnotu typu double.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`fmax`, `fmaxf`, `fmaxl`|\<math.h>|\<cmath – > nebo \<math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmin, fminf, fminl](fmin-fminf-fminl.md)  