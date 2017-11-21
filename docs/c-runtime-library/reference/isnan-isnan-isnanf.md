---
title: "isNaN, _isnan –, _isnanf | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
dev_langs: C++
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 982760deff4c5e2439c8743aa0de736a24faa02a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="isnan-isnan-isnanf"></a>isNaN, _isnan –, _isnanf
Testy, pokud hodnotu s plovoucí desetinnou čárkou není číslo (NAN).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int isnan(  
   /* floating-point */ x   
); /* C-only macro */  
  
int _isnan(  
   double x   
);  
  
int _isnanf(  
   float x  
); /* x64 only */  
  
template <class T>  
bool isnan(  
   T x  
) throw(); /* C++ only */  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 Hodnota s plovoucí desetinnou čárkou k testování.  
  
## <a name="return-value"></a>Návratová hodnota  
 V jazyce C `isnan` makro a `_isnan` a `_isnanf` vracejí nenulovou hodnotu, pokud argument `x` je NAN; v opačném případě, že budou vracet 0.  
  
 V jazyce C++ `isnan` šablony funkce vrátí `true` Pokud argument `x` je NAN; v opačném případě vracejí `false`.  
  
## <a name="remarks"></a>Poznámky  
 C `isnan` – makro a `_isnan` a `_isnanf` funkce testování s plovoucí desetinnou čárkou *x*, vrátí nenulovou hodnotu, pokud *x* je hodnota číslo (NAN). NAN se vygeneruje, když ve formátu plovoucí desetinné čárky IEEE 754 pro zadaný typ není možné vyjádřit výsledek operace s plovoucí desetinnou čárkou. Informace o tom, jak je reprezentována NAN pro výstup najdete v tématu [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
 Při kompilaci jako C++, `isnan` makro není definován a `isnan` funkce šablona je definována místo. Vrátí hodnotu typu `bool` místo celé číslo.  
  
 `_isnan` a `_isnanf` funkce se konkrétní společnosti Microsoft. `_isnanf` Funkce je dostupná pouze při zkompilovaném pro x64.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaná hlavička (C)|Požadovaná hlavička (C++)|  
|-------------|---------------------------|-------------------------------|  
|`isnan`, `_isnanf`|\<Math.h >|\<Math.h > nebo \<cmath – >|  
|`_isnan`|\<float.h – >|\<float.h – > nebo \<cfloat – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [_finite –, _finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [_fpclass _fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)