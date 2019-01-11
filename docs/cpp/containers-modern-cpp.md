---
title: Kontejnery (moderní verze jazyka C++)
ms.date: 1/18/2018
ms.topic: conceptual
ms.openlocfilehash: 2da57bfca8b04f50a223dddfb886835c69f746a4
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220137"
---
# <a name="containers-modern-c"></a>Kontejnery (moderní verze jazyka C++)

Ve výchozím nastavení používají [vektoru](../standard-library/vector-class.md) jako upřednostňované sekvenční kontejner v jazyce C++. Jedná se o ekvivalent k `List<T>` v jazycích .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Použití [mapy](../standard-library/map-class.md) (ne `unordered_map`) jako výchozí asociativní kontejner. Použití [nastavit](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md), a [multiset](../standard-library/multiset-class.md) degenerovaných & více případů.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Když je potřeba optimalizace výkonu, zvažte použití:

- [Pole](../standard-library/array-class-stl.md) zadejte při vkládání je důležitý, například jako člen třídy.

- Například neuspořádané asociativní kontejnery [unordered_map](../standard-library/unordered-map-class.md). Mají nižší na element režii a vyhledávaní v konstantním čase, ale může být obtížnější použít správně a efektivně.

- Seřazené `vector`. Další informace najdete v tématu [algoritmy](../cpp/algorithms-modern-cpp.md).

Nepoužívejte pole stylu C. Pro starší rozhraní API, třeba přímý přístup k datům, použijte přístupové metody `f(vec.data(), vec.size());` místo.

Další informace o kontejnerech naleznete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět (moderní verze jazyka C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
