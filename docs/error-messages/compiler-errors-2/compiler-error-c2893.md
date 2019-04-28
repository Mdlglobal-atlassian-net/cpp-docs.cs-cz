---
title: Chyba kompilátoru C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: f1fad1ad18af54945ef32dadaac50a6de4dbd62f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366378"
---
# <a name="compiler-error-c2893"></a>Chyba kompilátoru C2893

Nepovedlo se specializovat šablonu funkcí "název šablony.

Kompilátor nepovedlo se specializovat šablonu funkce. Může existovat mnoho příčiny této chyby.

Obecně platí je způsob, jak vyřešit chybu C2893 kontrolovat signatury funkce a ujistěte se, že každý typ lze vytvořit instanci.

## <a name="example"></a>Příklad

C2893 dochází, protože `f`pro parametr šablony `T` je rozpoznán jako `std::map<int,int>`, ale `std::map<int,int>` nemá žádný člen `data_type` (`T::data_type` nelze vytvořit instanci s `T = std::map<int,int>`.). Následující ukázka generuje C2893.

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