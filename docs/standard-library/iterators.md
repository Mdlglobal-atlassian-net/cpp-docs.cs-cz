---
title: Iterátory
ms.date: 11/04/2016
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
ms.openlocfilehash: cf1f519521d86f2b7782fb93ed3b4aca4ecd5b24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643440"
---
# <a name="iterators"></a>Iterátory

Iterátor je objekt, který může iterovat prvky v kontejneru standardní knihovny C++ a poskytují přístup k jednotlivým prvkům. Kontejnery standardní knihovny C++, všechny poskytnuté iterátory tak, aby algoritmů můžete ke jejich prvky standardním způsobem, aniž byste museli být obeznámeni s typu kontejneru elementů jsou uloženy v.

Můžete použít iterátory explicitně pomocí členské a globální funkce, jako `begin()` a `end()` a operátory, jako například **++** a **--** přesunout vpřed nebo zpětně. Můžete také použít iterátory implicitně s rozsahem-smyčky for nebo (pro některé typy iterátoru) operátor dolního indexu  **\[]**.

Na začátek pořadí nebo rozsahu ve standardní knihovně jazyka C++ je první prvek. Konec pořadí nebo rozsah je vždy definována jako jedno místo za posledním prvkem. Globální funkce `begin` a `end` vrátí iterátory do zadaného kontejneru. Typické explicitní iterace smyčky přes všechny prvky v kontejneru vypadá takto:

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec); it != end(vec); it++)
{
    // Access element using dereference operator
    cout << *it << " ";
}
```

Totéž lze provést jednoduše pomocí rozsah-smyčka for:

```cpp
for (auto num : vec)
{
    // no deference operator
    cout << num << " ";
}
```

Existuje pět kategorií iterátorů. V pořadí podle zvýšení výkonu kategorie jsou:

- **Výstup**. *Výstupního iterátoru* `X` můžete Iterujte vpřed přes posloupnosti pomocí **++** operátorů a můžete napsat jenom jednou, elementu s použitím **&ast;** operátor.

- **Vstup**. *Vstupní iterátor* `X` můžete Iterujte vpřed přes posloupnosti pomocí ++ operátor a může číst prvek libovolný počet pokusů s použitím **&ast;** operátor. Můžete porovnat vstupní iterátory s použitím **++** a **! =** operátory. Po zvýšit libovolné kopii vstupní iterátor žádné další kopie lze bezpečně porovnat, přes ukazatel nebo zvýšena po tomto datu.

- **Vpřed**. A *dopředný iterátor, který* `X` můžete Iterujte vpřed přes posloupnosti pomocí ++ – operátor a může číst libovolný prvek nebo zapisovat elementy nekonstantní libovolný počet pokusů s použitím **&ast;** operátor. Získáte přístup k členům elementu s použitím **->** operátor a porovnejte dál iterátory s použitím **==** a **! =** operátory. Může vytvářet více kopií dopředný iterátor, z nichž každý lze přistoupit přes ukazatel a zvýší, nezávisle na sobě. Dopředný iterátor, který je inicializován bez odkazu na kterýkoli kontejner se volá *null dopředný iterátor, který*. Null dopředných iterátorů vždy porovnávají se stejně.

- **Obousměrné**. A *obousměrný iterátor, který* `X` může proběhnout iterátor předání. Vám může, ale také snížení obousměrný iterátor, stejně jako v `--X`, `X--`, nebo `(V = *X--)`. Je možné přistupovat k členům elementu a porovnat obousměrných iterátorů stejným způsobem jako dopředných iterátorů.

- **Náhodný přístup**. A *iterátor s náhodným přístupem* `X` může proběhnout obousměrný iterátor. S iterátor náhodného přístupu můžete použít operátor dolního indexu  **\[]** k přístupu k prvkům. Můžete použít **+**, **-**, **+=** a **-=** operátory přesunutí dopředu nebo dozadu zadaný počet prvků a vzdálenosti mezi vzájemně iterátory. Můžete porovnat s použitím obousměrných iterátorů **==**, **! =**, **\<**, **>**, **\< =**, a **>=**.

Všechny iterátory můžete přiřadit nebo zkopírován. Jsou považovány za jednoduché objekty a jsou často předané a vrácené hodnoty není odkazem. Všimněte si také, že žádná z operací výše popsaný může vyvolat výjimku při provádění na iterátor platný.

Hierarchie kategorií iterátoru můžeme shrnout tím, že zobrazuje tři pořadí. Pro přístup pouze pro zápis do sekvence můžete použít některý z:

> výstupní iterátor<br/>
> Dopředný iterátor, který -><br/>
> obousměrný iterátor, který -><br/>
> -> iterátor s náhodným přístupem<br/>

Na šipku vpravo znamená "může být nahrazen." Libovolný algoritmus, který volá pro výstupní iterátor by měl fungovat například krásně pro dopředný iterátor, ale *není* naopak.

Pro přístup jen pro čtení do sekvence můžete použít některý z:

> vstupní iterátor<br/>
> Dopředný iterátor, který -><br/>
> obousměrný iterátor, který -><br/>
> -> iterátor s náhodným přístupem<br/>

Vstupní iterátor v tomto případě je nejnižší prioritu všech kategorií.

Nakonec pro přístup pro čtení a zápis do pořadí, můžete použít některý z:

> Dopředný iterátor, který<br/>
> obousměrný iterátor, který -><br/>
> -> iterátor s náhodným přístupem<br/>

Ukazatelem na objekt může vždycky sloužit jako iterátor náhodného přístupu, aby mohl sloužit jako libovolnou kategorii iterátoru, pokud podporuje přístup správné čtení a zápis do sekvence, které určí.

Iterátor `Iterator` jiného než objekt musí ukazatel také definovat typy členů vyžadované specializace `iterator_traits<Iterator>`. Všimněte si, že tyto požadavky můžete splnit odvozením `Iterator` ze základní třídy veřejné [iterátoru](../standard-library/iterator-struct.md).

Je důležité pochopit, co a omezení jednotlivých kategorií iterátoru zobrazíte používání iterátorů tak, že kontejnery a algoritmy ve standardní knihovně jazyka C++.

> [!NOTE]
> Používání iterátorů explicitně pomocí rozsahu můžete vyhnout-smyčky for. Další informace najdete v tématu [Range-based pro příkaz](../cpp/range-based-for-statement-cpp.md).

Visual C++ teď nabízí kontrolované iterátory a iterátory ladění Ujistěte se, že nedojde k přepsání hranice vašeho kontejneru. Další informace najdete v tématu [Checked Iterators](../standard-library/checked-iterators.md) a [Debug Iterator Support](../standard-library/debug-iterator-support.md).

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
