---
title: Vlastnosti (C++/CX)
ms.date: 01/22/2017
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
ms.openlocfilehash: fdff2bf5abd3177eda962b7cc55ace1078522f32
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741098"
---
# <a name="properties-ccx"></a>Vlastnosti (C++/CX)

Typy prostředí Windows Runtime zveřejňují veřejná data jako vlastnosti. Kód klienta přistupuje k vlastnosti, jako je například veřejný DataMember. Interně je vlastnost implementována jako blok, který obsahuje přístupovou metodu GET, metodu set přistupující objekt nebo obojí. Pomocí metod přístupového objektu můžete provést další akce před nebo po načtení hodnoty, například můžete vyvolat událost nebo provádět kontroly ověřování.

### <a name="remarks"></a>Poznámky

Hodnota vlastnosti je obsažena v soukromé proměnné, označované jako *záložní úložiště*, což je stejný typ jako vlastnost. Vlastnost může obsahovat přístupový objekt set, který přiřadí hodnotu záložnímu úložišti a přístupový objekt get, který načte hodnotu záložního úložiště. Vlastnost je jen pro čtení, pokud poskytuje pouze přistupující objekt get pouze pro zápis, pokud poskytuje pouze přístupový objekt set a čtení/zápis (může být upravitelný), pokud poskytuje oba přistupující objekty.

*Triviální* vlastnost je vlastnost pro čtení a zápis, pro kterou kompilátor automaticky implementuje přistupující objekty a záložní úložiště. Nemáte přístup k implementaci kompilátoru. Můžete ale deklarovat vlastní vlastnost a explicitně deklarovat její přistupující objekty a záložní úložiště. V rámci přístupového objektu můžete provést libovolnou logiku, kterou požadujete, například ověření vstupu do přístupového objektu set, výpočet hodnoty z hodnoty vlastnosti, přístup k databázi nebo vyvolávání události při změně vlastnosti.

Je- C++li vytvořena instance referenční třídy/CX, je před voláním konstruktoru inicializována jeho paměť. všechny vlastnosti jsou proto přiřazeny výchozí hodnotě nula nebo nullptr v bodě deklarace.

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje, jak deklarovat a přistupovat k vlastnosti. První vlastnost, `Name`, je známá jako vlastnost *triviální* , protože `set` kompilátor automaticky `get` generuje přistupující objekt, přistupující objekt a záložní úložiště.

Druhá vlastnost, `Doctor`, je vlastnost jen pro čtení, protože určuje *blok vlastnosti* , který explicitně `get` deklaruje pouze přistupující objekt. Vzhledem k tomu, že je deklarován blok vlastnosti, je nutné explicitně deklarovat záložní úložiště; To znamená, že proměnná privátního řetězce ^ `doctor_`,. Vlastnost jen pro čtení obvykle vrací pouze hodnotu záložního úložiště. Pouze samotná třída může nastavit hodnotu záložního úložiště, obvykle v konstruktoru.

Třetí vlastnost, `Quantity`je vlastnost pro čtení i zápis, protože deklaruje blok vlastnosti, který deklaruje `set` přistupující objekt i `get` přistupující objekt.

`set` Přistupující objekt provádí uživatelsky definovaný test platnosti na přiřazené hodnotě. A na rozdíl C#od, *hodnota* název je pouze identifikátor `set` parametru v přistupující objekt; není to klíčové slovo. Pokud *hodnota* není větší než nula, je vyvolána platforma:: InvalidArgumentException. V opačném případě se záložní `quantity_`úložiště aktualizuje s přiřazenou hodnotou.

Všimněte si, že vlastnost nemůže být inicializována v seznamu členů. Můžete samozřejmě inicializovat proměnné záložního úložiště v seznamu členů.

[!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
