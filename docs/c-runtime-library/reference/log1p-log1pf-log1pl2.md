---
title: "log1p – log1pf –, log1pl2 | Microsoft Docs"
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
- log1p
- log1pf
- log1pl
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
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 14d0228b24a97c2b7113cf9ceccf337c15ef904c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="log1p-log1pf-log1pl"></a>log1p – log1pf –, log1pl
Vypočítá přirozený logaritmus 1 plus zadanou hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double log1p(  
   double x  
);  
  
float log1p(  
   float x  
); //C++ only  
  
long double log1p(  
   long double x  
); //C++ only  
  
float log1pf(  
   float x  
);  
  
long double log1pl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Argumentem s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí přirozené protokol (základem e) (`x`+ 1).  
  
 Jinak může vrátit jednu z následujících hodnot:  
  
|Vstup|Výsledek|Výjimka SEH|Kód chyby|  
|-----------|------------|-------------------|-----------|  
|+ inf|+ inf|||  
|Denormals|Stejné jako vstup|PODTEČENÍ||  
|±0|Stejné jako vstup|||  
|-1|-inf|DIVBYZERO|ERANGE –|  
|< -1|NaN.|NEPLATNÝ|EDOM –|  
|-inf|NaN.|NEPLATNÝ|EDOM –|  
|±SNaN|Stejné jako vstup|NEPLATNÝ||  
|±QNaN neomezené|Stejné jako vstup|||  
  
 `errno` Hodnota nastavena na erange – Pokud `x` = -1. `errno` Hodnota nastavena na edom – Pokud `x` < -1.  
  
## <a name="remarks"></a>Poznámky  
 `log1p` Funkce může být přesnější, než pomocí protokolu (`x`+ 1) Pokud x je téměř 0.  
  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `log1p` , přijmout a vrátit float a typy long double. V programu C `log1p` vždy provede a vrátí hodnotu typu double.  
  
 Pokud `x` přirozený číslo, vrátí tato funkce logaritmus faktoriál (`x`-1).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`log1p`,                `log1pf`,  `log1pl`|\<Math.h >|\<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log2, log2f –, log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)   
 [protokol, logf –, log10, log10f –](../../c-runtime-library/reference/log-logf-log10-log10f.md)