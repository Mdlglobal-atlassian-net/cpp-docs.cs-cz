---
title: Chyba kompilátoru C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: 9f844b54285a7df69bfb4387a7afcc82dfef9252
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177128"
---
# <a name="compiler-error-c2672"></a>Chyba kompilátoru C2672

> '*Function*': nebyla nalezena žádná vyhovující přetížená funkce

Kompilátor nemůže najít přetíženou funkci, která odpovídá zadané funkci. Nenašla se žádná funkce, která přebírá odpovídající parametry, nebo žádná odpovídající funkce nemá v kontextu požadovanou přístupnost.

Při použití v určitých standardních kontejnerech nebo algoritmech knihovny musí vaše typy poskytovat přístupné členy nebo funkce Friend, které splňují požadavky kontejneru nebo algoritmu. Například typy iterátorů by měly odvozovat z `std::iterator<>`. Operace porovnání nebo použití jiných operátorů na typech kontejnerových prvků může vyžadovat, aby byl typ považován za levý a pravý operand. Použití typu jako operandu na pravé straně může vyžadovat implementaci operátoru jako nečlenskou funkci typu.

## <a name="example"></a>Příklad

Verze kompilátoru před aplikací Visual Studio 2017 neprováděly kontrolu přístupu k kvalifikovaným názvům v některých kontextech šablony. To může kolidovat s očekávaným chováním SFINAE, kde se očekává, že náhrada selže z důvodu nedostupnosti názvu. To může potenciálně způsobit selhání nebo neočekávané chování při běhu, protože kompilátor nesprávně volá nesprávné přetížení operátoru. V aplikaci Visual Studio 2017 je vyvolána chyba kompilátoru.

Tento příklad kompiluje v aplikaci Visual Studio 2015, ale vyvolává chybu v aplikaci Visual Studio 2017. Chcete-li tento problém vyřešit, zajistěte, aby byl člen parametru šablony přístupný tam, kde je vyhodnocen.

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
