---
title: casin, casinf, casinl | Microsoft Docs
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
- casin
- casinf
- casinl
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
- casin
- casinf
- casinl
- complex/casin
- complex/casinf
- complex/casinl
dev_langs:
- C++
helpviewer_keywords:
- casin function
- casinf function
- casinl function
ms.assetid: b75d1455-7b1e-43b0-bd46-c530be190be9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f0b0131db3ce020d4f840cc7374c8d55b01a5ab
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="casin-casinf-casinl"></a>casin, casinf, casinl
Načte Arkus sinus komplexního čísla, s větve kusy mimo interval [-1, + 1] pro skutečné osu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_Dcomplex casin(   
   _Dcomplex z   
);  
_Fcomplex casin(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex casin(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex casinf(   
   _Fcomplex z   
);  
_Lcomplex casinl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `z`  
 Komplexní číslo, které představuje úhel v radiánech.  
  
## <a name="return-value"></a>Návratová hodnota  
 Arkus sinus `z`, v radiánech. Výsledkem je, bez vazby pomyslná osy a v intervalu [-pí/2 + pí/2] pro skutečné osu.  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `casin` , přijmout a vrátit `_Fcomplex` a `_Lcomplex` hodnoty. V programu C `casin` vždy provede a vrátí `_Dcomplex` hodnotu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Hlavička C|Hlavička C++|  
|-------------|--------------|------------------|  
|`casin`,               `casinf`, `casinl`|\<complex.h>|\<ccomplex>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh, catanhf, catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh, ctanhf, ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan, catanf, catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh, csinhf, csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh, casinhf, casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh, ccoshf, ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh, cacoshf, cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos, cacosf, cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan, ctanf, ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin, csinf, csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [ccos, ccosf, ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt, csqrtf, csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)