---
title: "TRUNC, truncf –, truncl | Microsoft Docs"
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
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
dev_langs: C++
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 911636e4fa843afa1220dc99e1f679d5bfe88d7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl
Určuje, na nejbližší celé číslo, která je menší než nebo rovna zadané hodnotě s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double trunc(  
   double x  
);  
  
float trunc(  
   float x  
); //C++ only  
  
long double trunc(  
   long double x  
); //C++ only  
  
float trunc(  
   float x  
); //C++ only  
  
long double truncl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`x`  
 Hodnota zkrátit.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud bylo úspěšné, vrátí metoda hodnotu `x`, zaokrouhleno směrem k nule.  
  
 Jinak může vrátit jednu z těchto možností:  
  
|Problém|Vrátí|  
|-----------|------------|  
|`x`= ±INFINITY|x|  
|`x` =  ±0|x|  
|`x`= NaN.|NaN|  
  
 Vznikly chyby uvedené v [_matherr –](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Poznámky  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `trunc` , přijmout a vrátit float a typy long double. V programu C `trunc` vždy provede a vrátí hodnotu typu double.  
  
 Protože největší hodnoty s plovoucí desetinnou čárkou jsou přesný celá čísla, tato funkce nebude přetečení svoje vlastní. Může ale způsobit funkce přetečení vrácením hodnotu do celočíselného typu.  
  
 Vám může také zaokrouhlí dolů podle implicitní převod z s plovoucí desetinnou čárkou do integrální; to proto je však omezená na hodnoty, které mohou být uloženy ve cílový typ.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Hlavička C|Hlavička C++|  
|--------------|--------------|------------------|  
|`trunc`,                `truncf`,  `truncl`|\<Math.h >|\<cmath – >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace funkcí abecedně](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [Floor, floorf –, floorl –](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [ceil, ceilf –, ceill –](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [round, roundf, roundl](../../c-runtime-library/reference/round-roundf-roundl.md)