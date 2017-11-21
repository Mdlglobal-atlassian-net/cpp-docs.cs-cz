---
title: "Cos, cosf –, cosl –, cosh, coshf –, coshl – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- coshl
- cosh
- cos
- cosl
- cosf
- coshf
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
- coshl
- cos
- cosf
- cosh
- cosl
- coshf
dev_langs: C++
helpviewer_keywords:
- cosines
- cosl function
- calculating cosine
- cosf function
- cos function
- cosh function
- coshf function
- trigonometric functions
- cosines, calculating
- coshl function
- hyperbolic functions
ms.assetid: ae90435e-6b68-4a47-a81f-be87d5c08f16
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c37223f67e5c6d03aa7401870fb7ccbbd111cee3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cos-cosf-cosl-cosh-coshf-coshl"></a>cos, cosf, cosl, cosh, coshf, coshl
Výpočet kosinu (`cos`, `cosf`, nebo `cosl`), nebo hyperbolický kosinus (`cosh`, `coshf`, nebo `coshl`).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double cos(   
   double x   
);  
float cos(  
   float x   
);  // C++ only  
long double cos(  
   long double x  
);  // C++ only  
float cosf(   
   float x   
);  
long double cosl(  
   long double x  
);  
double cosh(   
   double x   
);  
float cosh(  
   float x   
);  // C++ only  
long double cosh(  
   long double x  
);  // C++ only  
float coshf(  
   float x   
);  
long double coshl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Úhel v radiánech.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kosinus nebo hyperbolický kosinus `x`. Pokud `x` je větší než nebo rovno 263, nebo menší než nebo rovna-263 ztrátu násobek ve výsledku volání `cos`, `cosf`, nebo `cosl` dojde.  
  
 Ve výchozím nastavení, pokud je výsledek příliš velké `cosh`, `coshf`, nebo `coshl` volat, funkce vrátí hodnotu `HUGE_VAL` a nastaví `errno` k `ERANGE`.  
  
|Vstup|Výjimka SEH|Matherr – výjimka|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|žádná|`_DOMAIN`|  
|± ∞  (`cosf`, `cos`, `cosl`)|`INVALID`|`_DOMAIN`|  
|x ≥ 7.104760e + 002 (`cosh`, `coshf`, `coshl`)|`INEXACT`+`OVERFLOW`|`OVERFLOW`|  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `cos` a `cosh` , přijmout a vrátit `float` nebo `long double` hodnoty. V programu C `cos` a `cosh` vždy přijmout a vrátit `double`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`cos`, `cosh`, `cosf`, `coshf`, `cosl`, `coshl`|\<Math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad v [sin, sinf –, sinl –, sinh, sinhf –, sinhl –](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [ACOS, acosf –, acosl –](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [ASIN, asinf –, asinl –](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [Atan, atanf –, atanl –, atan2, atan2f –, atan2l –](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [_matherr –](../../c-runtime-library/reference/matherr.md)   
 [Sin, sinf –, sinl –, sinh, sinhf –, sinhl –](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [Tan, tanf –, tanl –, tanh, tanhf –, tanhl –](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [_Cicos –](../../c-runtime-library/cicos.md)