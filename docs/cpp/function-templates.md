---
title: Šablony funkcí
ms.date: 07/15/2019
helpviewer_keywords:
- function templates
- templates, function
- function templates, about function templates
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
ms.openlocfilehash: d430ad7650ffa47f0d6334a827b416cfb05ae6c2
ms.sourcegitcommit: fd466f2e14ad001f52f3dbe54f46d77be10f2d7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894363"
---
# <a name="function-templates"></a>Šablony funkcí

Šablony třídy definují skupinu souvisejících tříd, které jsou založeny na typech argumentů předaných při vytváření instance třídy. Šablony funkce jsou podobné jako šablony třídy, ale definují skupinu funkcí. Pomocí šablon funkce lze určit sadu funkcí, které jsou založeny na stejném kódu, ale pracují s různými typy nebo třídami. Následující šablona funkce zamění dvě položky:

```cpp
// function_templates1.cpp
template< class T > void MySwap( T& a, T& b ) {
   T c(a);
   a = b;
   b = c;
}
int main() {
}
```

Tento kód definuje skupinu funkcí, které zamění hodnoty argumentů. Z této šablony lze vytvořit funkce, které budou provádět záměnu **int** a **dlouhé** typy a také uživatelem definovaných typů. Šablona funkce `MySwap` dokonce provede záměnu tříd, pokud je správně definován kopírovací konstruktor a operátor přiřazení těchto tříd.

Kromě toho šablony funkce zabrání v záměně objektů různých typů, protože kompilátor zná typy *a* a *b* parametry v době kompilace.

Přestože lze tuto funkci pomocí ukazatelů typu void provést pomocí nešablonové funkce, verze s šablonou je typově bezpečná. Vezměte v úvahu následující volání:

```cpp
int j = 10;
int k = 18;
CString Hello = "Hello, Windows!";
MySwap( j, k );          //OK
MySwap( j, Hello );      //error
```

Druhé volání funkce `MySwap` vyvolá chybu v době kompilace, protože kompilátor nemůže funkci `MySwap` vygenerovat s parametry různých typů. Pokud byly použity ukazatele typu void, obě volání funkce se zkompilují správně, ale tato funkce nebude v době spuštění fungovat správně.

Explicitní určení argumentů šablony pro šablonu funkce je povoleno. Příklad:

```cpp
// function_templates2.cpp
template<class T> void f(T) {}
int main(int j) {
   f<char>(j);   // Generate the specialization f(char).
   // If not explicitly specified, f(int) would be deduced.
}
```

Pokud je argument šablony explicitně zadán, jsou provedeny normální implicitní převody pro převod argumentu funkce na typ odpovídající parametrům šablony funkce. Ve výše uvedeném příkladu kompilátor převede `j` na typ **char**.

## <a name="see-also"></a>Viz také:

[Šablony](../cpp/templates-cpp.md)<br/>
[Vytváření instancí šablon funkce](../cpp/function-template-instantiation.md)<br/>
[Explicitní vytvoření instance](../cpp/explicit-instantiation.md)<br/>
[Explicitní specializace šablon funkcí](../cpp/explicit-specialization-of-function-templates.md)