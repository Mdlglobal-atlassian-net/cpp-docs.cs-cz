---
title: Ukazatel na implementaci pro zapouzdření za kompilace (moderní verze jazyka C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: f1eb06ad3a52be486f085babf699677951b1ee71
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245180"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Ukazatel na implementaci pro zapouzdření za kompilace (moderní verze jazyka C++)

*Ukazatel na implementaci idiom* je moderní C++ technika pro skrytí implementace, k minimalizaci spojení a k oddělení rozhraní. Ukazatel na implementaci je pro "ukazatel na implementaci" krátký. Můžete už být obeznámeni s konceptem, ale znáte ho jinými názvy, jako je Cheshire Cat nebo idiom firewall kompilátoru.

## <a name="why-use-pimpl"></a>Proč používat ukazatel na implementaci?

Tady je postup, jak může ukazatel na implementaci idiom zlepšit životní cyklus vývoje softwaru:

- Minimalizace závislostí kompilace.

- Oddělení rozhraní a implementace.

- Přenosn.

## <a name="pimpl-header"></a>Ukazatel na implementaci hlavičku

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

Ukazatel na implementaci idiom zabraňuje opětovnému sestavení kaskádových a poměrně křehkých objektů. Je vhodný pro (projíždějící) oblíbené typy.

## <a name="pimpl-implementation"></a>Implementace ukazatel na implementaci

V souboru. cpp Definujte třídu `impl`.

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

Zvažte, zda přidat podporu pro specializaci neaktivačního swapu.

## <a name="see-also"></a>Viz také:

[Vítejte zpět naC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
