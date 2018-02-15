---
title: "ASIN, asinf –, asinl – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- asinf
- asinl
- asin
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
- asin
- asinl
- asinf
dev_langs:
- C++
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4cb5f90a909a4e2250768bf158f6f51f53bbee4a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl
Vypočítá Arkus sinus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double asin(   
   double x   
);  
float asin(  
   float x  
);  // C++ only  
long double asin(  
   long double x  
);  // C++ only  
float asinf (   
   float x   
);  
long double asinl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota, jejíž Arkus sinus je vypočtena.  
  
## <a name="return-value"></a>Návratová hodnota  
 `asin` Funkce vrátí Arkus sinus (inverzní sinus funkce) z `x` v rozsahu - pí/2 do pí/2 radiánech.  
  
 Ve výchozím nastavení pokud `x` je menší než -1 nebo větší než 1, `asin` vrátí neomezené.  
  
|Vstup|Výjimka SEH|Matherr – výjimka|  
|-----------|-------------------|-----------------------|  
|± ∞|`INVALID`|`_DOMAIN`|  
|± `QNAN`,`IND`|žádná|`_DOMAIN`|  
|&#124;x&#124;>1|`INVALID`|`_DOMAIN`|  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `asin` s `float` a `long double` hodnoty. V programu C `asin` vždy provede a vrátí hodnotu typu double.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`asin`, `asinf`, `asinl`|\<math.h>|  
  
## <a name="example"></a>Příklad  
 Další informace najdete v tématu [acos, acosf –, acosl –](../../c-runtime-library/reference/acos-acosf-acosl.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [ACOS, acosf –, acosl –](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [Atan, atanf –, atanl –, atan2, atan2f –, atan2l –](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [Cos, cosf –, cosl –, cosh, coshf –, coshl –](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [_matherr](../../c-runtime-library/reference/matherr.md)   
 [Sin, sinf –, sinl –, sinh, sinhf –, sinhl –](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)