---
title: "C3162 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3162
dev_langs: C++
helpviewer_keywords: C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8c3526eecbe125a1a76b637734fecc72785556b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3162"></a>C3162 chyby kompilátoru
'type': odkaz na typ, který má destruktor nelze použít jako typ člena statických dat "člen"  
  
 Modul common language runtime nemůže vědět, kdy spustit destruktor definovaný uživatelem, když třída také obsahuje funkce statický člen.  
  
 Pokud je tento objekt odstranit, explicitně nikdy spouštěna destruktor.  
  
 Další informace najdete v tématu,  
  
-   [/ CLR (kompilace common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Obecné problémy migrace v 64bitovém prostředí Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3162.  
  
```  
// C3162.cpp  
// compile with: /clr /c  
ref struct A {  
   ~A() { System::Console::WriteLine("in destructor"); }  
   static A i;   // C3162  
   static A^ a = gcnew A;   // OK  
};  
  
int main() {  
   A ^ a = gcnew A;  
   delete a;  
}  
```