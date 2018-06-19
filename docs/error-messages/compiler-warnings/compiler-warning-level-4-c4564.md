---
title: Kompilátoru (úroveň 4) upozornění C4564 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4564
dev_langs:
- C++
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f0cf68eb75d420a0d23c04687d4f9492910b53f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293670"
---
# <a name="compiler-warning-level-4-c4564"></a>C4564 kompilátoru upozornění (úroveň 4)
Metoda metodu třídy 'class'. definuje nepodporované výchozí parametr "parametr"  
  
 Kompilátor zjištěna metodu s jeden nebo více parametrů s výchozími hodnotami. Výchozí hodnoty pro parametry budou ignorovány, když je volána metoda; explicitně zadáte hodnoty pro tyto parametry. Pokud nezadáte explicitně hodnoty těchto parametrů, C++ compiler dojde k chybě.  
  
 Zadaný následující .dll vytvořit pomocí jazyka Visual Basic, který umožňuje výchozí parametry v metoda argumenty:  
  
```  
' C4564.vb  
' compile with: vbc /t:library C4564.vb  
Public class TestClass  
   Public Sub MyMethod (a as Integer, _  
                        Optional c as Integer=1)  
   End Sub  
End class  
```  
  
 A následující ukázka C++, který používá .dll vytvořit pomocí jazyka Visual Basic  
  
```  
// C4564.cpp  
// compile with: /clr /W4 /WX  
#using <C4564.dll>  
  
int main() {  
   TestClass ^ myx = gcnew TestClass();   // C4564  
   myx->MyMethod(9);  
   // try the following line instead, to avoid an error  
   // myx->MyMethod(9, 1);  
}  
```