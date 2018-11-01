---
title: Přetypování
ms.date: 11/04/2016
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
ms.openlocfilehash: eb309319a4af6d604d8558552ce313ba1d0fb629
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560794"
---
# <a name="casting"></a>Přetypování

Jazyk C++ udává, že je-li třída odvozena ze základní třídy obsahující virtuální funkce, lze ukazatel na typ této základní třídy použít k volání implementací virtuálních funkcí umístěných v objektu odvozené třídy. Třída obsahující virtuální funkce je někdy označována jako „polymorfní třída“.

Jelikož odvozená třída obsahuje všechny definice všech základních tříd, z nichž byla odvozena, lze ukazatel přetypovat na libovolnou z těchto tříd vyskytujících se výše v jejich hierarchii. Je-li dán ukazatel na základní třídu, může být bezpečné přetypovat ukazatel na třídu umístěnou v hierarchii níže. Přetypování je bezpečné, pokud objekt, na který ukazatel ukazuje, je ve skutečnosti typem odvozeným ze základní třídy. V takovém případě se skutečný objekt nazývá „kompletním objektem“. O ukazateli na základní třídu se říká, že ukazuje na „podobjekt“ kompletního objektu. Vezměte v úvahu například hierarchii tříd znázorněnou na následujícím obrázku.

![Hierarchie třídy](../cpp/media/vc38zz1.gif "vc38ZZ1") hierarchie tříd

Objekt typu `C` lze vizualizovat tak, jak ukazuje následující obrázek.

![Třída C s sub&#45;objekty B a A](../cpp/media/vc38zz2.gif "vc38ZZ2") třídy C s Podobjekty B a A podobjekt

Je-li dána instance třídy `C`, existuje podobjekt `B` a podobjekt `A`. Instance třídy `C`, včetně podobjektů `A` a `B`, je „kompletním objektem“.

Pomocí informací o typu modulu runtime lze zkontrolovat, zda ukazatel skutečně ukazuje na kompletní objekt a lze jej bezpečně přetypovat tak, aby ukazoval na jiný objekt ve své hierarchii. [Dynamic_cast](../cpp/dynamic-cast-operator.md) operátor je možné provádět tyto druhy přetypování. Operátor provádí za běhu také kontroly potřebné k zajištění bezpečnosti operace.

Pro převod nepolymorfních typů lze použít [static_cast](../cpp/static-cast-operator.md) – operátor (Toto téma vysvětluje rozdíl mezi statickými a dynamickými převody a kdy je vhodné je použít).

Tato část obsahuje následující témata:

- [Operátory přetypování](../cpp/casting-operators.md)

- [Informace běhového typu](../cpp/run-time-type-information.md)

## <a name="see-also"></a>Viz také:

[Výrazy](../cpp/expressions-cpp.md)