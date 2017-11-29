---
title: "Kompilátoru (úroveň 4) upozornění C4564 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4564
dev_langs: C++
helpviewer_keywords: C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 43462a2ea15ea50306b346d02a149a185cee902f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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