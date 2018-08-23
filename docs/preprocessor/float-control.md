---
title: float_control | Dokumentace Microsoftu
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
ms.openlocfilehash: b9b94e5b8eccdc63735c7cb25faa7eacb1e23670
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465300"
---
# <a name="floatcontrol"></a>float_control
Určuje chování plovoucí desetinné čárky pro funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>Příznaky  
 
*Hodnota*, *nastavení* *[nabízených]*  
Určuje chování plovoucí desetinné čárky. *Hodnota* může být `precise` nebo `except`. Další informace najdete v tématu [/fp (určení chování plovoucí desetinné čárky)](../build/reference/fp-specify-floating-point-behavior.md). *nastavení* může být buď `on` nebo `off`.  
  
Pokud *hodnotu* je `precise`, nastavení `precise` a `except` jsou zadané. `except` lze nastavit pouze `on` při `precise` je také nastavena na `on`.  
  
Pokud volitelný *nabízených* token se přidá, aktuální nastavení pro *hodnotu* je vloženo do zásobníku vnitřního kompilátoru.  
  
*push*  
Nabízená aktuální **float_control** nastavení do vnitřního zásobníku kompilátoru  
  
*POP*  
Odebere **float_control** nastavení z vrcholu vnitřního zásobníku kompilátoru a, která umožňuje novou **float_control** nastavení.  
  
## <a name="remarks"></a>Poznámky  
 
Nedá se zase `float_control precise` vypnuté, kdy `except` zapnutý. Obdobně `precise` nelze vypnout, kdy `fenv_access` zapnutý. Přejít od modelu striktní rychlé modelu s **float_control** – Direktiva pragma, použijte následující kód:  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
```  
  
Přejít od modelu rychlé striktní modelu s **float_control** – Direktiva pragma, použijte následující kód:  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
```  
  
Mezi další direktivy pragma pro čísla s plovoucí desetinnou čárkou patří:  
  
- [fenv_access](../preprocessor/fenv-access.md)  
  
- [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>Příklad  
 
Následující příklad ukazuje, jak zachytit výjimku přetečení s plovoucí desetinnou čárkou pomocí direktivy pragma **float_control**.  
  
```cpp  
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
