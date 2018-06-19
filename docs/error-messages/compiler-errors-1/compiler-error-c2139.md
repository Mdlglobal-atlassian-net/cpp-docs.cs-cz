---
title: C2139 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2139
dev_langs:
- C++
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd56ee920d3f53b22d9979b45c39fa78b9054662
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169801"
---
# <a name="compiler-error-c2139"></a>C2139 chyby kompilátoru
'type': Nedefinovaná třída není povolen jako argumentu kompilátoru vnitřního typu znak 'znak.  
  
 Typ znak byl předán neplatný argument.  
  
 Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2139.  
  
```  
// C2139.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
struct is_polymorphic {  
   static const bool value = __is_polymorphic(T);  
};  
  
class C;  
class D {};  
  
class E {  
public:  
   virtual void Test() {}  
};  
  
int main() {  
   cout << is_polymorphic<C>::value << endl;   // C2139  
   cout << is_polymorphic<D>::value << endl;   // OK  
   cout << is_polymorphic<E>::value << endl;   // OK  
}  
```