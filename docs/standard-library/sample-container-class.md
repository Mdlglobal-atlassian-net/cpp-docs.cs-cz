---
title: Ukázkový kontejner – třída
ms.date: 11/04/2016
helpviewer_keywords:
- container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
ms.openlocfilehash: dbfa076756b9e4829898d38e0277ad90106ba579
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410990"
---
# <a name="sample-container-class"></a>Ukázkový kontejner – třída

> [!NOTE]
> Toto téma je v dokumentaci k Visual C++ jako funkční příklad kontejnery používané ve standardní knihovně jazyka C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Popisuje objekt, který řídí různé délky sekvence elementů typu obvykle `Ty`. Sekvence je uložen různými způsoby v závislosti na skutečné kontejneru.

Kontejner konstruktor nebo členským funkcím zjistit příležitosti k volání konstruktoru **Ty**(**const Ty &**) nebo funkci **Ty::operator =**(**const Ty &**). Pokud takové volání vyvolá výjimku, objekt kontejneru musí zachovat svou integritu a znovu vyvolat jakoukoli výjimku, který zachycuje. Můžete bezpečně odkládacího souboru, můžete přiřadit k vymazání nebo zničit objekt kontejneru po vyvolá jednu z těchto výjimek. Obecně platí ale nemůžete jinak předpovědět, stav sekvence řízenou parametrem objektu kontejneru.

Několik dalších upozornění:

- Pokud výraz `~Ty` vyvolá výjimku, výsledný stav objektu kontejneru není definován.

- Pokud kontejner ukládají objekt alokátoru *al*, a *al* vyvolá výjimku jako výsledek volání do jiných než `al.allocate`, výsledný stav objektu kontejneru není definován.

- Pokud kontejner ukládá objekt funkce *kompozice*určete způsob řazení řízené sekvence a *comp* vyvolává výjimky jakéhokoli druhu, výsledný stav objektu kontejneru není definován.

Třídy kontejnerů, které jsou definované ve standardní knihovně C++ splnit několik dalších požadavků, jak je popsáno v následujících odstavcích.

Kontejner šablony třídy [seznamu](../standard-library/list-class.md) poskytuje chování deterministické a užitečné i v případě výskytu výjimky je popsáno výše. Pokud dojde k výjimce při vložení jedné nebo víc elementů kontejneru je beze změny doleva a je znovu vyvolána výjimka.

Pro *všechny* třídy kontejnerů definované standardní knihovny C++, pokud dojde k výjimce během volání následující členské funkce `insert`, `push_back`, nebo `push_front`, kontejner zůstane beze změny a znovu se vyvolá výjimka.

Pro *všechny* tříd kontejnerů definovaných výčtem standardní knihovny C++, není vyvolána žádná výjimka při volání na tyto členské funkce: `pop_back`, `pop_front`.

Členská funkce [vymazat](../standard-library/container-class-erase.md) vyvolá výjimku, pouze v případě, že operace kopírování (přiřazení nebo kopírování konstrukce) dojde k výjimce.

Kromě toho není vyvolána žádná výjimka při kopírování iterátor vrácený členskou funkci.

Členská funkce [prohození](../standard-library/container-class-swap.md) učiní další příslibů *všechny* kontejneru tříd definovaných výčtem standardní knihovny jazyka C++:

- Členská funkce vyvolá výjimku, pouze v případě, že kontejner ukládá objekt přidělování al a `al` vyvolá výjimku při kopírování.

- Odkazy, ukazatele a iterátory, které určují prvky řízené sekvencí prohazují zůstávají platné.

Objekt třídy kontejneru standardní knihovny C++ definované přiděluje a uvolňuje úložiště pro sekvenci řídí, prostřednictvím uloženého objektu typu `Alloc`, což je obvykle parametru šablony. Takový objekt alokátoru musí mít stejné externí rozhraní jako objekt třídy `allocator<Ty>`. Zejména `Alloc` musí být stejného typu jako `Alloc::rebind<value_type>::other`

Pro *všechny* definované standardní knihovny C++, členské funkce třídy kontejnerů `Alloc get_allocator const;` vrátí kopii objektu uložený objekt alokátoru. Všimněte si, že je uložený objekt alokátoru *není* zkopírován při přiřazení objektu kontejneru. Všechny konstruktory inicializují hodnotu uloženou v `allocator`do `Alloc` Pokud konstruktor obsahuje parametr allocator.

Podle standardu jazyka C++ kontejneru třídy definované ve standardní knihovně C++ můžete předpokládat, že:

- Všechny objekty třídy `Alloc` porovnání rovnosti.

- Typ `Alloc::const_pointer` je stejný jako `const Ty *`.

- Typ `Alloc::const_reference` je stejný jako `const Ty&`.

- Typ `Alloc::pointer` je stejný jako `Ty *`.

- Typ `Alloc::reference` je stejný jako `Ty&`.

V této implementaci ale kontejnerů Nedovolte, aby byly tyto předpoklady. To znamená fungují správně s přidělování objektů, které jsou náročnějších:

- Všechny objekty třídy `Alloc` nemusí porovnávání stejné. (Můžete spravovat více fondů úložiště.)

- Typ `Alloc::const_pointer` nemusí být stejné jako `const Ty *`. (Ukazatel const musí být třída)

- Typ `Alloc::pointer` nemusí být stejné jako `Ty *`. (Ukazatel může být třída).

## <a name="requirements"></a>Požadavky

**Hlavička**: \<ukázkový kontejner >

## <a name="see-also"></a>Viz také:

[\<Ukázkový kontejner >](../standard-library/sample-container.md)<br/>
