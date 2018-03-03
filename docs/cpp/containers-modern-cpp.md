---
title: "Kontejnery (moderní verze jazyka C++) | Microsoft Docs"
ms.custom: 
ms.date: 1/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d43570f644e9627de5a40fc5b824a17e4fd33ffc
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2018
---
# <a name="containers-modern-c"></a>Kontejnery (moderní verze jazyka C++)

Ve výchozím nastavení používají [vektoru](../standard-library/vector-class.md) jako upřednostňovaný sekvenční kontejneru v jazyce C++. Jde o ekvivalent `List<T>` v jazycích .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Použití [mapy](../standard-library/map-class.md) (ne `unordered_map`) jako výchozího kontejneru asociativní. Použití [nastavit](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md), a [multiset](../standard-library/multiset-class.md) degenerovanou & více případech.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Optimalizace výkonu je potřeba, zvažte použití:

- [Pole](../standard-library/array-class-stl.md) zadat, když je důležitá, například jako člena třídy vkládání.

- Neuspořádané asociativní kontejnery, jako [unordered_map](../standard-library/unordered-map-class.md). Tyto mít nižší za element režii a běhu konstanta vyhledávání, ale může být obtížnější použít správné a efektivní.

- Seřadit **vektoru**. Další informace najdete v tématu [algoritmy](../cpp/algorithms-modern-cpp.md).

Nepoužívejte stylu jazyka C pole. Pro starší rozhraní API, třeba přímý přístup k datům, pomocí metod `f(vec.data(), vec.size());` místo.

Další informace o kontejnery najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

## <a name="see-also"></a>Viz také

[C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)  
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)  
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)  
