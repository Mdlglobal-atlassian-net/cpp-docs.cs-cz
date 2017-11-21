---
title: "ERF –, erff –, erfl –, erfc, erfcf –, erfcl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- erff
- erfl
- erf
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
- erfl
- erf
- erff
dev_langs: C++
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: de987b726a4a25fa3bc23bbb569e7c9a9138de2b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl
Vypočítá chybovou funkci nebo funkce doplňkovou chybovou hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double erf(  
   double x  
);  
float erf(  
   float x  
); // C++ only  
long double erf(  
   long double x  
); // C++ only  
float erff(  
   float x  
);  
long double erfl(  
   long double x  
);  
double erfc(  
   double x  
);  
float erfc(  
   float x  
); // C++ only  
long double erfc(  
   long double x  
); // C++ only  
float erfcf(  
   float x  
);  
long double erfcl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `x`  
 Hodnota s plovoucí desetinnou čárkou.  
  
## <a name="return-value"></a>Návratová hodnota  
 `erf` Funkce vrátit gaussech Chyba funkce `x`. `erfc` Funkce vrátí doplňkové gaussech Chyba funkce `x`.  
  
## <a name="remarks"></a>Poznámky  
 `erf` Funkce Vypočítat x, která je definována jako funkce gaussech Chyba:  
  
 ![Chyba funkce x](../../c-runtime-library/reference/media/crt_erf_formula.PNG "CRT_erf_formula")  
  
 Doplňkové funkce gaussech chyba je definován jako 1 - erf(x). `erf` Funkce vrátí hodnotu v rozsahu-1.0 1.0. Neexistuje žádný návratový chyby. `erfc` Funkce vrátí hodnotu v rozsahu 0 až 2. Pokud `x` je příliš velký pro `erfc`, `errno` proměnná je nastavená na `ERANGE`.  
  
 Protože C++ umožňuje, aby přetížení, můžete volat přetížení `erf` a `erfc` , přijmout a vrátit `float` a `long double` typy. V programu C `erf` a `erfc` vždy přijmout a vrátit `double`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`erf`, `erff`, `erfl`, `erfc`, `erfcf`, `erfcl`|\<Math.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)