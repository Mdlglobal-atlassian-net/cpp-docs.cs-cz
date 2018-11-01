---
title: Chyba kompilátoru C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: df0f656c9db23739ec62629088b9cc5f7950a92d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570440"
---
# <a name="compiler-error-c2672"></a>Chyba kompilátoru C2672

> "*funkce*': žádná odpovídající Přetížená funkce nalezen

Kompilátor nemůže najít přetížené funkce, který odpovídá zadané funkce. Žádná funkce nebyla nalezena, má odpovídající parametry, nebo žádná odpovídající funkce má požadované usnadnění přístupu v kontextu.

Při použití určitých kontejnery standardní knihovny nebo algoritmů, musíte zadat vaše typy dostupné členy nebo spřátelené funkce, které splňují požadavky kontejneru nebo algoritmus. Například vaše typy iterátoru musí být odvozený z: `std::iterator<>`. Operace porovnání nebo použití jiných operátorů na typy elementů kontejneru může vyžadovat považovat za typ jako levé straně a zpracovával pravý operand. Použití typu zpracovával pravý operand může vyžadovat implementace operátoru jako funkce bez členů typu.

## <a name="example"></a>Příklad

Verze kompilátoru Visual Studio 2017 neprovedli přístup kontrolujeme kvalifikované názvy v některých kontextech šablony. To může narušit očekávané chování SFINAE, kde se očekává selhat z důvodu inaccessibility název nahrazení. To může potenciálně způsobit selhání nebo neočekávané chování za běhu z důvodu kompilátor nesprávně volání nesprávné přetížení operátoru. V sadě Visual Studio 2017 se vyvolá chybu kompilátoru.

V tomto příkladu zkompiluje ve Visual Studiu 2015 ale vyvolá chybu v sadě Visual Studio 2017. Chcete tento problém vyřešit, upravte člena parametr šablony přístupné, kde je vyhodnocen.

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```