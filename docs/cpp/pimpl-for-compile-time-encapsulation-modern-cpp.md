---
title: Ukazatel na implementaci pro zapouzdření za kompilace (moderní verze jazyka C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: 6e114e2802dd4b2e5d1497867e2224be90c4752d
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220683"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Ukazatel na implementaci pro zapouzdření za kompilace (moderní verze jazyka C++)

*Ukazatel na implementaci idiom* je moderní C++ techniku ke skrytí implementace, chcete-li minimalizovat párování a k oddělení rozhraní. Ukazatel na implementaci je zkratka pro "ukazatel na implementaci." Může již být seznámení s konceptem, ale znáte jiné názvy jako idiom Cheshiru Cat nebo brány Firewall kompilátoru.

## <a name="why-use-pimpl"></a>Proč používat ukazatel na implementaci?

Zde je, jak vylepšit idiom ukazatel na implementaci životního cyklu vývoje softwaru:

- Minimalizace závislostí kompilace.

- Oddělení rozhraní a implementaci.

- Přenositelnost.

## <a name="pimpl-header"></a>Ukazatel na implementaci záhlaví

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

Idiom ukazatel na implementaci vyhýbá cascades opětovné sestavení a křehký objekt rozložení. Je vhodná pro (přechodně) oblíbených typů.

## <a name="pimpl-implementation"></a>Ukazatel na implementaci implementace

Definovat `impl` třída v souboru .cpp.

```cpp
// my_class.cpp
class my_class::impl {  // defined privately here
  // ... all private data and functions: all of these
  //     can now change without recompiling callers ...
};
my_class::my_class(): pimpl( new impl )
{
  // ... set impl values ...
}
```

## <a name="best-practices"></a>Osvědčené postupy

Zvažte, jestli se má přidat podporu pro specializaci non-throwing. prohození.

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět (moderní verze jazyka C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
