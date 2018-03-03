---
title: "Pimpl pro zapouzdření kompilaci (moderní verze jazyka C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a109015f3d30b04eaf89e769e1265c49663599f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Ukazatel na implementaci pro zapouzdření za kompilace (moderní verze jazyka C++)
*Pimpl stylu* jde o techniku moderní C++ skrýt implementace, chcete-li minimalizovat párování a k oddělení rozhraní. Pimpl je zkratka pro "ukazatel na implementaci." Může už se seznamte s koncept, ale víte, že jiné názvy jako Cheshiru Cat nebo brány Firewall kompilátoru stylu.  
  
## <a name="why-use-pimpl"></a>Proč používat pimpl?  
 Zde je, jak stylu pimpl vylepšit životního cyklu softwaru:  
  
-   Minimalizace kompilace závislosti.  
  
-   Oddělení rozhraní a implementace.  
  
-   Přenositelnost.  
  
## <a name="pimpl-header"></a>Pimpl záhlaví  
  
```cpp  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
  
```  
  
 Stylu pimpl zabraňuje cascades opětovné sestavení a rozložení křehká objektu. Dobře je vhodná pro typy (přechodně) oblíbených.  
  
## <a name="pimpl-implementation"></a>Implementace Pimpl  
 Definování `impl` – třída v souboru.  
  
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
  
## <a name="best-practices"></a>Doporučené postupy  
 Zvažte, jestli se má přidat podporu pro jiný vyvolávání specializace odkládacího souboru.  
  
## <a name="see-also"></a>Viz také  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)