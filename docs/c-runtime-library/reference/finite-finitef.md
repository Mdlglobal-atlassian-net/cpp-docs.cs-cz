---
title: "_finite –, _finitef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _finite
- _finitef
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
- finite
- _finite
- _finitef
- math/_finite
- math/_finitef
- float/_finite
dev_langs:
- C++
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb904e04e8a99bff242d520f6c0ca3d404a74e89
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="finite-finitef"></a>_finite –, _finitef
Určuje, zda je omezené hodnotu s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _finite(   
   double x   
);  
  
int _finitef(   
   float x   
); /* x64 and ARM/ARM64 only */  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota s plovoucí desetinnou čárkou k testování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Obě `_finite` a `_finitef` vrátí nenulovou hodnotu, pokud argument *x* je konečného počtu permutací; je, pokud -INF < `x` < + INF. Vrátí 0, pokud je argument nekonečné nebo NAN.  
  
## <a name="remarks"></a>Poznámky  
 `_finite` a `_finitef` funkce se konkrétní společnosti Microsoft. `_finitef` Funkce je pouze k dispozici v případě zkompilovaném pro x86 ARM nebo ARM64 platformy.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|  
|--------------|---------------------------|-------------------------------|  
|`_finite`|\<float.h – > nebo \<math.h >|\<float.h – >, \<math.h >, \<cfloat – >, nebo \<cmath – >|  
|`_finitef`|\<math.h>|\<Math.h > nebo \<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [isnan, _isnan, _isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [_fpclass, _fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)