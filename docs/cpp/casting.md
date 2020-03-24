---
title: Přetypování
ms.date: 11/19/2018
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
ms.openlocfilehash: bb06db3af6aee031b6cb2d69b38a9404304420fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190123"
---
# <a name="casting"></a>Přetypování

Jazyk C++ udává, že je-li třída odvozena ze základní třídy obsahující virtuální funkce, lze ukazatel na typ této základní třídy použít k volání implementací virtuálních funkcí umístěných v objektu odvozené třídy. Třída obsahující virtuální funkce je někdy označována jako „polymorfní třída“.

Jelikož odvozená třída obsahuje všechny definice všech základních tříd, z nichž byla odvozena, lze ukazatel přetypovat na libovolnou z těchto tříd vyskytujících se výše v jejich hierarchii. Je-li dán ukazatel na základní třídu, může být bezpečné přetypovat ukazatel na třídu umístěnou v hierarchii níže. Přetypování je bezpečné, pokud objekt, na který ukazatel ukazuje, je ve skutečnosti typem odvozeným ze základní třídy. V takovém případě se skutečný objekt nazývá „kompletním objektem“. O ukazateli na základní třídu se říká, že ukazuje na „podobjekt“ kompletního objektu. Vezměte v úvahu například hierarchii tříd znázorněnou na následujícím obrázku.

![Hierarchie tříd](../cpp/media/vc38zz1.gif "Hierarchie tříd") <br/>
Hierarchie tříd

Objekt typu `C` lze vizualizovat tak, jak ukazuje následující obrázek.

![Třída C s podřízenými&#45;objekty B a](../cpp/media/vc38zz2.gif "Třída C s podřízenými&#45;objekty B a") <br/>
Třída C s dílčími objekty B a a

Je-li dána instance třídy `C`, existuje podobjekt `B` a podobjekt `A`. Instance třídy `C`, včetně podobjektů `A` a `B`, je „kompletním objektem“.

Pomocí informací o typu modulu runtime lze zkontrolovat, zda ukazatel skutečně ukazuje na kompletní objekt a lze jej bezpečně přetypovat tak, aby ukazoval na jiný objekt ve své hierarchii. Operátor [dynamic_cast](../cpp/dynamic-cast-operator.md) lze použít k vytvoření těchto typů přetypování. Operátor provádí za běhu také kontroly potřebné k zajištění bezpečnosti operace.

Pro převod nepolymorfních typů lze použít operátor [static_cast](../cpp/static-cast-operator.md) (Toto téma vysvětluje rozdíl mezi statickým a dynamickým převodem přetypování a kdy je vhodné je použít).

Tato část obsahuje následující témata:

- [Operátory přetypování](../cpp/casting-operators.md)

- [Informace o typu běhového běhu](../cpp/run-time-type-information.md)

## <a name="see-also"></a>Viz také

[Výrazy](../cpp/expressions-cpp.md)
