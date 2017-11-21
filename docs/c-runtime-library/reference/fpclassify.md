---
title: "fpclassify – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apiname: fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e38ca3275c290d96fd5cf7910044abc32721eb85
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fpclassify"></a>fpclassify –
Vrátí s plovoucí desetinnou čárkou klasifikace argumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int fpclassify(   
   /* floating-point */ x   
);  
  
int fpclassify(   
   float x   
); // C++ only  
  
int fpclassify(   
   double x   
); // C++ only  
  
int fpclassify(   
   long double x   
); // C++ only  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota s plovoucí desetinnou čárkou k testování.  
  
## <a name="return-value"></a>Návratová hodnota  
 `fpclassify`Vrací celočíselnou hodnotu, která určuje třídu s plovoucí desetinnou čárkou argumentu `x`. Tato tabulka obsahuje možné hodnoty vrácené `fpclassify`, definované v \<math.h >.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`FP_NAN`|Tichý, signalizace nebo neurčitém NaN.|  
|`FP_INFINITE`|Kladné a záporné infinity|  
|`FP_NORMAL`|Kladné a záporné normalizovaný nenulovou hodnotu|  
|`FP_SUBNORMAL`|Kladné a záporné hodnoty nenormalizované|  
|`FP_ZERO`|Kladná nebo záporná hodnota nulová hodnota|  
  
## <a name="remarks"></a>Poznámky  
 V jazyce C `fpclassify` je makro; v jazyce C++ `fpclassify` je přetížena pomocí typy argument funkce `float`, `double`, nebo `long double`. V obou případech hodnota vrácená závisí na efektivní výraz argumentu typu, nikoli na všechny zprostředkující reprezentace. Například normální `double` nebo `long double` hodnota stát nekonečna, denormal nebo při převést na hodnotu nula `float`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce/makra|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|  
|---------------------|---------------------------|-------------------------------|  
|`fpclassify`|\<Math.h >|\<Math.h > nebo \<cmath – >|  
  
 `fpclassify` Makro a `fpclassify` funkce požadavkům C99 a C ++ 11 specifikace. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [isNaN, _isnan –, _isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)