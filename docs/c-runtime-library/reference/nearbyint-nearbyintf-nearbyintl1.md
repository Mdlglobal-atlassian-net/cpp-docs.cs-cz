---
title: "nearbyint – nearbyintf –, nearbyintl1 | Microsoft Docs"
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
dev_langs: C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d95f92d15dcf4b8baf84b762b994bdb52930346d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [v]`x`  
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
|`nearbyint`,                `nearbyintf`,  `nearbyintl`|\<Math.h >|\<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Abecední seznam odkazů na funkce](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)