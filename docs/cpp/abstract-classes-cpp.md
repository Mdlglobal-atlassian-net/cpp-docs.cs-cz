---
title: Abstraktní třídy (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
ms.openlocfilehash: a7b41a2cabc2cff2eca24cf50c6c30d5190d39a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461305"
---
# <a name="abstract-classes-c"></a>Abstraktní třídy (C++)

Abstraktní třídy působí jako výrazy obecných konceptů, ze kterých mohou být odvozeny konkrétnější třídy. Nejde vytvořit objekt typu abstraktní třídy; Můžete však použít ukazatele a odkazy na abstraktní typy tříd.

Třída, která obsahuje alespoň jednu prázdnou virtuální funkci, je považován za abstraktní třídu. Třídy odvozené od abstraktní třídy musí implementovat čistě virtuální funkce nebo, příliš, jsou abstraktní třídy.

Zvažte příklad uvedený v [virtuální funkce](../cpp/virtual-functions.md). Záměrem třídy `Account` je poskytnout obecné funkce, ale objekty typu `Account` jsou příliš obecné, aby byla užitečná. Proto `Account` , je vhodným kandidátem pro abstraktní třídu:

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

Jediný rozdíl mezi předchozí a touto deklarací je, že `PrintBalance` je deklarován s čistým specifikátorem (`= 0`).

## <a name="restrictions-on-abstract-classes"></a>Omezení pro abstraktní třídy

Abstraktní třídy nelze použít pro:

- Proměnné nebo členská data

- Typy argumentů

- Návratové typy funkcí

- Typy explicitních převodů

Dalším omezením je skutečnost, že pokud konstruktor abstraktní třídy zavolá čistě virtuální funkci, ať už přímo či nepřímo, není výsledek definován. Konstruktory a destruktory abstraktních tříd však mohou volat ostatní členské funkce.

Čistě virtuální funkce mohou být definovány pro abstraktní třídy, ale mohou být volány pouze pomocí této syntaxe:

*Název třídy abstraktní*::*název funkce*)

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

## <a name="see-also"></a>Viz také:

[Dědičnost](../cpp/inheritance-cpp.md)