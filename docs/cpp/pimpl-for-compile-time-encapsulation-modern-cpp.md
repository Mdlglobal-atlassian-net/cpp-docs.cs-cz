---
title: Ukazatel na implementaci pro zapouzdření za kompilace (moderní verze jazyka C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e80c4bd86cd4c7400e3937fcb8d164fe6b14106
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404652"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Ukazatel na implementaci pro zapouzdření za kompilace (moderní verze jazyka C++)
*Ukazatel na implementaci idiom* je moderní C++ techniku ke skrytí implementace, chcete-li minimalizovat párování a k oddělení rozhraní. Ukazatel na implementaci je zkratka pro "ukazatel na implementaci." Může již být seznámení s konceptem, ale znáte jiné názvy jako idiom Cheshiru Cat nebo brány Firewall kompilátoru.  
  
## <a name="why-use-pimpl"></a>Proč používat ukazatel na implementaci?  
 Zde je, jak vylepšit idiom ukazatel na implementaci životního cyklu vývoje softwaru:  
  
-   Minimalizace závislostí kompilace.  
  
-   Oddělení rozhraní a implementaci.  
  
-   Přenositelnost.  
  
## <a name="pimpl-header"></a>Ukazatel na implementaci záhlaví  
  
```cpp  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
```  
  
 Idiom ukazatel na implementaci vyhýbá cascades opětovné sestavení a křehký objekt rozložení. Je vhodná pro (přechodně) oblíbených typů.  
  
## <a name="pimpl-implementation"></a>Ukazatel na implementaci implementace  
 Definovat `impl` třída v souboru .cpp.  
  
```cpp  
// my_class.cpp  
class my_class::impl {  // defined privately here  
  // ... all private data and functions: all of these  
  //     can now change without recompiling callers ...  
};  
my_class::my_class(): pimpl( new impl )  
{  
  // ... set impl values ...   
}  
```  
  
## <a name="best-practices"></a>Osvědčené postupy  
 Zvažte, jestli se má přidat podporu pro specializaci non-throwing. prohození.  
  
## <a name="see-also"></a>Viz také:  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)