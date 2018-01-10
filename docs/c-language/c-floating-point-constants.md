---
title: "Konstanty jazyka C s plovoucí desetinnou čárkou | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67883acbb2a6d5c0df075c47b7eda0d40a568f38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-floating-point-constants"></a>Konstanty jazyka C s plovoucí desetinnou čárkou
"S plovoucí desetinnou čárkou konstanta" je desetinné číslo představující podepsaný reálné číslo. Reprezentace podepsaný reálné číslo zahrnuje celočíselnou část, zlomkové části a exponentem. Konstanty s plovoucí desetinnou čárkou znázornit s plovoucí desetinnou čárkou, které nelze změnit.  
  
## <a name="syntax"></a>Syntaxe  
 *Konstanta floating point*:  
 &nbsp;&nbsp;*zlomkové konstanta exponent – část*<sub>opt</sub> *plovoucí příponu*<sub>opt</sub>  
 &nbsp;&nbsp;*plovoucí exponent část číslice pořadí přípona*<sub>opt</sub>  
  
 *desetinná konstanta*:  
 &nbsp;&nbsp;*číslice pořadí*<sub>opt</sub> **.** *pořadí číslice*  
 &nbsp;&nbsp;*číslice pořadí***.**   
  
 *exponent část*:  
 &nbsp;&nbsp;**e***přihlašovací*<sub>opt</sub> *pořadí číslice*   
 &nbsp;&nbsp;**E***přihlašovací*<sub>opt</sub> *pořadí číslice*   
  
 *přihlašovací* : jeden z  
 &nbsp;&nbsp; **+ -**  
  
 *pořadí číslice*:  
 &nbsp;&nbsp;*číslice*  
 &nbsp;&nbsp;*číslice pořadí číslice*  
  
 *plovoucí příponu* : jeden z  
 &nbsp;&nbsp;**L l F f**  
  
 Je možné vynechat buď číslic od desetinné čárky (celočíselnou část hodnoty) nebo číslice za desetinnou čárkou (část), ale ne pomocí obou. Můžete ponechat si desetinné čárky pouze v případě, že zahrnují exponentem. Bez prázdných znaků můžete oddělit číslic nebo znaků, konstanty.  
  
 Následující příklady ilustrují některé formy konstanty s plovoucí desetinnou čárkou a výrazy:  
  
```  
15.75  
1.575E1   /* = 15.75   */  
1575e-2   /* = 15.75   */  
-2.5e-3   /* = -0.0025 */  
25E-4     /* =  0.0025 */  
```  
  
 Konstanty s plovoucí desetinnou čárkou jsou kladné, pokud jsou uvozená znakem minus (**-**). V takovém případě mínus považován za operátor unární aritmetické negace. Konstanty s plovoucí desetinnou čárkou mít typ `float`, `double`, nebo `long double`.  
  
 Konstanty s plovoucí desetinnou čárkou bez **f**, **F**, **l**, nebo **L** příponu má typ `double`. Pokud písmeno **f** nebo **F** je přípona, má typ konstanta `float`. Pokud na konci písmenem **l** nebo **L**, má typ `long double`. Příklad:  
  
```  
100L  /* Has type long double  */  
100F  /* Has type float        */  
```  
  
 Všimněte si, že Microsoft C kompilátoru interně představuje `long double` stejný jako typ `double`. V tématu [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o typu `double`, `float`, a `long double`.  
  
 Část celé číslo s plovoucí desetinnou čárkou konstantu, můžete vynechat, jak je znázorněno v následujících příkladech. Číslo.75 může být vyjádřený v mnoha způsoby, včetně následujících:  
  
```  
.0075e2  
0.075e1  
.075e1  
75e-2  
```  
  
## <a name="see-also"></a>Viz také  
 [Konstanty jazyka C](../c-language/c-constants.md)