---
title: "C3771 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3771
dev_langs:
- C++
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1f552eee7ac20c086240a4ce79fd3616127268b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3771"></a>C3771 chyby kompilátoru
"identifikátor": deklarace friend nebyl nalezen v nejbližší oboru názvů  
  
Deklarace třídy šablony pro zadanou šablonu *identifikátor* nebyl nalezen v aktuálním oboru názvů.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, že deklaraci třídy šablony pro identifikátor šablony je definována v aktuálním oboru názvů nebo že identifikátor šablony je plně kvalifikovaný název.  
  
## <a name="example"></a>Příklad  
Následující příklad kódu deklaruje šablona třídy a funkce v oboru názvů `NA`, ale pokusí se deklarovat šablonu funkce friend v oboru názvů `NB`.  
  
```cpp  
// C3771.cpp   
// compile with: /c  
  
namespace NA {  
template<class T> class A {  
    void aFunction(T t) {};  
    };  
}  
// using namespace NA;  
namespace NB {  
    class X {  
        template<class T> friend void A<T>::aFunction(T); // C3771  
// try the following line instead  
//      template<class T> friend void NA::A<T>::aFunction(T);  
// or try "using namespace NA;" instead.  
    };  
}  
```  
  
## <a name="see-also"></a>Viz také  
[Šablony](../../cpp/templates-cpp.md)  