---
title: "copysign –, copysignf –, copysignl –, _copysign –, _copysignf –, _copysignl – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
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
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
dev_langs: C++
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 48e78da8f8ffa72ee5e10dab866f5ffdee5aac4c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="copysign-copysignf-copysignl-copysign-copysignf-copysignl"></a>copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl
Vrátí hodnotu, která má odhad jeden argument a přihlaste jiným serverem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double copysign(   
   double x,  
   double y   
);  
float copysign(   
   float x,  
   float y   
); // C++ only  
long double copysign(   
   long double x,  
   long double y   
); // C++ only  
float copysignf(   
   float x,  
   float y   
); // C++ only  
long double copysignl(   
   long double x,  
   long double y   
); // C++ only  
double _copysign(   
   double x,  
   double y   
);  
long double _copysignl(   
   long double x,  
   long double y   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota s plovoucí desetinnou čárkou, která se vrátí jako výsledek odhad.  
  
 `y`  
 Hodnota s plovoucí desetinnou čárkou, která se vrátí jako značka výsledku.  
  
 [Podpora plovoucí desetinné čárky rutiny](../../c-runtime-library/floating-point-support.md)  
  
## <a name="return-value"></a>Návratová hodnota  
 `copysign` Funkce vrátí hodnotu s plovoucí desetinnou čárkou, které kombinuje odhad `x` a znaménko `y`. Neexistuje žádný návratový chyby.  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `copysign` , přijmout a vrátit `float` nebo `long double` hodnoty. V programu C `copysign` vždy provede a vrátí `double`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_copysign`|\<float.h – >|  
|`copysign`, `copysignf`, `copysignl`, `_copysignf`, `_copysignl`|\<Math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [fabs, fabsf –, fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [_chgsign – _chgsignf –, _chgsignl –](../../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)