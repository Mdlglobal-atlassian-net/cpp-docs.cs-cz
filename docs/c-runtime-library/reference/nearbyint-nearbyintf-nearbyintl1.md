---
title: "nearbyint – nearbyintf –, nearbyintl | Microsoft Docs"
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
- nearbyint
- nearbyintf
- nerabyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
dev_langs:
- C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d981df622450ef0b52a9b0d81427497a3e180bc
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl
Zaokrouhlí číslo s plovoucí desetinnou čárkou zadanou hodnotu na celé číslo a vrátí tuto hodnotu ve formátu s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double nearbyint(  
   double x  
);  
  
float nearbyint(  
   float x  
); //C++ only  
  
long double nearbyint(  
   long double x  
); //C++ only  
  
float nearbyintf(  
   float x  
);  
  
long double nearbyintl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `x`  
 Hodnota, která má být zaokrouhleno.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `x`, zaokrouhleno na nejbližší celé číslo ve formátu aktuální zaokrouhlení jako určené fegetround. Funkce, jinak může vrátit jednu z následujících hodnot:  
  
|Problém|Vrátí|  
|-----------|------------|  
|`x`= ±INFINITY|±INFINITY, ponechat beze změny|  
|`x` = ±0|±0, ponechat beze změny|  
|`x`= NaN.|NaN|  
  
 Nejsou chyby nahlášené prostřednictvím [_matherr –](../../c-runtime-library/reference/matherr.md); konkrétně tato funkce nehlásí nějaké FE_INEXACT výjimky.  
  
## <a name="remarks"></a>Poznámky  
 Hlavní rozdíl mezi tato funkce a `rint` je, že tato funkce nevyvolá nepřesný plovoucí výjimka bodu.  
  
 Protože jsou maximální hodnoty s plovoucí desetinnou čárkou přesný celá čísla, tato funkce se nikdy přetečení samostatně; Místo toho může výstupu přetečení návratovou hodnotu, podle toho, kterou verzi funkce používáte.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`nearbyint`,                `nearbyintf`,  `nearbyintl`|\<math.h>|\<cmath>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Abecední seznam odkazů na funkce](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)