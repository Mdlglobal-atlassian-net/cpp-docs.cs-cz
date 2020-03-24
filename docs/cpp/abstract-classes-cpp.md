---
title: Abstraktní třídy (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
ms.openlocfilehash: 2ea9d3765f65434cb738c2b7c53f9499bba24545
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181691"
---
# <a name="abstract-classes-c"></a>Abstraktní třídy (C++)

Abstraktní třídy fungují jako výrazy obecných konceptů, ze kterých lze odvodit více specifických tříd. Nemůžete vytvořit objekt typu abstraktní třídy; Můžete však použít ukazatele a odkazy na abstraktní typy tříd.

Třída, která obsahuje alespoň jednu čistě virtuální funkci, je považována za abstraktní třídu. Třídy odvozené od abstraktní třídy musí implementovat čistě virtuální funkci, nebo jsou také abstraktní třídy.

Vezměte v úvahu příklad prezentovaný ve [funkcích Virtual Functions](../cpp/virtual-functions.md). Záměrem třídy `Account` je poskytnout obecné funkce, ale objekty typu `Account` jsou příliš obecné, aby byly užitečné. Proto `Account` je dobrým kandidátem na abstraktní třídu:

```cpp
// deriv_AbstractClasses.cpp
// compile with: /LD
class Account {
public:
   Account( double d );   // Constructor.
   virtual double GetBalance();   // Obtain balance.
   virtual void PrintBalance() = 0;   // Pure virtual function.
private:
    double _balance;
};
```

Jediným rozdílem mezi touto deklarací a předchozí je, že `PrintBalance` je deklarován s čistým specifikátorem (`= 0`).

## <a name="restrictions-on-abstract-classes"></a>Omezení pro abstraktní třídy

Abstraktní třídy nelze použít pro:

- Proměnné nebo členská data

- Typy argumentů

- Návratové typy funkcí

- Typy explicitních převodů

Dalším omezením je skutečnost, že pokud konstruktor abstraktní třídy zavolá čistě virtuální funkci, ať už přímo či nepřímo, není výsledek definován. Konstruktory a destruktory abstraktních tříd však mohou volat ostatní členské funkce.

Čistě virtuální funkce mohou být definovány pro abstraktní třídy, ale mohou být volány pouze pomocí této syntaxe:

*název abstraktní třídy*::*Function-Name*()

Tato vlastnost je výhodná při návrhu hierarchií tříd, jejichž základní třídy zahrnují čistě virtuální destruktory, protože destruktory základních tříd jsou vždy volány během procesu ničení objektu. Vezměte v úvahu v následujícím příkladu:

```cpp
// Declare an abstract base class with a pure virtual destructor.
// deriv_RestrictionsonUsingAbstractClasses.cpp
class base {
public:
    base() {}
    virtual ~base()=0;
};

// Provide a definition for destructor.
base::~base() {}

class derived:public base {
public:
    derived() {}
    ~derived(){}
};

int main() {
    derived *pDerived = new derived;
    delete pDerived;
}
```

Je-li objekt, na nějž ukazuje ukazatel `pDerived`, odstraněn, je zavolán destruktor třídy `derived` a poté destruktor třídy `base`. Prázdná implementace čistě virtuální funkce zajišťuje existenci alespoň jedné její implementace.

> [!NOTE]
> V předchozím příkladu je čistě virtuální funkce `base::~base` zavolána implicitně z funkce `derived::~derived`. Čistě virtuální funkce lze zavolat i explicitně pomocí plně kvalifikovaného názvu členské funkce.

## <a name="see-also"></a>Viz také

[Dědičnost](../cpp/inheritance-cpp.md)
