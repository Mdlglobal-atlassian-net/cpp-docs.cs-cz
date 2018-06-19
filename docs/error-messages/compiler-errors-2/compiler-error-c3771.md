---
title: C3771 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3771
dev_langs:
- C++
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8adfdb1562cc9efbe208bd7c887b7c4aa77ddd82
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272542"
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