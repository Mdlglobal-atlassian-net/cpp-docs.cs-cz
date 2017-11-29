---
title: "fp_contract – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 95b7e8e4147e168cb36e8a5e4be023def6960a4f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fpcontract"></a>fp_contract
Určuje, zda bude prováděno zkracování čísel s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma fp_contract [ON | OFF]  
```  
  
## <a name="remarks"></a>Poznámky  
 Parametr `fp_contract` je standardně ON (zapnutý).  
  
 Další informace o s plovoucí desetinnou čárkou chování najdete v tématu [/fp (zadejte Floating-Point chování)](../build/reference/fp-specify-floating-point-behavior.md).  
  
 Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:  
  
-   [fenv_access –](../preprocessor/fenv-access.md)  
  
-   [float_control –](../preprocessor/float-control.md)  
  
## <a name="example"></a>Příklad  
 Kód, který vygenerovala od této ukázky nepoužívá začleněny násobení přidat (**FMA –**) instrukcí na procesory Itanium. Pokud jste komentář `#pragma fp_contract (off)`, generovaný kód bude používat **FMA –** instrukcí.  
  
```  
// pragma_directive_fp_contract.cpp  
// compile with: /O2  
#include <stdio.h>  
#include <float.h>  
  
#pragma fp_contract (off)   
  
int main() {  
   double z, b, t;  
  
   for (int i = 0; i < 10; i++) {  
      b = i * 5.5;  
      t = i * 56.025;  
      _set_controlfp(_PC_24, _MCW_PC);  
  
      z = t * i + b;  
      printf_s ("out=%.15e\n", z);  
   }  
}  
```  
  
```Output  
out=0.000000000000000e+000  
out=6.152500152587891e+001  
out=2.351000061035156e+002  
out=5.207249755859375e+002  
out=9.184000244140625e+002  
out=1.428125000000000e+003  
out=2.049899902343750e+003  
out=2.783724853515625e+003  
out=3.629600097656250e+003  
out=4.587524902343750e+003  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)