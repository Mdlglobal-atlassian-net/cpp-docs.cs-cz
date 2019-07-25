---
title: Ukázkový kontejner – třída
ms.date: 11/04/2016
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
ms.openlocfilehash: 2024574633069cc70f0885fdce63f3afc09227c0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451110"
---
# <a name="sample-container-class"></a>Ukázkový kontejner – třída

> [!NOTE]
> Toto téma se nachází v dokumentaci C++ společnosti Microsoft jako nefunkční příklad kontejnerů použitých ve C++ standardní knihovně. Další informace najdete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

Popisuje objekt, který ovládá proměnlivou délku sekvence prvků, obvykle typu `Ty`. Sekvence je ukládána různými způsoby v závislosti na skutečném kontejneru.

Konstruktor kontejneru nebo členská funkce se mohou setkat s voláním konstruktoru **daného (** const ta **&** ) nebo funkcí **:: operator =** (**const Ty &** ). Pokud takové volání vyvolá výjimku, objekt kontejneru je povinen zachovat jeho integritu a znovu vyvolat všechny výjimky, které zachytí. Můžete bezpečně prohodit, přiřadit, smazat nebo zničit objekt kontejneru poté, co vyvolá jednu z těchto výjimek. Obecně však nemůžete odhadnout stav sekvence řízené objektem kontejneru.

Několik dalších aspektů:

- Pokud výraz `~Ty` vyvolá výjimku, výsledný stav objektu kontejneru není definován.

- Pokud kontejner ukládá objekt přidělování *Al*a *Al* vyvolá výjimku jinou než v důsledku volání `al.allocate`, výsledný stav objektu kontejneru není definován.

- Pokud kontejner ukládá kompozici objektů funkcí , aby bylo možné určit, jak sestavovat řízený sekvenci, a *comp* vyvolá výjimku jakéhokoli druhu, výsledný stav objektu kontejneru není definován.

Třídy kontejneru definované C++ standardní knihovnou splňují několik dalších požadavků, jak je popsáno v následujících odstavcích.

[Seznam](../standard-library/list-class.md) tříd šablony kontejneru poskytuje deterministické a užitečné chování i v přítomnosti výše popsaných výjimek. Například pokud je vyvolána výjimka během vložení jednoho nebo více prvků, kontejner zůstane nezměněn a výjimka je znovu vyvolána.

Pro *všechny* třídy kontejneru C++ definované standardní knihovnou, pokud je vyvolána výjimka během volání následujících členských funkcí `insert`,, `push_back`nebo `push_front`, kontejner zůstane nezměněn a výjimka je znovu vyvolána.

Pro *všechny* třídy kontejneru definované C++ standardní knihovnou není během volání následujících členských funkcí vyvolána žádná výjimka: `pop_back`,. `pop_front`

[Vymazání](../standard-library/container-class-erase.md) členské funkce vyvolá výjimku pouze v případě, že operace kopírování (přiřazení nebo konstrukce kopírování) vyvolá výjimku.

Kromě toho není vyvolána žádná výjimka při kopírování iterátoru vráceného členskou funkcí.

[Swap](../standard-library/container-class-swap.md) členské funkce poskytuje další příslibů pro *všechny* třídy kontejneru definované C++ standardní knihovnou:

- Členská funkce vyvolá výjimku pouze v případě, že kontejner ukládá objekt přidělování Al a `al` vyvolá výjimku při zkopírování.

- Odkazy, ukazatele a iterátory, které označují prvky kontrolovaných kontrolovaných sekvencí, zůstávají platné.

Objekt třídy kontejneru definované C++ standardní knihovnou přiděluje a uvolňuje úložiště pro sekvenci, kterou ovládá, prostřednictvím uloženého objektu typu `Alloc`, což je obvykle parametr šablony. Takový objekt přidělování musí mít stejné externí rozhraní jako objekt třídy `allocator<Ty>`. Konkrétně `Alloc` musí být stejný typ jako`Alloc::rebind<value_type>::other`

Pro *všechny* třídy kontejneru definované C++ standardní knihovnou vrátí členská funkce `Alloc get_allocator const;` kopii uloženého objektu přidělování. Všimněte si, že uložený objekt přidělování *není zkopírován při* přiřazení objektu kontejneru. Všechny konstruktory inicializují hodnotu uloženou `allocator`v, `Alloc` na, pokud konstruktor neobsahuje parametr přidělování.

V souladu se C++ standardem může třída kontejneru definovaná C++ standardní knihovnou předpokládat, že:

- Všechny objekty třídy `Alloc` Compare EQUAL.

- Typ `Alloc::const_pointer` je stejný jako `const Ty *`.

- Typ `Alloc::const_reference` je stejný jako `const Ty&`.

- Typ `Alloc::pointer` je stejný jako `Ty *`.

- Typ `Alloc::reference` je stejný jako `Ty&`.

V této implementaci ale kontejnery nedělají takové zjednodušení předpokladů. Proto fungují správně s objekty přidělování, které jsou více výzvám souvisejícím:

- Všechny objekty třídy `Alloc` nemusejí porovnat stejné. (Můžete udržovat více fondů úložiště.)

- Typ `Alloc::const_pointer` nemusí být stejný jako `const Ty *`. (Ukazatel const může být třída.)

- Typ `Alloc::pointer` nemusí být stejný jako `Ty *`. (Ukazatel může být třída.)

## <a name="requirements"></a>Požadavky

**Záhlaví**: \<ukázkový kontejnerový >

## <a name="see-also"></a>Viz také:

[\<Ukázkový > kontejneru](../standard-library/sample-container.md)
