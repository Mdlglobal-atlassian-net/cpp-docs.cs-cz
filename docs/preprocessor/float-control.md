---
title: float_control – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
dev_langs:
- C++
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7ac671c938b80fc69b8214456efecf798e1e5f6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="floatcontrol"></a>float_control
Určuje s plovoucí desetinnou čárkou chování pro funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>Příznaky  
 `value`, `setting` **[nabízené]**  
 Určuje chování s plovoucí desetinnou čárkou. `value` může být **přesné** nebo **s výjimkou**. Další informace najdete v tématu [/fp (zadejte Floating-Point chování)](../build/reference/fp-specify-floating-point-behavior.md). `setting` lze buď **na** nebo **vypnout**.  
  
 Pokud `value` je **přesné**, nastavení pro **přesné** a **s výjimkou** jsou specifikované. **s výjimkou** lze nastavit pouze **na** při **přesné** je také nastavena na **na**.  
  
 Pokud volitelné **nabízené** token se přidá, aktuální nastavení pro `value` vložena do zásobníku vnitřní kompilátoru.  
  
 **push**  
 Nabízená aktuální `float_control` nastavení k zásobníku vnitřní kompilátoru  
  
 **POP**  
 Odebere `float_control` nastavení z horní části zásobníku vnitřní kompilátoru a který zpřístupňuje nové `float_control` nastavení.  
  
## <a name="remarks"></a>Poznámky  
 Nelze zapnout `float_control precise` vypnout při **s výjimkou** zapnutý. Podobně **přesné** kdy nelze vypnout `fenv_access` zapnutý. Přechod od striktní modelu k rychlé model se `float_control` – Direktiva pragma, použijte následující kód:  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
```  
  
 Přechod od rychlé modelu striktní modelu s `float_control` – Direktiva pragma, použijte následující kód:  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
```  
  
 Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:  
  
-   [fenv_access](../preprocessor/fenv-access.md)  
  
-   [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zachytit výjimku přetečení s plovoucí desetinnou čárkou s použitím – Direktiva pragma `float_control`.  
  
```  
// pragma_directive_float_control.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <float.h>  
  
double func( ) {  
   return 1.1e75;  
}  
  
#pragma float_control (except,on)  
  
int main( ) {  
   float u[1];  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);  
   if (err != 0)  
      printf_s("_controlfp_s failed!\n");  
  
   try  {  
      u[0] = func();  
      printf_s ("Fail");     
      return(1);  
   }   
  
   catch (...)  {  
      printf_s ("Pass");  
      return(0);  
   }  
}  
```  
  
```Output  
Pass  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
