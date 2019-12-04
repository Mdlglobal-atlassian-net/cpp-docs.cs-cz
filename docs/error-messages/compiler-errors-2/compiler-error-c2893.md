---
title: Chyba kompilátoru C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: ca603eb94d5d528a7fed15e0320e1f5d88bf0629
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760873"
---
# <a name="compiler-error-c2893"></a>Chyba kompilátoru C2893

Nepovedlo se specializovat šablonu funkce – název šablony

Kompilátor nemohl provést specializaci šablony funkce. Tato chyba může mít mnoho příčin.

Obecně se způsob, jak vyřešit chybu C2893, je zkontrolovat signatura funkce a ujistit se, že je možné vytvořit instanci každého typu.

## <a name="example"></a>Příklad

K C2893 dochází, protože parametr šablony `f``T` je odvozen `std::map<int,int>`, ale `std::map<int,int>` nemá žádného člena `data_type` (`T::data_type` nelze vytvořit instanci s `T = std::map<int,int>`.). Následující ukázka generuje C2893.

```cpp
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
