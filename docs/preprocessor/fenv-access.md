---
title: "fenv_access – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d2f95187be09177fea573181f1e3a827409fb77c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fenvaccess"></a>fenv_access
Zakáže (zapnuto) nebo povolí (optimalizace, které může změnit příznak testy a změny v režimu vypnuto).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma fenv_access [ON | OFF]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `fenv_access` je VYPNUTÝ.  
  
 Další informace o s plovoucí desetinnou čárkou chování najdete v tématu [/fp (zadejte Floating-Point chování)](../build/reference/fp-specify-floating-point-behavior.md).  
  
 Druhy optimalizace, které podléhají `fenv_access` jsou:  
  
-   Globální eliminace společných dílčích výrazů  
  
-   Kód pohybu  
  
-   Konstantní skládání  
  
 Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:  
  
-   [float_control –](../preprocessor/float-control.md)  
  
-   [fp_contract –](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>Příklad  
  
```  
// pragma_directive_fenv_access_x86.cpp  
// compile with: /O2  
// processor: x86  
#include <stdio.h>  
#include <float.h>   
#include <errno.h>  
#pragma fenv_access (on)  
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
```Output  
out=9.999999776482582e-003  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad je kompilátoru vytváření výstupních souborů pro procesory Itanium. **/FP: přesné** uchová mezilehlých výsledků rozšířené přesnost, kde hodnoty vyšší než flt_max – (3.402823466e + 38F), lze vypočítat a v důsledku tohoto součtu bude mít 1.0 výsledek, jako by měl pokud ručně vypočítat. **/FP: striktní** udržuje mezilehlé výsledky v jejich přesnost zdroje (float), takže první přidání vytváří infinity, který je uložen v rámci výrazu.  
  
```  
// pragma_directive_fenv_access_IPF.cpp  
// compile with: /O2 /fp:precise  
// processor: IPF  
// compiling with /fp:precise prints 1.0F  
// compile with /fp:strict to print infinity  
  
#include <stdio.h>  
float arr[5] = {3.402823465e+38F,   
               3.402823462e+38F,  
               3.402823464e+38F,  
               3.402823463e+38F,  
               1.0F};  
  
int main() {  
   float sum = 0;  
   sum = arr[0] + arr[1] - arr[2] - arr[3] + arr[4];  
   printf_s("%f\n", sum);  
}  
```  
  
```Output  
1.000000  
```  
  
## <a name="example"></a>Příklad  
 Při psaní komentářů se `#pragma fenv_access (on)` od předchozího vzorku, Všimněte si, že výstup různých kvůli kompilátor vyhodnocení kompilaci, který nepoužívá režim ovládacího prvku.  
  
```  
// pragma_directive_fenv_access_2.cpp  
// compile with: /O2  
#include <stdio.h>  
#include <float.h>   
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
```Output  
out=1.000000000000000e-002  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)