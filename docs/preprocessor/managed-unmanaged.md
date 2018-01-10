---
title: "spravované, nespravované | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
dev_langs: C++
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d8e2b50f7d505a4e262559b6cb69b0bab81ffcd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="managed-unmanaged"></a>managed, unmanaged
Povolení řízení na úrovni funkce pro kompilování funkcí jako spravovaných nebo nespravovaných.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      #pragma managed  
#pragma unmanaged  
#pragma managed([push,] on | off)  
#pragma managed(pop)  
```  
  
## <a name="remarks"></a>Poznámky  
 [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru poskytuje úroveň modulu řízení kompilaci funkce buď jako spravované nebo nespravované.  
  
 Nespravovaná funkce bude zkompilována pro nativní platformu a provádění části programu bude modulem CLR (Common Language Runtime) předáno nativní platformě.  
  
 Kompilované funkce jako spravovaný ve výchozím nastavení při **/CLR** se používá.  
  
 Při použití těchto direktivy:  
  
-   Přidání direktivy pragma před funkci, ale nikoliv do těla funkce.  
  
-   Přidat – Direktiva pragma po `#include` příkazy. Nepoužívejte tyto direktivy před `#include` příkazy.  
  
 Kompilátor ignoruje `managed` a `unmanaged` direktivy Pokud **/CLR** není použita při kompilaci.  
  
 Když je vytvořena instance funkce šablony, stav direktivy pragma v době definice šablony určuje, zda je spravovaná nebo nespravovaná.  
  
 Další informace najdete v tématu [inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md).  
  
## <a name="example"></a>Příklad  
  
```cpp  
// pragma_directives_managed_unmanaged.cpp  
// compile with: /clr  
#include <stdio.h>  
  
// func1 is managed  
void func1() {  
   System::Console::WriteLine("In managed function.");  
}  
  
// #pragma unmanaged  
// push managed state on to stack and set unmanaged state  
#pragma managed(push, off)  
  
// func2 is unmanaged  
void func2() {  
   printf("In unmanaged function.\n");  
}  
  
// #pragma managed  
#pragma managed(pop)  
  
// main is managed  
int main() {  
   func1();  
   func2();  
}  
```  
  
```Output  
In managed function.  
In unmanaged function.  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)