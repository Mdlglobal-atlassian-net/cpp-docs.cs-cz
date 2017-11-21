---
title: "FMA – fmaf –, fmal | Microsoft Docs"
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
- fma
- fmaf
- fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
dev_langs: C++
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ec77e462b357708153f26b5289f35c2ee7b7a104
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal
Vynásobí dvě hodnoty společně, přidá třetí hodnota a pak zaokrouhlí výsledek, aniž by došlo ke ztrátě všech přesnost kvůli zprostředkující zaokrouhlení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double fma(  
   double x,   
   double y,   
   double z  
);  
  
float fma(  
   float  x,   
   float  y,   
   float z  
); //C++ only  
  
long double fma(  
   long double  x,   
   long double  y,   
   long double z  
); //C++ only  
  
float fmaf(  
   float  x,   
   float  y,   
   float z  
);  
  
long double fmal(  
   long double  x,   
   long double  y,   
   long double z  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`x`  
 První hodnota k násobení.  
  
 [v]`y`  
 Druhá hodnota mají vynásobit.  
  
 [v]`z`  
 Hodnota k přidání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `(x * y) + z`. Návratová hodnota je zaokrouhlí formátu aktuální zaokrouhlení.  
  
 Jinak může vrátit jednu z následujících hodnot:  
  
|Problém|Vrátí|  
|-----------|------------|  
|`x`= INFINITY, `y` = 0 nebo<br /><br /> `x`= 0, `y` = INFINITY|NaN|  
|`x`nebo `y` = přesný rozmezí INFINITY, `z` = INFINITY s opačným znaménkem|NaN|  
|`x`nebo `y` = NaN.|NaN|  
|Ne (`x` = 0, `y`= neomezené) a `z` = NaN.<br /><br /> Ne (`x`= neomezené, `y`= 0) a `z` = NaN.|NaN|  
|Rozsah chybu přetečení|±HUGE_VAL, ±HUGE_VALF nebo ±HUGE_VALL|  
|Podtečení rozsah chyby|správnou hodnotu po zaokrouhlení.|  
  
 Vznikly chyby uvedené v [_matherr –](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `fma` , přijmout a vrátit **float** a **long double** typy. V programu C `fma` vždy provede a vrátí **dvojité**.  
  
 Tato funkce vypočítá hodnotu, jako kdyby byly provedeny na neomezenou přesnost a pak zaokrouhlí konečný výsledek.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`fma`, `fmaf`, `fmal`|\<Math.h >|\<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [zbývající, remainderf –, remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)   
 [remquo – remquof –, remquol –](../../c-runtime-library/reference/remquo-remquof-remquol.md)