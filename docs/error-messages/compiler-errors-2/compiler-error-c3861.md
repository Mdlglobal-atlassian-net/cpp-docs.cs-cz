---
title: "C3861 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3861
dev_langs: C++
helpviewer_keywords: C3861
ms.assetid: 0a1eee30-b3db-41b1-b1e5-35949c3924d7
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d515c112c94024f123ee712b674b668b0c62287d
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="compiler-error-c3861"></a>C3861 chyby kompilátoru

> '*identifikátor*': nebyl nalezen identifikátor  
  
Kompilátor nebylo možné přeložit odkaz na identifikátor, i pomocí vyhledávání závislého na argumentu.  
  
Chcete-li tuto chybu opravit, porovnejte použití *identifikátor* identifikátor deklaraci pro případ a pravopis. Ověřte, že [oboru rozlišení operátory](../../cpp/scope-resolution-operator.md) a obor názvů [pomocí direktiv](../../cpp/namespaces-cpp.md#using_directives) používají správně. Pokud je identifikátor deklarován v záhlaví souboru, ověření hlavičku zahrnuté před identifikátor odkazuje. Pokud identifikátor měl by být externě viditelné, ujistěte se, že je deklarovaná ve zdrojovém souboru, který se používá. Také zkontrolujte, jestli není vyloučený identifikátor deklarace a definice [Podmíněná kompilace direktivy](../../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md). 

Změny k odebrání zastaralé funkce běhové knihovny jazyka C v sadě Visual Studio 2015 může způsobit C3861. Chcete-li tuto chybu vyřešit, odebrat odkazy na tyto funkce nebo je nahradit jejich zabezpečený alternativy, pokud existuje. Další informace najdete v tématu [zastaralé funkce](../../c-runtime-library/obsolete-functions.md).  

Pokud se zobrazí chyba C3861 po migraci projektu ze starších verzí kompilátor, můžete mít problémy související s podporovanou verzí Windows. Visual C++ již nepodporuje cílení systému Windows 95, Windows 98, Windows ME, Windows NT nebo Windows 2000. Pokud vaše maker WINVER a _WIN32_WINNT přiřazené na jednu z těchto verzí systému Windows, musíte upravit makra. Další informace najdete v tématu [úprava WINVER a _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md).
  
## <a name="example"></a>Příklad  

Následující ukázka generuje C3861, protože identifikátor není definován.  
  
```cpp  
// C3861.cpp  
void f2(){}  
int main() {  
   f();    // C3861  
   f2();   // OK  
}  
```  
  
## <a name="example"></a>Příklad  

Následující ukázka generuje C3861, protože identifikátor je viditelné v oboru souboru jeho definice, pouze pokud je deklarovaná v jiné zdrojové soubory, které ho používají.  
  
```cpp  
// C3861_a1.cpp
// Compile with: cl /EHsc /W4 C3861_a1.cpp C3861_a2.cpp  
#include <iostream>
// Uncomment the following line to fix:
// int f();  // declaration makes external function visible
int main() {  
   std::cout << f() << std::endl;    // C3861
}  
```  
  
```cpp  
// C3861_a2.cpp  
int f() {  // declared and defined here
   return 42;  
}
```  
  
## <a name="example"></a>Příklad  

Třídy výjimek ve standardní knihovně C++ vyžadují `std` oboru názvů.  
  
```cpp  
// C3861_b.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   try {  
      throw exception("Exception");   // C3861  
      // try the following line instead  
      // throw std::exception("Exception");  
   }  
   catch (...) {  
      std::cout << "caught an exception" << std::endl;  
   }  
}  
```  
## <a name="example"></a>Příklad  

Zastaralé funkce byly odebrány z knihovny CRT.  
  
```cpp  
// C3861_c.cpp  
#include <stdio.h>  
int main() {  
   char line[21]; // room for 20 chars + '\0'  
   gets( line );  // C3861  
   // Use gets_s instead.  
   printf( "The line entered was: %s\n", line );  
}  
```
Následující ukázka generuje C3767, protože kompilátor pro FriendFunc nelze použít argument závislé vyhledávání:  
  
```  
namespace N {  
   class C {  
      friend void FriendFunc() {}  
      friend void AnotherFriendFunc(C* c) {}  
   };  
}  
  
int main() {  
   using namespace N;  
   FriendFunc();   // C3861 error  
   C* pC = new C();  
   AnotherFriendFunc(pC);   // found via argument-dependent lookup  
}  
```  
  
Opravte chybu, deklarovat friend v rozsahu třídy a definovat v oboru názvů:  
  

MyClass {– třída  
   int m_private;  
   Friend void func();  
};  
  
{void func()  
   MyClass s;  
   s.m_private = 0;  
}  
  
int main() {  
   Func();  
}  