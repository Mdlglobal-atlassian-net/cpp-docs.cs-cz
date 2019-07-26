---
title: Iterátory
ms.date: 11/04/2016
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
ms.openlocfilehash: ec23cbea63bc6884a361600362fcf0061e927ca6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449965"
---
# <a name="iterators"></a>Iterátory

Iterátor je objekt, který může iterovat prvky ve C++ standardním kontejneru knihovny a poskytnout přístup k jednotlivým prvkům. C++ Standardní kontejnery knihovny poskytují iterátory, aby algoritmy mohly přistupovat ke svým prvkům standardním způsobem, aniž by museli mít obavy z typu kontejneru, v němž jsou uloženy prvky.

Můžete použít `begin()` iterátory explicitně pomocí členů a globálních funkcí, jako jsou a `end()` a **--** a **++** přesunout dopředu nebo zpět. Můžete také použít iterátory implicitně s rozsahem smyčky for nebo (u některých typů iterátorů) operátoru  **\[** dolního indexu].

Ve C++ standardní knihovně je začátek sekvence nebo rozsahu prvním prvkem. Konec sekvence nebo rozsahu je vždy definován jako první prvek za posledním prvkem. Globální funkce `begin` a `end` vracejí iterátory do určeného kontejneru. Typický explicitní cyklus iterátoru u všech prvků v kontejneru vypadá takto:

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec); it != end(vec); it++)
{
    // Access element using dereference operator
    cout << *it << " ";
}
```

Stejnou věc lze dosáhnout více jednoduše pomocí cyklu Range-for:

```cpp
for (auto num : vec)
{
    // no deference operator
    cout << num << " ";
}
```

Existuje pět kategorií iterátorů. V rámci zvýšení výkonu jsou tyto kategorie:

- **Výstup**. *Výstupní iterátor* `X` může iterovat přes **++** sekvenci pomocí operátoru a může napsat __\*__ element pouze jednou pomocí operátoru.

- **Vstup**. *Vstupní iterátor* `X` může iterovat přes sekvenci pomocí operátoru + + a může číst prvek libovolným počtem **&ast;** pokusů pomocí operátoru. Vstupní iterátory můžete porovnat pomocí **++** operátorů a **! =** . Po zvýšení jakékoli kopie vstupního iterátoru není možné žádná z ostatních kopií bezpečně porovnat, odkázat nebo zvýšit.

- **Předá**. Dopředný *iterátor* `X` může iterovat přes sekvenci pomocí operátoru + + a může číst libovolný element nebo zapisovat nekonstantní prvky libovolným počtem **&ast;** pokusů pomocí operátoru. Ke členům elementu můžete přistupovat pomocí **->** operátoru a porovnat dopředné iterátory **==** pomocí operátorů a **! =** . Můžete vytvořit několik kopií dopředných iterátorů, z nichž každý může být přesměrován a zvýšen nezávisle. Dopředný iterátor, který je inicializován bez odkazu na libovolný kontejner, se nazývá *iterátor s hodnotou null*. Nevydávané iterátory s hodnotou null vždy porovnají.

- **Obousměrný**. *Obousměrný iterátor* `X` může místo dopředný iterátor uskutečnit. Můžete ale také snížit obousměrný iterátor, jako v `--X`, `X--`nebo `(V = *X--)`. Můžete přistupovat ke členům prvků a porovnat obousměrné iterátory stejným způsobem jako dopředné iterátory.

- **Náhodný přístup**. Iterátor`X` náhodného přístupu může vzít místo obousměrného iterátoru. Pomocí iterátoru náhodného přístupu můžete k prvkům přistupovat pomocí  **\[** operátoru dolního indexu]. Operátory **+** **,-** **a-=můžete** použít k přesunutí dopředu nebo dozadu určeného počtu prvků a k výpočtu vzdálenosti mezi iterátory. **+=** Obousměrné iterátory můžete **==** porovnat pomocí, **! =** , **\<** , **>** , **\< =** a. **>=**

Všechny iterátory je možné přiřadit nebo zkopírovat. Předpokládá se, že jsou prosté objekty a jsou často předávány a vraceny hodnotou, nikoli odkazem. Všimněte si také, že žádná z dříve popsaných operací nemůže vyvolat výjimku, pokud je provedena na platné iterátory.

Hierarchii kategorií iterátoru lze shrnout zobrazením tří sekvencí. Pro přístup k sekvenci pouze pro zápis můžete použít některý z těchto možností:

> výstupní iterátor \
> -> dopředný iterátor \
> -> obousměrný iterátor \
> -> iterátor s náhodným přístupem

Šipka doprava znamená, že může být nahrazena. Jakýkoli algoritmus, který volá pro výstupní iterátor, by měl pracovat s dopředný iterátorem, například  jiným způsobem.

Pro přístup ke sekvenci jen pro čtení můžete použít libovolný z těchto:

> vstupní iterátor \
> -> dopředný iterátor \
> -> obousměrný iterátor \
> -> iterátor s náhodným přístupem

Vstupní iterátor je nejslabší ze všech kategorií, v tomto případě.

Nakonec můžete pro přístup pro čtení a zápis do sekvence použít některý z těchto možností:

> dopředný iterátor \
> -> obousměrný iterátor \
> -> iterátor s náhodným přístupem

Ukazatel objektu může vždy sloužit jako iterátor náhodného přístupu, takže může sloužit jako libovolná kategorie iterátoru, pokud podporuje správný přístup pro čtení a zápis do sekvence, kterou určuje.

Iterátor `Iterator` jiný než ukazatel na objekt musí také definovat typy členů vyžadované specializací `iterator_traits<Iterator>`. Všimněte si, že tyto požadavky lze splnit odvozením `Iterator` z veřejného iterátoru základní [](../standard-library/iterator-struct.md)třídy.

Je důležité pochopit příslibů a omezení každé kategorie iterátoru a zjistit, jak jsou iterátory používány kontejnery a algoritmy ve C++ standardní knihovně.

> [!NOTE]
> Můžete se vyhnout používání iterátorů explicitně pomocí cyklu Range-for. Další informace naleznete v tématu [Range-based for Statement](../cpp/range-based-for-statement-cpp.md).

Microsoft C++ teď nabízí kontrolované iterátory a ladicí iterátory, aby se zajistilo, že nepřepisujete hranice vašeho kontejneru. Další informace najdete v tématech [kontrolované iterátory](../standard-library/checked-iterators.md) a [Podpora pro ladění iterátorů](../standard-library/debug-iterator-support.md).

## <a name="see-also"></a>Viz také:

[C++Odkaz na standardní knihovnu](../standard-library/cpp-standard-library-reference.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
