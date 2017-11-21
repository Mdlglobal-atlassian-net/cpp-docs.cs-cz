---
title: "Fmin, fminf –, fminl | Microsoft Docs"
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
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4e8fd804c63caa1a8558e19cb67b4b3f35ecf180
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl
Určuje menší ze dvou zadaných hodnot.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double fmin(  
   double x,   
   double y  
);  
  
float fmin(  
   float x,   
   float y  
); //C++ only  
  
long double fmin(  
   long double x,   
   long double y  
); //C++ only  
  
float fminf(  
   float x,   
   float y  
);  
  
long double fminl(  
   long double x,   
   long double y  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 První hodnota pro porovnání.  
  
 `y`  
 Druhá hodnota pro porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí menší z `x` nebo `y`.  
  
|Vstup|Výsledek|  
|-----------|------------|  
|`x`je NaN.|`y`|  
|`y`je NaN.|`x`|  
|`x`a `y` jsou NaN.|NaN|  
  
 Funkce nezpůsobí [_matherr –](../../c-runtime-library/reference/matherr.md) má být volána, způsobit, že všechny výjimky, s plovoucí desetinnou čárkou nebo změňte hodnotu `errno`.  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `fmin` , přijmout a vrátit float a typy long double. V programu C `fmin` vždy provede a vrátí hodnotu typu double.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`fmin`, `fminf`, `fminl`|C: \<math.h ><br />C++: \<math.h > nebo \<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)  
 [Fmax, fmaxf –, fmaxl](fmax-fmaxf-fmaxl.md)  