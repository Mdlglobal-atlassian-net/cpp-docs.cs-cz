---
title: Prostředky ve vlastnictví objektů (RAII)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f86b484e-5a27-4c3b-a92a-dfaa5dd6d93a
ms.openlocfilehash: a10d6c2177c391ead6065767994b09fb6236ee3a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593606"
---
# <a name="objects-own-resources-raii"></a>Prostředky ve vlastnictví objektů (RAII)

Ujistěte se, že objekty vlastní prostředky. Tento princip se označuje také jako "získávání prostředků je inicializace" nebo "RAII."

## <a name="example"></a>Příklad

Každý "nové" objekt předejte jako argument konstruktoru jiného pojmenovaný objekt, který ji (téměř vždy unique_ptr) vlastní.

```cpp
void f() {
    unique_ptr<widget> p( new widget() );
    my_class x( new widget() );
    // ...
} // automatic destruction and deallocation for both widget objects
  // automatic exception safety, as if "finally { p->dispose(); x.w.dispose(); }"
```

Nový prostředek bezprostředně předejte jiným objektem, který ho vlastní.

```cpp
void g() {
    other_class y( OpenFile() );
    // ...
} // automatic closing and release for file resource
  // automatic exception safety, as if "finally { y.file.dispose(); }"
```

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)