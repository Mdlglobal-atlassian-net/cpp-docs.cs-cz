---
title: C2672 Chyba kompilátoru | Microsoft Docs
ms.date: 10/24/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2672
dev_langs:
- C++
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98c569c8b9b1466f184b44d345e76341d1476935
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2672"></a>C2672 chyby kompilátoru

> '*funkce*': funkce najít žádný odpovídající přetížený.

Přetížené funkce, která odpovídá zadanou funkci nelze nalézt kompilátoru. Nebyla nalezena žádná funkce, že trvá odpovídající parametry, nebo žádná odpovídající funkce má požadované usnadnění v kontextu.

Při použití určitých standardní knihovna kontejnery nebo algoritmy, musí vaše typy poskytovat dostupné členy nebo funkcí friend, které splňují požadavky na kontejneru nebo algoritmus. Například vaše iterator typy by měl být odvozen z `std::iterator<>`. Operace porovnání nebo použití jiných operátorů na typy elementů kontejner může vyžadovat typ považovat za levé a pravé operand. Použijte typu pravém operand může vyžadovat implementace operátoru jako funkce třetí typu.

## <a name="example"></a>Příklad

Verze kompilátoru než Visual Studio 2017 nebyla provedena kontrola na kvalifikované názvy v některých kontextech šablony přístup. To může narušovat očekávané chování sfinae u výrazů, kde je očekávána nahrazování selhání kvůli inaccessibility názvu. To může potenciálně způsobit selhání nebo neočekávané chování za běhu z důvodu kompilátoru nesprávně volání nesprávný přetížení operátoru. V aplikaci Visual Studio 2017 je vyvolána chyba kompilátoru.

Tento příklad zkompiluje v sadě Visual Studio 2015, ale vyvolá chybu v Visual Studio 2017. Chcete-li tento problém vyřešit, zkontrolujte parametr člen šablony, které jsou přístupné, kde je vyhodnocena.

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