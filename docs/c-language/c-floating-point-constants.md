---
title: Konstanty jazyka C s plovoucí desetinnou čárkou | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3608e40db2aa3eb0c49942de278c1d428e26689f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="c-floating-point-constants"></a>Konstanty jazyka C s plovoucí desetinnou čárkou
"S plovoucí desetinnou čárkou konstanta" je desetinné číslo představující podepsaný reálné číslo. Reprezentace podepsaný reálné číslo zahrnuje celočíselnou část, zlomkové části a exponentem. Konstanty s plovoucí desetinnou čárkou znázornit s plovoucí desetinnou čárkou, které nelze změnit.  
  
## <a name="syntax"></a>Syntaxe  
 *Konstanta floating point*:  
 &nbsp;&nbsp; *exponent částí zlomkové konstanta*<sub>výslovný</sub> *plovoucí příponu*<sub>opt</sub>  
 &nbsp;&nbsp; *plovoucí exponent část číslice pořadí přípona*<sub>opt</sub>  
  
 *desetinná konstanta*:  
 &nbsp;&nbsp; *pořadí číslice*<sub>opt</sub> **.** *pořadí číslice*  
 &nbsp;&nbsp; *pořadí číslice***.**   
  
 *exponent část*:  
 &nbsp;&nbsp; **e***přihlašovací*<sub>opt</sub> *pořadí číslice*   
 &nbsp;&nbsp; **E***přihlašovací*<sub>opt</sub> *pořadí číslice*   
  
 *přihlašovací* : jeden z  
 &nbsp;&nbsp; **+ -**  
  
 *pořadí číslice*:  
 &nbsp;&nbsp; *Číslice*  
 &nbsp;&nbsp; *pořadí číslice číslice*  
  
 *plovoucí příponu* : jeden z  
 &nbsp;&nbsp; **f l F L**  
  
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