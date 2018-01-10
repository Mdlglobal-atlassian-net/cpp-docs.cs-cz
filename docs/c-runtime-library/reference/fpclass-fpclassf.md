---
title: _fpclass _fpclassf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fpclass
- _fpclassf
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
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
dev_langs: C++
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92501f119d0f0222de0ffeca0611e5fd6c96b697
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fpclass-fpclassf"></a>_fpclass _fpclassf
Vrátí hodnotu, která určuje s plovoucí desetinnou čárkou klasifikace argumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _fpclass(   
   double x   
);  
  
int _fpclassf(   
   float x   
); /* x64 only */  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota s plovoucí desetinnou čárkou k testování.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_fpclass` a `_fpclassf` funkce vrátí celočíselnou hodnotu, která určuje, s plovoucí desetinnou čárkou klasifikace argumentu `x`. Klasifikace může mít jednu z následujících hodnot, které jsou definované v \<float.h – >.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`_FPCLASS_SNAN`|Signalizace NaN.|  
|`_FPCLASS_QNAN`|Quiet NaN.|  
|`_FPCLASS_NINF`|Záporné nekonečno (-INF)|  
|`_FPCLASS_NN`|Záporné normalized nulová|  
|`_FPCLASS_ND`|Záporné nenormalizovanou|  
|`_FPCLASS_NZ`|Záporné nula (– 0)|  
|`_FPCLASS_PZ`|Kladné 0 (+ 0)|  
|`_FPCLASS_PD`|Kladná nenormalizovanou|  
|`_FPCLASS_PN`|Kladná normalized nulová|  
|`_FPCLASS_PINF`|Kladné nekonečno (+ INF)|  
  
## <a name="remarks"></a>Poznámky  
 `_fpclass` a `_fpclassf` funkce se konkrétní společnosti Microsoft. Jsou podobná [fpclassify –](../../c-runtime-library/reference/fpclassify.md), ale vrátit podrobnější informace o argument. `_fpclassf` Funkce je dostupná pouze při zkompilovaném pro x64 platformy.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fpclass`|\<float.h – >|  
  
 Kompatibilita a shoda informace naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [isNaN, _isnan –, _isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [fpclassify](../../c-runtime-library/reference/fpclassify.md)