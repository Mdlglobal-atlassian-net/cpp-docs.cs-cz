---
title: Chyba kompilátoru C3556
ms.date: 11/04/2016
f1_keywords:
- C3556
helpviewer_keywords:
- C3556
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
ms.openlocfilehash: 7b87f8c57b0d871a577793936ea3cb7dbab7e58d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531167"
---
# <a name="compiler-error-c3556"></a>Chyba kompilátoru C3556

> "*výraz*': nesprávný argument pro decltype"–"

Kompilátor nemůže odvodit typ výrazu, která je argumentem `decltype(` *výraz* `)` specifikátoru typu.

## <a name="example"></a>Příklad

V následujícím příkladu kódu, kompilátor nemůže odvodit typ `myFunction` argument protože `myFunction` je přetížena. Chcete-li vyřešit tento problém, můžete použít `static_cast` k vytvoření instance ukazatele na konkrétní Přetížená funkce. Pokud chcete zadat do `decltype` výrazu.

```cpp
// C3556.cpp
// compile with: cl /W4 /EHsc C3556.cpp
#include <iostream>

void myFunction(int);
void myFunction(float, float);

void callsMyFunction(decltype(myFunction) fn); // C3556
// One way to fix is to comment out the line above, and
// use static_cast to create specialized function pointer
// instances:
auto myFunctionInt = static_cast<void(*)(int)>(myFunction);
auto myFunctionFloatFloat = static_cast<void(*)(float,float)>(myFunction);
void callsMyFunction(decltype(myFunctionInt) fn, int n);
void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g);

void myFunction(int i) {
    std::cout << "called myFunction(" << i << ")" << std::endl;
}

void myFunction(float f, float g) {
    std::cout << "called myFunction(" << f << ", " << g << ")" << std::endl;
}

void callsMyFunction(decltype(myFunctionInt) fn, int n) {
    fn(n);
}

void callsMyFunction(decltype(myFunctionFloatFloat) fn, float f, float g) {
    fn(f, g);
}

int main() {
    callsMyFunction(myFunction, 42);
    callsMyFunction(myFunction, 0.1f, 2.3f);
}
```