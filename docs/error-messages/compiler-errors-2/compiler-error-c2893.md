---
title: C2893 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2893
dev_langs:
- C++
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db3b71a05ece6b79672d47699dc68e0eb5bb1f60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246695"
---
# <a name="compiler-error-c2893"></a>C2893 chyby kompilátoru
Nepodařilo se specializují šablony funkce "název šablony.  
  
 Specialize šablonu funkce kompilátoru se nezdařilo. Může být mnoho příčiny této chyby.  
  
 Obecně platí je způsob, jak vyřešit chyby C2893 zkontrolovat podpis funkce a ujistěte se, že každý typ můžete vytvořit instanci.  
  
## <a name="example"></a>Příklad  
 C2893 dochází `f`pro parametr šablony `T` není rozpoznán jako `std::map<int,int>`, ale `std::map<int,int>` nemá žádné člen `data_type` (`T::data_type` nelze vytvořit instanci s `T = std::map<int,int>`.). Následující ukázka generuje C2893.  
  
```  
// C2893.cpp  
// compile with: /c /EHsc  
#include<map>  
using namespace std;  
class MyClass {};  
  
template<class T>   
inline typename T::data_type  
// try the following line instead  
// inline typename  T::mapped_type  
f(T const& p1, MyClass const& p2);  
  
template<class T>  
void bar(T const& p1) {  
    MyClass r;  
    f(p1,r);   // C2893  
}  
  
int main() {  
   map<int,int> m;  
   bar(m);  
}  
```