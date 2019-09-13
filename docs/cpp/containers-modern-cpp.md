---
title: Kontejnery (moderní verze jazyka C++)
ms.date: 01/18/2018
ms.topic: conceptual
ms.openlocfilehash: 37b540132fc9ddc03d5eaafd33c545b5db5e7935
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926250"
---
# <a name="containers-modern-c"></a>Kontejnery (moderní verze jazyka C++)

Ve výchozím nastavení použijte [Vector](../standard-library/vector-class.md) jako preferovaný sekvenční kontejner v C++. Toto je ekvivalent `List<T>` v jazycích .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Použijte [mapu](../standard-library/map-class.md) (ne `unordered_map`) jako výchozí asociativní kontejner. Použijte [set](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md)a [multiset](../standard-library/multiset-class.md) pro vygenerování & více případů.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Když je potřeba optimalizace výkonu, zvažte použití:

- Typ [pole](../standard-library/array-class-stl.md) , když je vkládání důležité, například jako člen třídy.

- Neuspořádané asociativní kontejnery, například [unordered_map](../standard-library/unordered-map-class.md). Ty mají nižší režijní náklady na prvky a vyhledávání v čase, ale mohou být těžší používat správně a efektivně.

- Seřazeno `vector`. Další informace najdete v tématu [algoritmy](../cpp/algorithms-modern-cpp.md).

Nepoužívejte pole ve stylu jazyka C. U starších rozhraní API, která potřebují přímý přístup k datům, použijte místo toho přístupové `f(vec.data(), vec.size());` metody, jako je například.

Další informace o kontejnerech naleznete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět (moderní verze jazyka C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
