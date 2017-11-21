---
title: clog10, clog10f, clog10l | Microsoft Docs
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
- clog10
- clog10f
- clog10l
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
- clog10
- clog10f
- clog10l
- complex/clog10
- complex/clog10f
- complex/clog10l
dev_langs: C++
helpviewer_keywords:
- clog10 function
- clog10f function
- clog10l function
ms.assetid: 2ddae00d-ef93-4441-add3-f4d58358401b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bab5be9a8c686c2c6cd207232ddc6f98d11aa519
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="clog10-clog10f-clog10l"></a>clog10, clog10f, clog10l
Načte logaritmus o základu 10 komplexního čísla.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
_Dcomplex clog10(   
   _Dcomplex z   
);  
_Fcomplex clog10(   
  _Fcomplex z   
);  // C++ only  
_Lcomplex clog10(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex clog10f(   
   _Fcomplex z   
);  
_Lcomplex clog10l(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `z`  
 Základ logaritmu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty jsou:  
  
|z parametru|Návratová hodnota|  
|-----------------|------------------|  
|Kladné|10 logaritmus z|  
|Nula|- ∞|  
|Záporný|NaN|  
|NaN|NaN|  
|+ ∞|+ ∞|  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `clog10` , přijmout a vrátit `_Fcomplex` a `_Lcomplex` hodnoty. V programu C `clog10` vždy provede a vrátí `_Dcomplex` hodnotu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Hlavička C|Hlavička C++|  
|-------------|--------------|------------------|  
|`clog10`,               `clog10f`, `clogl`|\<COMPLEX.h >|\<ccomplex >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp, cexpf, cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [cpow, cpowf, cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog, clogf, clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)