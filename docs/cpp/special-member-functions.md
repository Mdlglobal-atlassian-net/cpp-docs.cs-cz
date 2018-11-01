---
title: Speciální členské funkce
ms.date: 12/06/2016
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
ms.openlocfilehash: 3b26628fd18749bd19819fe787888fd3264a79d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535757"
---
# <a name="special-member-functions"></a>Speciální členské funkce

*Speciálních členských funkcí* se, že v některých případech kompilátor automaticky generuje můžete členské funkce třídy (nebo struct). Tyto funkce jsou [výchozí konstruktor](constructors-cpp.md#default_constructors), [destruktor](destructors-cpp.md), [konstruktor kopie a operátor přiřazení kopie](copy-constructors-and-copy-assignment-operators-cpp.md)a [konstruktor přesunu a operátor Move assignment](move-constructors-and-move-assignment-operators-cpp.md). Pokud vaše třída nedefinuje jeden nebo více zvláštních členských funkcí, pak kompilátor může implicitně deklarace a definice funkce, které se používají. Implementace vygenerovaný kompilátorem jsou volány *výchozí* speciálních členských funkcí. Kompilátor negeneruje funkce, pokud nejsou potřeba.

Výchozí zvláštní členské funkce lze explicitně deklarovat s použitím **= default** – klíčové slovo. To způsobí, že kompilátor definovat funkci pouze v případě potřeby stejným způsobem, jako kdyby byly funkce nebyla vůbec deklarovány.

V některých případech může kompilátor generovat *odstranit* speciálních členských funkcí, které nejsou definované a proto nelze volat. K tomu může dojít v případech, kdy volání konkrétní zvláštní členské funkce třídy nedává smysl, uvedeny další vlastnosti třídy. Explicitně zabránit automatické generování speciálních členských funkcí, je možné deklarovat ho jako odstraněný pomocí **= delete** – klíčové slovo.

Kompilátor generuje *výchozí konstruktor*, konstruktor, který nepřijímá žádné argumenty, pouze v případě, že nebyly deklarovány jiných konstruktoru. Pokud je deklarován pouze konstruktor, který používá parametry, kód, který se pokusí o volání výchozího konstruktoru způsobí, že kompilátor vytvoří chybová zpráva. Vygenerovaný kompilátorem výchozí konstruktor provádí jednoduché member-wise [výchozí inicializace](initializers.md#default_initialization) objektu. Výchozí inicializace zůstanou všechny proměnné členů v neurčitém stavu.

Výchozí destruktor provádí požadování zničení objektu. Je virtuální pouze v případě, že je virtuální destruktor základní třídy.

Výchozí kopírování a přesun konstrukce a operací přiřazení provádět požadování bitový vzor kopíruje nebo přesouvá nestatických datových členů. Přesun operace jsou generovány pouze, pokud žádný destruktor nebo operací přesunutí nebo kopírování jsou deklarovány. Výchozí konstruktor kopie se vygeneruje pouze tehdy, když je deklarován žádný kopírovací konstruktor. Se implicitně odstranila, pokud je deklarována operace přesunu. Výchozí operátor přiřazení kopie se vygeneruje pouze v případě, že je explicitně deklarován žádný operátor přiřazení kopie. Se implicitně odstranila, pokud je deklarována operace přesunu.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](cpp-language-reference.md)